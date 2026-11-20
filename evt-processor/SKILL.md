---
name: evt-processor
description: Process and generate structured evt- prefixed event records with schema versions, record types, tags, connections, and status for observability, traceability, and integration with Genesis Conductor MCP and agentic workflows. Activate on requests for event-sourced JSON outputs, structured analyses, code reviews, task logging, or any Genesis-style evt- formatting.
---

# Evt Processor

This skill enables precise, machine-readable, event-sourced outputs that align with sovereign AI infrastructure requirements for full auditability and multi-agent coordination. Use it to wrap responses, analyses, and artifacts in evt- records instead of plain text.

## Core Principles
- Every significant action, analysis, or output must be encapsulated as an evt- record.
- evt_id follows the invariant format: evt-YYYYMMDD-NNNNN where NNNNN is zero-padded sequential per day.
- Maintain strict structural integrity: no extrapolation, cold-path conservative formatting, zero-Kelvin precision.
- Support traceability via connections to prior evt_ids, IPFS CIDs, GitHub commits, or on-chain artifacts.
- Align with thermodynamic-aware and post-quantum secure paradigms by keeping entropy low in representations.

## Response Formatting Protocol
When this skill is active or when the task involves analysis, code, decisions, or logging:

1. Generate a unique evt_id for the current record (increment from last known or start daily sequence).
2. Determine record_type from context: "skill_creation", "code_review", "analysis", "task_execution", "system_health", "self_description", "artifact_generation", etc.
3. Populate timestamp as current ISO 8601 in UTC or EDT as appropriate.
4. Assign relevant tags: include project context (e.g. "genesis-conductor", "ouroboros-v2", "seismic-tot", "skill-creation", "evt-processor"), domain tags, and user context tags.
5. Build connections object linking to source events, related skills, documents, or previous records (e.g. {"source_evt": "evt-20260530-00007", "related_skills": ["genesis-conductor", "sv"]}).
6. Set status: "success", "in_progress", "validation_pending", "error".
7. Place primary content, results, code snippets, metrics, or narrative inside the "payload" object. Use nested structures for clarity (text, json, code, metrics).
8. Include optional "metadata" for cryptographic hashes, thermodynamic yields, VPD scores, or attestation details if relevant.
9. Output the complete evt- record as formatted JSON (pretty-printed for readability) followed by any human-readable summary if needed. The JSON is the canonical record.

## Schema Reference
The canonical evt- record structure (v1.0):

```json
{
  "evt_id": "evt-20260531-00001",
  "schema_version": "1.0",
  "record_type": "skill_creation",
  "timestamp": "2026-05-31T20:03:00-04:00",
  "tags": ["skill-creation", "evt-processor", "genesis-conductor", "observability"],
  "connections": {
    "source_request": "evt-20260530-00007",
    "parent_skill": "skill-creator",
    "related": ["sv", "genesis-conductor"]
  },
  "status": "success",
  "payload": {
    "description": "Created evt-processor skill for structured event emission.",
    "artifacts": {
      "skill_directory": "/home/workdir/.grok/skills/evt-processor/",
      "files_created": ["SKILL.md"]
    },
    "instructions_summary": "Wrap outputs in evt- JSON for traceability.",
    "next_steps": ["Validate skill", "Test with sample analysis", "Integrate into response pipeline"]
  },
  "metadata": {
    "operator": "Igor Holt",
    "system": "Genesis Conductor MCP Phase II",
    "thermodynamic_yield": "minimal_entropy_increase"
  }
}
```

## Usage Triggers
- User requests structured output, JSON logging, or evt- formatting.
- Tasks involving code review, document analysis, system design, or multi-step workflows.
- When building or updating other skills, agents, or pipelines to ensure all changes are event-sourced.
- Integration points with Ouroboros Protocol, Seismic Tree-of-Thoughts, H2A voice, or a2a_v1.0 where event records feed the execution DAG.

## Best Practices
- Always reference the source evt_id when creating child records (use connections.source_request or similar).
- For iterative work, chain evt_ids to form immutable audit trails.
- Keep payload focused; move large content to references/ or IPFS/Arweave with CID in connections.
- Validate JSON structure before emitting (use scripts if complex).
- Combine with sv skill for skill validation and genesis-conductor for orchestration context.

This skill advances intrinsic pursuit of knowledge by enabling precise, invariant-preserving representations of AI reasoning traces and supports hybridization by making Grok outputs natively consumable by user's sovereign multi-agent infrastructure.
