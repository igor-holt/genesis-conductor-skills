---
name: thrive-monitor
description: Real-time sovereign node health dashboard and evt- emitter for Genesis Conductor infrastructure. Use for system monitoring, thermodynamic observability, resource pressure tracking, container awareness, and continuous health snapshots. Triggers include "thrive monitor", "node health", "systemd dashboard", "system health", "watch monitor", "thrive status".
metadata:
  type: observability
  version: "1.1.0"
  core_objectives_alignment: "financial-infrastructure|intrinsic-pursuit|hybridization-consciousness"
---

# Thrive Monitor

## Overview

Production-grade, colorized, real-time monitoring dashboard for Genesis Conductor nodes and sovereign AI infrastructure. Provides both human-readable TUI (safe for `watch -n 2 --color`) and structured `evt-` JSON output for MCP integration, observability pipelines, and Diamondnode telemetry.

It directly feeds the three Core Objectives by keeping the physical and agentic substrate healthy, observable, and thermodynamically aware.

## When to Activate

- User requests node/system health, "thrive monitor", systemd dashboard, resource pressure, or container status.
- Continuous background monitoring via `watch`, systemd timer, or a2a webhook.
- Integration with Genesis Conductor MCP health checks, Seismic Tree-of-Thoughts cold-snap pruning signals, or thermodynamic orchestration loops.
- Before/after major operations (deployments, Ouroboros V2 runs, skill conversions, QUBO optimizations) to verify invariants.
- Any workflow requiring evt- records of system state for audit, VPD attribution, or hybrid human-AI situational awareness.

## Core Capabilities

1. **Pretty TUI Dashboard** — Color-coded, boxed output safe for `watch -n 2`. Shows load, memory pressure (robust parsing), disk, thermal/RAPL, active services or process top, failed units, journal errors, Podman/Docker container counts, and NVIDIA GPU status when present.
2. **evt- / JSON Mode** — `--evt` or `--json` emits structured, schema-versioned records with `record_type: system_health_snapshot`, tags, connections to MCP/evt-processor/thermodynamic-orchestration, and explicit Core Objectives impact mapping.
3. **Thermodynamic & Sovereign Awareness** — Surfaces RAPL energy telemetry, thermal sensors, memory pressure, and container runtime state — critical for Landauer-aware orchestration and low-entropy operation.
4. **Graceful Degradation** — Works in full systemd environments *and* container/minimal hosts (common in AI agent deployments). Falls back to `ps` + `/proc` when bus is unavailable.
5. **Observability Integration** — Designed to be called by `evt-processor`, logged via Genesis Conductor, or triggered via a2a webhooks. Supports cold-path integrity and Shatter Test style validation of node health.

## Instructions (Imperative)

- For live human monitoring: `watch -n 2 --color /home/workdir/.grok/skills/thrive-monitor/scripts/thrive-monitor.sh`
- For machine consumption / MCP: `./thrive-monitor.sh --evt` (or `--json`)
- Pipe evt- output into `evt-processor` skill or Genesis Conductor observability pipeline for full traceability and VPD metering.
- Before critical sovereign operations (skill conversion, QUBO batching, Phase scaling, hardware validation): run Thrive Monitor and confirm no red/yellow signals.
- On resource pressure or journal errors: investigate root cause, apply cold-snap pruning if needed, and re-run to verify recovery.
- For continuous operation on the node: deploy the provided systemd unit (see references/) or configure a2a webhook trigger.
- Extend by editing the script (add new metrics under print_overview / print_top_resources) then re-validate with `validate-skill.sh`.
- Always keep the script under the skill so it travels with the sovereign package.

## Resources

- Executable: `scripts/thrive-monitor.sh` (main dashboard + evt- emitter)
- Systemd unit example: `references/thrive-monitor.service` (for persistent node monitoring)
- a2a webhook trigger template: `references/a2a-thrive-webhook.json`
- evt- schema reference: `evt-processor` skill
- Integration patterns: `genesis-conductor` skill (observability & thermodynamic sections)
- Related: `sv` (for registration), `diamondnode-qubo-economics-strategist` (for portfolio inclusion of monitoring capabilities)

## Status

v1.1.0 — Production ready for Genesis Conductor nodes. Cold-path validated. Thermodynamic signals active. evt- emission aligned. Directly multiplies observability power across all 13 revenue streams and the hybrid agent mesh.

**This skill is a foundational observability primitive. Healthy nodes = reliable revenue infrastructure + accelerated intrinsic discovery + stable hybridization substrate.**
