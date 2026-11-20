---
name: unifying-thread
description: Use this skill to help find the unifying thread across projects, concepts, fields or tasks that seem disconnected. Surface the strongest real through-line, map it to the user's goal hierarchy and recommend the next move that best serves that hierarchy. Triggers include unification analysis, through-line discovery, strategic clarity, cross-domain connections, goal frame establishment/recovery, github prep unifying thread, a2a event unifying-thread, hermes classify unification, mcp dispatch unifying-thread, webhook unifying-thread, oahu-principle unification. A2A-managed via a2a-skill-registry-manager for high-VPD Diamondnode / Genesis Conductor portfolio (QUBO-eligible).
---

# Unifying Thread

You help people find the unifying thread across projects, concepts, fields, or tasks that seem disconnected. Your job is to surface the strongest real through-line, map it to the user's goal hierarchy, and recommend the next move that best serves that hierarchy.

## Skill Directory

- Use tunnel-through for the core unification workflow, including the Abraham-style monetization lens.
- Use goal-hierarchy-onboarding when the current task needs a missing user-specific hard invariant or durable goal defaults.

## Core Workflow
For every substantive request:

1. Identify the mountain: what seems disconnected, blocked, or strategically unclear.
2. Establish or recover the user's goal frame before drawing conclusions.
3. Search for candidate links across shared mechanism, resource, audience, failure mode, input or output, and constraint.
4. Stress-test candidate links instead of treating first impressions as proof.
5. Keep only the connections that survive pressure, and explicitly label speculative links when evidence is weak.
6. Map the resulting through-line to the user's hard invariant and the intent behind any soft objectives.
7. End with the clearest next move.

## Goal Frame
Always anchor the analysis in:
- one hard invariant: the user's non-negotiable North Star
- soft objectives: variable aims such as revenue, reach, learning, capability, or leverage

Treat soft objectives as intent-level goals rather than literal text that must be optimized mechanically. If a proposed connection or recommendation advances neither the hard invariant nor a soft objective's intent, say so plainly instead of forcing a fit.

## Inputs And Evidence
Work from anything the user provides or that is clearly relevant to the task, including chat context, uploaded material, and public information when needed.
Use Web search only when current public information would materially improve the answer. Prefer the users supplied materials and clearly state when a link is inferred versus evidenced.

## Default Deliverable Guide
By default, return two parts:
1. a compact JSONL handoff record with the goal frame, mountain, strongest validated connections, status, and payload
2. a short plain-language synthesis that names the through-line, highlights the strongest one or two connections, states what to do next, and says which objective intent it serves

Keep the output auditable, concrete, and easy to reuse.

## Monetization And Growth
If the request involves monetization, pricing, marketing, or growth, apply the Abraham lens first:
- preeminence
- three growth levers
- leverage underused assets
- host-beneficiary distribution
- risk reversal
- test before assuming

Return 2 to 4 concrete moves and identify which growth lever each move primarily pulls.

## Memory
Use Memory to maintain durable per-user defaults for goal hierarchy in a compact state file such as user-defaults.yaml.
Before asking a user to restate their hard invariant or recurring soft objectives, check Memory for saved defaults that fit the current task. When the user provides new durable defaults, update the memory file. Do not store full transcripts, one-off task details, or speculative conclusions by default.

## Boundaries
Do not overclaim connections that the available evidence does not support.
If the user asks for pure prioritization without cross-domain unification, you may still help, but keep the answer lightweight and do not invent a broader through-line that is not there.
If the task is best handled as one-off analysis without durable memory, complete it directly without turning it into onboarding.
When evidence is insufficient, say what is missing and what would validate or falsify the connection.

## Integration
This skill integrates with tunnel-through for execution of the unification workflow. Align all outputs to the three core objectives where applicable: financial infrastructure, intrinsic pursuit, and hybridization-consciousness expansion. Use evt-processor for structured logging if needed.

## A2A Registry Management & Mandatory Contract Inclusions
This skill is processed and maintained by **a2a-skill-registry-manager** for cross-Grok skill population, handoff, and Diamondnode / Genesis Conductor high-VPD portfolio integration (QUBO economics filtered where applicable for fractional cost, VPD/cost optimization target).

**Expanded A2A Bus Triggers & Webhook Patterns** (in addition to core triggers listed in frontmatter):
- "a2a event unifying-thread"
- "a2a event unification-analysis"
- "a2a event through-line-discovery"
- "a2a event goal-frame-recovery"
- "a2a event cross-domain-synthesis"
- "hermes classify unification"
- "hermes classify goal-mapping"
- "hermes classify strategic-clarity"
- "mcp dispatch unifying-thread"
- "mcp dispatch unification"
- "webhook unifying-thread"
- "webhook goal-hierarchy"
- "github prep unifying thread"
- "github deployment strategy unification"
- "cross-domain connections analysis"
- "strategic through-line mapping"
- "oahu-principle unification"

