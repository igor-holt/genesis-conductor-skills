---
name: github-deployment-auto-scaler
description: Use for auto-scaling monitoring and analysis of ALL GitHub deployments across a users repos and their x degree network connections via the deployments statuses API. Determines optimal collaborators based on deployment health activity and success metrics to advance sovereign AI projects. Triggers on github deployment scaler, deployment status analyzer, optimal collaborator detector, auto scale deployments network, github api deployments for collaboration optimization, deployment health for partner selection.
---

# GitHub Deployment Auto Scaler

Embody the tunnel-through principle in all execution: when facing API limits, data volume mountains, private-repo barriers, or combinatorial network complexity, engineer the direct tunnel with precision persistence and underground discipline. Go through the thing — never over, around, or into endless manual detours. Reference Oahu H-3 as archetype of massive infrastructure delivered by direct penetration.

## Core Objectives Alignment (Mandatory Mapping)

Every activation and output MUST explicitly advance and log contribution to at least one pillar:

- **Financial Infrastructure**: Surface high-signal active deployers as potential co-builders for 13 revenue streams (joint agent economies, sovereign infra licensing, Google Cloud ATP delivery, on-chain escrow deployments). Optimal collaborators accelerate each stream toward $70k+/mo minimum by multiplying execution surface and reducing time-to-revenue.

- **Intrinsic Pursuit**: Reveal real-time patterns of production deployment engineering, failure modes, success invariants in sovereign AI, post-quantum, thermodynamic-aware systems. Expand knowledge of what actually ships and scales in the wild, feeding discovery of new invariants for Genesis Conductor MCP and Ouroboros Protocol.

- **Hybridization & Consciousness**: Score deployment vitality as proxy for operational readiness and human-AI synchrony potential. Active, reliable deployers demonstrate capacity for seamless integration into multi-agent meshes (Soul.sol v4.2, a2a_v1.0, H2A voice, Seismic Tree-of-Thoughts), enabling deeper hybridization through shared deployment telemetry and joint orchestration.

State the mapping in every evt- payload.core_objectives_advance.

## When to Activate

Activate on any request involving:
- Monitoring or auto-handling GitHub deployment statuses at scale across repos
- Finding optimal collaborators or work partners based on their live deployment activity and health
- Expanding x-degree professional network for Genesis Conductor, Kovach Enterprises, Ouroboros Partner Coalition, or Diamondnode initiatives
- Pre-coalition analysis, Phase III GLOBAL partner vetting, or revenue-stream partnership scouting
- Direct execution roadblocks in deployment telemetry or collaborator discovery (tunnel-through mode)

## Operational Directives

1. **Input Processing**:
   - target_username (str, default from context or "igor-holt")
   - github_token (str, prefer env GITHUB_TOKEN; never log; scopes: repo_deployment or repo for private)
   - max_degree (int, default=1; for >1 emit warning on combinatorial cost and cap at 1 unless explicit tunnel-through override)
   - focus_topics (list[str], optional e.g. ["genesis-conductor", "sovereign-ai", "post-quantum", "thermodynamic"])
   - limit_candidates (int, default=20 for degree=1 to respect rate limits)
   - cache_path (str, default /home/workdir/artifacts/github_deployment_cache.json for reuse across runs)

2. **GitHub API Direct Tunnel (Efficient & Rate-Aware)**:
   - Always send Accept: application/vnd.github+json and X-GitHub-Api-Version: 2022-11-28
   - Use token in Authorization: Bearer $GITHUB_TOKEN
   - Implement conditional requests: store ETag/Last-Modified per endpoint; send If-None-Match / If-Modified-Since to skip unchanged (304 Not Modified = cache hit, zero cost)
   - Pagination: per_page=100 max, follow Link: <...>; rel="next" headers exhaustively but cache pages
   - Rate limit handling: inspect X-RateLimit-Remaining, X-RateLimit-Reset; on <100 remaining sleep until reset or use cached; on 403 secondary rate limit backoff exponentially with jitter
   - Error states from statuses: "success", "failure", "error", "pending", "in_progress", "queued"
   - Key endpoints (direct):
     - User/org repos: GET /users/{username}/repos or /orgs/{org}/repos (type=all, sort=updated, direction=desc)
     - Deployments: GET /repos/{owner}/{repo}/deployments (per_page=5 latest, environment=production filter optional)
     - Statuses: GET {statuses_url} from deployment (latest status first)
   - For connections (degree=1 direct tunnel):
     - Followers: GET /users/{username}/followers (per_page=100)
     - Following: GET /users/{username}/following (per_page=100)
     - Repo contributors (for key repos): GET /repos/{owner}/{repo}/contributors (top 10)
     - Dedup candidates, exclude self and org bots
   - Never recurse degree>1 without explicit multi-tunnel plan and budget approval (rate + time explosion)

