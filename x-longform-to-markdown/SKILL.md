---
name: x-longform-to-markdown
description: Retrieve long form posts Articles and threads from X users; save as individual Markdown files with metadata. Supports scheduled daily actions, looping pagination, dynamic workflow for directory/MD population on user call or autonomous run. Use for archive export convert X longform/Articles (e.g. @InvariantX) to markdown; daily incremental population; full history loops.
---

# X Longform To Markdown (A2A Regenerated)

## Overview
Targeted + autonomous retrieval of long-form X content (extended posts, threads, X Articles) for usernames. Exports clean self-contained .md files (YAML frontmatter + formatted body) to artifacts/x-longform-archive/USERNAME/. Now regenerated via A2A standards with scheduled daily action support, looping for pagination/full-populate, dynamic workflow that branches on call context (user-interactive vs scheduled), stateful incremental updates (dedup by post ID), and mandatory maru/trace-consent/A2A JSONL/Hermes compliance. When called by user: dynamic on-demand population of directories and files. When scheduled: loops over configured users, incremental since last_run, emits evt- artifacts.

## Activation Triggers (A2A Extended)
- Original: "retrieve all articles/long form posts a user has published on X", "provide them as individual Markdown Files", "archive my X longposts/threads/Articles as markdown", "export @InvariantX long form content to md"
- New scheduled/daily/loop/dynamic: "daily scheduled x longform archive population", "run scheduled daily action for x articles to markdown", "loop populate x longform directory and markdown files", "dynamic workflow x longform archive for user", "incremental populate markdown from X Articles", a2a event x-longform-to-markdown, webhook x-longform-archive, hermes classify archive

## Mandatory A2A / Genesis Conductor Compliance (Injected)
- **maru guard**: On risk signal (R>0.4 equiv: repeated empty batches, rate-limit stalls, no progress) → unconditional nox reframe + escalation (see scripts/maru_guard.py). Baseline never cut.
- **trace-consent ledger**: Every execution appends D1-schema entry with timestamp, username/batch, details, provenance to artifacts/trace-consent-x-longform.jsonl (via emitter).
- **A2A JSONL output**: Emits evt- structured record (schema_version, record_type e.g. "x_longform_archive_run", payload with metrics, tags, connections) to artifacts/x-longform-archive/.a2a_events.jsonl and ledger. Supports bus handoff, VPD accounting, observability.
- **Hermes tier routing notes**: Default Haiku for intent classification / simple incremental runs (2-4k tokens, 30s). Sonnet for complex historical loops or multi-user dynamic (8k, 120s). Opus only for strategic arbitration or high-stakes coalition archive policy. Hard caps enforced.
- **genesis-conductor-ucp-integration**: Compatible with Diamondnode AAL, KVDF paths, thermodynamic-aware where relevant; aligns with sovereign infrastructure goals.
- All runs produce utilization metrics (items_processed, new_files, skipped_dedup, runtime) for ledger.

## Core Dynamic Workflow (Imperative — Adapts to Context)
Detect call mode from request/context/payload:
1. **User-interactive / dynamic call** (default when human mentions handle or "dynamic"/"populate directory"): 
   - Parse username(s) (default InvariantX or list), mode=incremental|full|loop, since/until, max_items or pagination flag.
   - Use state_manager to load last_run/processed_ids per user.
   - If incremental (recommended for user calls): compute effective since = max(user last_run or provided), fetch only new via x_keyword_search + x_thread_fetch, filter unprocessed post_ids.
   - Dynamic population: mkdir -p per username; for each qualifying item generate MD via template + sanitize_filename; write_file; update running index.md (append table row + summary); mark processed in state.
   - If loop/full requested: enter pagination loop (while results==limit: add max_id:LAST_ID to query, repeat, sleep 1-2s between pages to respect rates). Cap at reasonable safety (e.g. 50 items or 5 pages) or until maru risk.
   - On completion: emit A2A evt- + trace-consent; report files created, new vs skipped, state updated. Offer follow-up for more pages.

