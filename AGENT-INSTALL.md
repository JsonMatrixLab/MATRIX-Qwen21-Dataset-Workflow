# AI-agent installation entry point

This repository contains two separate fail-closed installation contracts:

- [Normal workflow contract](workflows/normal/AGENTS.md)
- [Turbo workflow contract](workflows/turbo/AGENTS.md)

Select exactly one contract unless the operator explicitly asks for both. Do not queue either workflow during installation verification.

## Mandatory boundaries

- Resolve the active ComfyUI root and launcher before changing anything.
- Never overwrite, merge, delete, move, or disable an existing installation.
- Never inspect, print, copy, or store credential values or private reference images.
- Installation does not authorize a paid action, provider call, or workflow execution.
- Verify exact custom-node commits, model filenames, startup status, and the visible missing-node state; file presence alone is not success.
- Preserve ComfyUI core, Python, Torch, CUDA, user workflows, outputs, and settings.
- Stop on any path conflict, unavailable source, license issue, dependency conflict, missing node, or unverified UI state.

Report observed versions, commits, file presence, visible verification, and blockers. State that no workflow was queued.