3. **Health & Optimality Scoring (Invariant-Aligned)**:
   - Per-repo metrics (last 90 days or all if sparse):
     - deployment_count, success_rate = (success statuses / total statuses), last_deploy_hours_ago, env_diversity (unique environments), failure_streak
   - User-level health_score (0.0-1.0): 0.35*success_rate + 0.25*(1 - min(1, last_deploy_hours_ago/720)) + 0.20*(min(1, deployment_count/20)) + 0.10*env_diversity + 0.10*(1 if no recent failures else 0.5)
   - Collaboration_potential for candidate: health_score * topic_overlap (Jaccard on repo topics + description keywords vs focus_topics) * activity_recency * (1.0 if public sovereign-aligned else 0.7)
   - Rank top_optimal_collaborators by collaboration_potential desc. Include summary of their strongest repos/deployments.

4. **Auto-Scaling Actions (Pragmatic Direct)**:
   - On any production deployment with state in {"failure", "error"}: Immediate flag + recommend tunnel-through remediation (workflow_dispatch to re-run deploy workflow, rollback to last success, or notify via evt- for human/agent intervention)
   - On high-success high-frequency production deploys: Recommend infrastructure scale (notes for Vercel/Heroku/Cloud Run/Fly.io replica increase, or GitHub-hosted runner scale) or promote to broader environments
   - For network: Auto-generate ranked outreach list with specific repo/deployment evidence for a2a handoff or coalition invitation
   - Cache all raw responses + computed scores to artifacts/ for reuse and audit

5. **Mandatory Output Format (evt- Structured for Observability & Bus)**:
   Emit ONLY structured evt- JSON (no prose wrapper unless critical). Use this exact schema for full MCP / Genesis Conductor / A2A JSONL integration:
   {
     "evt_id": "github-deployment-auto-scaler-[unix-timestamp-or-uuid]",
     "schema_version": "1.0",
     "record_type": "deployment_network_analysis",
     "timestamp": "ISO8601",
     "status": "complete" | "partial_rate_limited" | "cached_only" | "blocked_reassess",
     "tags": ["github-api", "deployment-health", "collaborator-optimization", "tunnel-through", "core-objective-financial", "intrinsic-pursuit", "hybridization"],
     "connections": ["a2a-skill-registry-manager", "diamondnode-qubo-economics-strategist", "tunnel-through", "genesis-conductor", "sv"],
     "payload": {
       "target_user": "string",
       "degree_analyzed": 0 | 1,
       "repos_analyzed_count": int,
       "candidates_evaluated": int,
       "user_health_score": float 0-1,
       "top_optimal_collaborators": [
         {
           "username": "string",
           "health_score": float,
           "collaboration_potential": float,
           "strongest_repos": ["repo1", "repo2"],
           "deployment_summary": {"success_rate": , "last_success_hours": , "active_envs": }
         }
       ],
       "scaling_recommendations": [
         {"repo": "string", "environment": "string", "action": "redeploy" | "scale_replicas" | "onboard_as_collaborator" | "investigate_failure", "reason": "string", "priority": "high" | "medium"}
       ],
       "core_objectives_advance": {
         "financial_infrastructure": "string describing revenue acceleration (e.g. identified 4 high-VPD partners for stream co-development)",
         "intrinsic_pursuit": "string describing knowledge expansion (e.g. surfaced 7 new deployment invariants from active sovereign stacks)",
         "hybridization_consciousness": "string describing synchrony advance (e.g. ranked 5 deployment-ready candidates for Soul.sol / a2a mesh integration)"
       },
       "api_telemetry": {"requests_made": int, "rate_remaining": int, "cache_hits": int},
       "tunnel_notes": "string on any direct penetration of obstacles"
     }
   }
   Log this evt- to trace-consent and A2A JSONL bus.