2. **Scheduled daily action / autonomous loop** (triggered by "daily scheduled", webhook payload mode=scheduled_daily, or evt- from scheduler):
   - Load configured users (hardcoded default ["InvariantX"] or from state/config; extensible for coalition).
   - For each user in loop:
     - Load user state (last_run, processed_post_ids).
     - Set since = last_run or (today - 7d for safety); fetch Latest mode, prioritize /i/article/ or long content.
     - Process only unprocessed items (state_manager.should_process_post).
     - Dynamic dir/MD population exactly as above (but non-verbose, batch-optimized).
     - Update state with new last_run=now, new_post_ids, last_post_id.
     - If maru_risk detected mid-loop (empty x3 or errors): call maru_reframe, reduce scope, continue or halt user.
   - After all users: emit consolidated A2A JSONL evt- record_type="scheduled_daily_x_longform_archive" with aggregate metrics (users_processed, total_new_files, skipped, runtime). Append to ledger.
   - Non-interactive: minimal output, full artifacts for downstream (index updates, evt- bus).

3. **Looping / full history population** (explicit "loop" or pagination flag):
   - Enter while-loop: initial query (from:USER since: or max_id), x_keyword_search, process batch, if hit limit append max_id=last_id and repeat.
   - Dynamic: after each page, update partial index + state (so resumable).
   - Maru guard on every iteration; on risk → reframe to narrower window or escalate to Sonnet tier.
   - Safety: hard cap total_items or pages; thermodynamic note — prefer incremental daily over full loops for cost.

Common sub-steps (all modes):
- Validate username(s) via x_user_search.
- Build query: `from:USERNAME -is:retweet` + dates + engagement filter if quality needed. Mode=Latest preferred.
- For each post: skip short unless thread starter or contains x.com/i/article/ link.
- **Article handling**: Prefer x_thread_fetch(post_id) on teaser — it reliably expands full body (note: browse_page disabled on x.com; thread fetch surfaces the essay content directly). Fall back to content if already expanded.
- Non-Article/thread: x_thread_fetch if conversation indicates depth; assemble body + replies.
- Generate MD: YAML frontmatter (title/author/published/x_url/article_url/type/engagement/source_query) + # Title + structured body (headings, lists, code fences, references preserved) + archival footer.
- Filename: YYYY-MM-DD_slug.md via scripts/sanitize_filename.py.
- Write via write_file; maintain/append index.md with table of items + run summary.
- Dedup: state_manager checks processed_post_ids; skip if seen (prevents re-populate on re-runs).
- Risk/edge: zero items → suggest broader/narrower; rate error → maru + backoff; privacy → only public.

## Scripts & Resources (Dynamic Workflow Enablers)
- scripts/sanitize_filename.py — safe date_slug.md names.
- scripts/state_manager.py — load/update per-user last_run + processed_post_ids JSON; incremental/dedup support for scheduled + dynamic calls.
- scripts/a2a_jsonl_emitter.py — emit_evt(record_type, payload) for A2A JSONL + trace-consent ledger append.
- scripts/maru_guard.py — check_maru_risk(recent_results) + maru_reframe() for unconditional escalation path.
- references/markdown-template.md — canonical frontmatter + body structure (expand as needed).

Use `bash scripts/STATE_OR_EMITTER.py` or import in complex flows. State persists in artifacts/ for resumability across scheduled runs or sessions.

## Edge Cases, Best Practices & Limitations (Enhanced)
- Incremental is default for efficiency and daily scheduled loops — full history only on explicit request (costly).
- X Articles: teaser in search often minimal; thread_fetch on the post_id expands the full formatted essay (tested on InvariantX June 2026 Articles).
- Scheduled runs: configure external scheduler (Genesis Conductor MCP cron, Cloudflare Worker, or hermes dispatch) to invoke with mode flag or a2a event. Skill is idempotent + stateful.
- When user calls: always dynamic — can force "full loop for @user since 2025-01-01" or just "populate latest for me".
- Maru: any stall triggers reframe (never silent fail); escalate complex loops.
- Never claim complete history in one pass; daily incremental + state builds it safely over time.
- Files persist in artifacts/; index.md always reflects current population state.
- Token/runtime: follow Hermes caps; large loops may auto-tier or partial.

## Value & Integration
Directly supports sovereign archival of longform thought (e.g. technical essays, Article series) into queryable markdown for RAG, analysis, or publishing. Integrates with Genesis Conductor (evt- bus, trace-consent, UCP), Diamondnode high-VPD orchestration, and 13 revenue streams via automated population + observability. Thermodynamic note: incremental daily loops minimize waste vs. one-shot full scans.

Test by reading produced .md with read_file or running state show. Expand users/config in future iterations via registry update. This regenerated version is fully A2A-compliant and ready for scheduled daily autonomous operation + on-demand dynamic user calls.
