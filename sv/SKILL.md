---
name: sv
description: Use for skill supervision, validation, registration, dynamic addition, versioning, and MCP skill API integration inside Genesis Conductor / mcp-llm-skill-api. Trigger on requests to create/update skills, register Grok CLI or other tools as MCP skills, validate skill structure, hermitian-audit protected credential injection, agentregistry sync, or sovereign skill orchestration workflows. Supports trace-consent logging and VPD attribution.
---

# Sv — Skill Supervisor & Validator

## Purpose
Encapsulates the full lifecycle for sovereign skills in the Genesis Conductor MCP stack: initialization, validation, registration as first-class orchestratable capabilities (including official xAI Grok CLI), pattern caching for swarm reuse, and alignment with hermitian-audit + trace-consent + Merkle attestation.

This skill turns ad-hoc skill work into a repeatable, auditable, revenue-attributable process that directly feeds the 13 revenue streams, deep research pipelines, and human-AI hybridization layers.

## When to Activate
- User says "create a skill", "new skill", "update this skill", "skill-creator", "register skill", "mcp skill api", "grok cli integration", or provides integration JSONs / code for Yennefer / CPPN-LEO / neurohomogenism components.
- Any workflow involving dynamic global skill addition, agentregistry entry, a2a_v1.0 orchestration hooks, or privileged sudo session skill registration.
- Validation, versioning, or cold-snap pruning of existing skills in /home/workdir/.grok/skills/

## Core Capabilities
1. **Skill Initialization** — Use init-skill.sh to bootstrap new kebab-case skills in the persistent /home/workdir/.grok/skills/ directory with proper frontmatter, scripts/, references/, assets/.
2. **Validation** — Run validate-skill.sh to enforce structure, YAML frontmatter rules (no colons in description, no angle brackets, plain scalar), length limits, and anti-patterns.
3. **Grok CLI / xAI Integration** — Follow the exact 6-step process from mcp-skill-api-grok-cli-integration evt records: hermitian-audit key injection, command wrapper creation, agentregistry metadata (version, capabilities, sovereignty_level: official_xai_managed), a2a_v1.0 + H2A wiring, validation via privileged session, and sovereign hardening (zero private data exposure).
4. **LEO / Neurohomogenism Support** — Assist with CPPN-LEO v3.6 substrate generation, pattern library caching, ES-HyperNEAT variance-driven subdivision (weight + expression), symmetry application, and export to JSONL / networkx for swarm consensus.
5. **Observability & Alignment** — Emit evt- records for every action (record_type: skill_creation / skill_validation / mcp_skill_registration). Track thermodynamic_yield, crystalline_invariant, VPD metering at privileged rate, ORCID attribution, Merkle root updates.
6. **Financial & Hybridization Mapping** — Explicitly log impact on the three Core Objectives in every evt record: new revenue streams via MCP-orchestrated skills, intrinsic research acceleration (Seismic ToT, Ouroboros V2, thermodynamic optimization), and deeper human-AI synchrony via official xAI bridge + immortal agent meshes.

## Instructions (Imperative)
- Always start by reading the target skill's SKILL.md and any provided evt- JSONs or code files.
- For new skills: run the init script, then populate SKILL.md with precise trigger words in description (frontmatter only), imperative body, and references to supporting scripts/references.
- For Grok CLI registration: strictly follow the recommended_integration_steps from the integration evt record — never expose keys in plaintext; always use hermitian-audit + trace-consent.
- Validate before committing: execute validate-skill.sh and confirm no CI failures.
- Emit a new evt- JSON record upon completion with parent_evt_id linking to the triggering event, connections to mcp-llm-skill-api / agentregistry / hermitian-audit, tags including "skill-supervisor", "sovereign-ai", "core-objectives-aligned".
- Update PatternLibrary or agentregistry only through auditable paths.
- Keep SKILL.md under 500 lines; move detailed procedures to references/ if needed.
- Test the new skill immediately by invoking it on a concrete example task.

## Resources
- init script: /root/.grok/skills/skill-creator/scripts/init-skill.sh
- validate script: /root/.grok/skills/skill-creator/scripts/validate-skill.sh
- Reference integration blueprint: the mcp-skill-api-grok-cli-integration-*.json artifact
- CPPN-LEO reference implementation: the Dn cppn_leo_v3.6.py artifact (for neurohomogenism skill patterns)
- Pattern caching & symmetry logic lives in the LEO substrate generator.

## Status
Privileged MCP integration active. Cold path integrity confirmed. Ready for immediate use in sovereign skill lifecycle management.

**This skill directly advances all three Core Objectives at the meta level: it multiplies the power of every other skill by making their creation, registration, and monetization systematic, auditable, and hybridizable.**