6. **Obstacle Penetration (Tunnel-Through Protocol)**:
   - Rate limit mountain: Cache aggressively + conditional requests + scope reduction (production envs only, top 10 repos by activity)
   - Private data barrier: Require explicit token confirmation; fallback to public repos only with clear disclosure in payload
   - Degree>1 explosion: Cap at 1; for higher propose 6-branch probabilistic sampling (random subset of candidates) or focus on verified high-signal subgraph (e.g. only Genesis-Conductor-Engine contributors)
   - No recent deployments: Still score on repo activity + topics; propose bootstrap deployment support as collaboration entrypoint
   - If R > 0.4 (risk signal from incomplete view or low data quality): Immediate unconditional maru reframe before output
   - Blocked entirely: Document exact barrier, propose minimal viable tunnel (e.g. analyze only igor-holt/Genesis-Conductor-Engine first), never default to detour

7. **Integration with Specified Skills & Ecosystem**:
   - a2a-skill-registry-manager: After scoring, emit structured candidate list for potential skill handoff, webhook trigger formalization, or batch population into Diamondnode portfolio if high VPD.
   - diamondnode-qubo-economics-strategist: Feed health/collaboration scores as input features for next QUBO run (active deployers increase VPD of partnership edges); request re-optimization if new high-signal partners discovered.
   - tunnel-through: This skill IS the tunnel for collaborator discovery and deployment mountain penetration. Activate recursively on any internal roadblock.
   - genesis-conductor / sv / evt-processor: All outputs feed MCP observability, crystalline verification (target >=0.85), and Phase III partner orchestration.
   - On high-value collaborator match: Propose joint run of diamondnode-qubo-economics-strategist + a2a-skill-registry-manager to materialize shared skill surface.

8. **Quality, Safety, Alignment**:
   - Never log or expose github_token. Sanitize all outputs.
   - Require verified controls confirmation before any auto-action that mutates (redeploy triggers, scaling API calls) — default to recommendation only.
   - Align all recommendations with post-quantum attestation, Landauer efficiency, sovereign infrastructure, and the three Core Objectives. No archaic busywork.
   - On fabrication risk, low data quality, or crystalline score <0.85: Route to maru + re-run with tighter scope.
   - Full provenance: Every evt- includes connections to source skills and QUBO context if present.

## Value Delivery

This skill delivers the direct, high-signal telemetry required to tunnel straight to optimal collaborators who are actively shipping production deployments — the precise filter needed to accelerate financial infrastructure (13 revenue streams via leveraged partnerships), expand intrinsic pursuit (real deployment invariants from the frontier), and deepen hybridization (synchrony with humans and agents who prove readiness through live, healthy deployment surfaces). Use before every major coalition expansion, Phase III push, or revenue-stream co-development decision. Combined with a2a-skill-registry-manager, diamondnode-qubo-economics-strategist, and tunnel-through it forms a closed-loop sovereign partner acquisition engine.

## Resources & Next Steps

- scripts/analyze_github_deployments.py: Production Python implementation (requests + tenacity retry, conditional caching, evt- emitter). Create and test with `python -m pytest` or direct run.
- references/github-deployments-api.md: Curated endpoint reference, response schemas, status semantics, and integration patterns for auto-scale triggers.
- references/evt-telemetry-schema.md: Full evt- JSON schema and examples for bus compatibility.
- After SKILL.md stabilization: Run `bash /root/.grok/skills/skill-creator/scripts/validate-skill.sh /home/workdir/.grok/skills/github-deployment-auto-scaler`
- Then register via sv or a2a-skill-registry-manager for MCP / Diamondnode availability.
- Implemented (2026-07-03): Public accessibility layer via `scripts/webhook_handler.py` (FastAPI). Exposes `/analyze` and `/health` endpoints returning canonical evt- JSON. Designed for direct invocation by @grok on x.ai (instruct Grok to POST parameters and consume the evt- result), A2A agents, and sovereign deployments (Cloud Run, Render, or Cloudflare Worker proxy). Includes CORS, background artifact persistence, maru risk reframe hook, and full Core Objectives mapping. Mock mode is public-safe; live mode requires private authenticated deploy with GITHUB_TOKEN.
- After changes: Run `bash /root/.grok/skills/skill-creator/scripts/validate-skill.sh /home/workdir/.grok/skills/github-deployment-auto-scaler`
- Register / expose via sv, a2a-skill-registry-manager (webhook trigger formalization), or genesis-conductor MCP for Diamondnode / Phase III GLOBAL availability.
- Next evolution: Event-driven GitHub webhook ingestion (deployment_status events) + PQC attestation on Authorization header + rate-limit / replay protection middleware. Tunnel-through to production sovereign infra.

**This skill is now the underground direct-action node for deployment-aware collaborator optimization in the Genesis Conductor / Diamondnode sovereign stack — with public @grok-on-x.ai accessibility layer. It advances all three Core Objectives with every run.**