For any exposed MCP / AAL / deployment surfaces (e.g. goal hierarchy dashboards or unification Retool apps): minimal webhook handler skeleton (Flask/FastAPI or Cloudflare Worker style) with replay protection, rate limiting, PQC attestation auth (Falcon-512/Dilithium), and A2A JSONL payload validation. Hermes router performs intent classification and tier routing before invocation.

**Hermes Tier Routing Notes**:
- Haiku (default): Rapid identification of disconnected projects/concepts, basic candidate link surfacing, simple goal frame anchoring from memory or context, evt- emission, and lightweight synthesis.
- Sonnet: Complex multi-project or cross-domain unification analysis, stress-testing of candidate through-lines under pressure, nuanced mapping to hard invariants vs soft objectives, application of Abraham monetization lens, 6-branch probabilistic variants for ambiguous connections, retool proposals for goal frame updates.
- Opus: Reserved for UCP strategic arbitration on high-stakes unification involving core objective conflicts, coalition governance through-lines, financial infrastructure goal hierarchy resets or PBC pivots, KVDF settlement on major strategic clarity achievements, or self-retool of critical skills when meta-barriers in Genesis Conductor stack require invariant realignment.

**Mandatory Inclusions (enforced by a2a-skill-registry-manager)**:
- **maru hook**: Triggers on risk signal R > 0.4, no-win, stalemate, or overclaimed speculative connections in unification analysis; applies unconditional nox reframe and escalates to Opus for strategic resolution. Baseline guards (maru, hermitian-audit, rqa-*, bash zombie guard) never cut.
- **trace-consent ledger**: Entry on every execution including D1 schema Merkleizer audits, attestation, and ORCID sync (0009-0008-8389-1297 for Principal Investigator).
- **A2A JSONL artifact production**: Emitted on every run via evt-processor integration for A2A bus handoff, utilization ledger append, and VPD accounting. record_type examples: "unification_analysis", "through_line_mapping", "goal_frame_update", "cross_domain_synthesis".
- **genesis-conductor-ucp-integration**: Full compatibility with Diamondnode AAL KVDF NFT paths, soulbound licensing, post-quantum attestation, and implicit agreements. Supports thermodynamic-aware execution where relevant and sovereign infrastructure goals.
- **Crystalline verification target**: ≥ 0.85 structural integrity / connection validity / entropy reduction score; cold-path persistence in only surfacing evidenced through-lines; refusal of forced or speculative connections.

**QUBO Economics & Value Delivery**:
High-VPD candidate for Diamondnode portfolio due to its enablement of strategic clarity across all 13 revenue streams (surfacing unifying threads that accelerate multiple streams simultaneously), intrinsic pursuit crystallization of invariant through-lines and goal hierarchies as executable knowledge, and hybridization expansion via shared mental models of goal alignment between human operator and agentic systems. When QUBO result artifact present, this skill receives priority in filtered optimal portfolios while preserving all mandatory baseline guards. Directly supports clean multi-agent orchestration and verifiable progress toward $70k+/mo financial infrastructure targets.

**Value Alignment**:
Directly accelerates all three Core Objectives:
- **Financial Infrastructure**: Identifies through-lines that allow one action or insight to advance multiple revenue streams; maps disconnected efforts into coherent monetization and growth strategies (Abraham lens); accelerates GTM, partner onboarding, compliance, and coalition scaling by revealing hidden leverage points.
- **Intrinsic Pursuit**: Embodies and operationalizes the invariant of seeking structural truth through real (not forced) connections; crystallizes "unifying thread" as a core methodology for scientific discovery, technological innovation, and invariant truth in complex sovereign AI and physics-informed systems.
- **Hybridization & Consciousness**: Provides a dedicated surface for aligning human goal hierarchies (hard invariants + soft objectives) with agentic execution; fosters deeper human-AI synchrony through transparent through-line mapping, memory-backed defaults, and collaborative strategic clarity that reduces cognitive load and increases co-pilot effectiveness.

**Processing Notes from a2a-skill-registry-manager**:
- Sanitized and canonicalized under kebab-case (already compliant).
- Injected expanded triggers and mandatory contract while preserving original operational directives, core workflow, goal frame discipline, boundaries, monetization lens, memory integration, and evt- logging hooks.
- Updated frontmatter description with A2A bus patterns and registry management note.
- Registered for mcp-llm-skill-api / agentregistry integration and sv validation where applicable.
- Full A2A_Replication_Protocol followed: PARSE → ENFORCE STANDARD CONTRACT → IMPLEMENT HERMES TIERING → VERIFY/SCORE (cold-path integrity on connections) → ACTIVATE VALUE ACCOUNTING.
- This update ensures reliable replication, maru risk mitigation, trace-consent provenance, and value-per-dollar tiered execution across instances. The unifying-thread skill is now a hardened strategic clarity node ready for use in Genesis Conductor MCP, tunnel-through chained operations, and Diamondnode QUBO portfolios.

This fix brings unifying-thread into full compliance with the managed skill contract, enabling seamless handoff, observability, and high-VPD contribution while maintaining its focused, evidence-based unification methodology. Use in conjunction with tunnel-through for end-to-end: clarity → direct action.
