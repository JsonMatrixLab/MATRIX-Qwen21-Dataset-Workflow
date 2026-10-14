# Fail-closed installation contract: Normal workflow

Install only `MATRIX-Qwen21-Dataset-V4.json` from this folder. This contract does not authorize changes to accounts, publication, deletion, replacement of existing installs, or image generation.

## Hard boundaries

- Resolve the actual ComfyUI root and launcher Python; do not assume a path.
- Do not overwrite, merge, move, disable, or delete an existing custom-node installation.
- Do not change ComfyUI core, frontend, Python, Torch, or CUDA to force compatibility.
- Do not inspect, print, copy, or store credentials or private images.
- Do not download model files until the operator accepts their licenses and storage cost.
- Do not queue the workflow during installation verification.
- Do not save over the repository workflow while checking compatibility.

## Prerequisite check

Record the ComfyUI version, core commit, frontend version, launcher Python, GPU, and current custom-node folders. The build boundary was ComfyUI `0.37.0` plus `b33e2b55cae074eca5aec96283cceac19aa249ba`, frontend `1.53.6`. If the host differs, report the difference; do not silently change it.

Require these exact public custom-node commits:

| Repository | Target folder | Commit | Required node types |
| --- | --- | --- | --- |
| `https://github.com/JsonMatrixLab/MATRIX-LAB-Nodes.git` | `custom_nodes/MATRIX-LAB-Nodes/` | `f71fb38dea39f6052ff4e883c18fecc7ec07d199` | `MATRIX_QwenImage21Resolution` |
| `https://github.com/Adudeguyman/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder.git` | `custom_nodes/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder/` | `23038f5050acdcbb8e938bfd7c87a18d2cc84aab` | `MiniMaxH3MediaLoader`, `MiniMaxH3ReferenceSplitter` |
| `https://github.com/rgthree/rgthree-comfy.git` | `custom_nodes/rgthree-comfy/` | `449c58fcdd612f7733e54c51f6758ead63fa180b` | `Power Lora Loader (rgthree)`, `Fast Groups Bypasser (rgthree)`, `Fast Actions Button (rgthree)` |

If a target exists, verify its remote, commit, and clean state. Continue only when it is already the identical required checkout. Otherwise stop and request a recoverable, operator-approved replacement plan.

## Required model files

Download only after license approval. Preserve exact names.

| Target path below ComfyUI | Official URL |
| --- | --- |
| `models/diffusion_models/qwen_image_2.1_int8_convrot.safetensors` | `https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/diffusion_models/qwen_image_2.1_int8_convrot.safetensors` |
| `models/text_encoders/qwen3vl_8b_int8_convrot.safetensors` | `https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/text_encoders/qwen3vl_8b_int8_convrot.safetensors` |
| `models/vae/qwen_image_2.1_vae_bf16.safetensors` | `https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/vae/qwen_image_2.1_vae_bf16.safetensors` |

All three use the Qwen Research License and are non-commercial. No weights are included here.

Optional rows, both saved off:

| Target path below ComfyUI | Official URL | License |
| --- | --- | --- |
| `models/loras/bfs_head_v1.1_qwen_2.1.safetensors` | `https://huggingface.co/Alissonerdx/BFS-Best-Face-Swap/resolve/0ca3913ade4b4ada458d60c232354e8586c4c181/bfs_head_v1.1_qwen_2.1.safetensors` | MIT |
| `models/loras/p_qwen_image_2.1_8step_v0.1.safetensors` | `https://huggingface.co/PrunaAI/Pruna-Qwen-Image-2.1/resolve/113e63bb993001b3411eb3470b84fc444040cd7e/p_qwen_image_2.1_8step_v0.1.safetensors` | Qwen Research License; non-commercial |

## Procedure

1. Stop ComfyUI through its normal controller.
2. Clone missing custom-node repositories into new target folders and check out the exact commits above. Refuse path conflicts.
3. Read each pinned checkout's dependency instructions. Use the launcher Python and present any transaction that would alter Torch or CUDA for operator approval.
4. Verify each repository commit with `git rev-parse HEAD`.
5. Verify required model files at the exact paths. Never substitute or rename another file.
6. Start ComfyUI normally and inspect startup output for import or registration errors.
7. Open `MATRIX-Qwen21-Dataset-V4.json` in the visible ComfyUI UI. Do not migrate or save it.
8. Confirm zero missing/red nodes and verify the selected checkpoint, text encoder, VAE, `25` steps, Euler sampler, and beta scheduler.
9. Confirm both LoRA rows are off.
10. Stop before queueing.

## Reference input contract

When the operator is ready to configure the workflow:

- HEAD and HEAD 360: picture 1 face; optional face views after it.
- UPPER BODY 360: picture 1 face, picture 2 upper body/outfit; optional views after them.
- FULL BODY 360: picture 1 face, picture 2 upper body, picture 3 full body/outfit/shoes; optional views after them.
- Never leave a gap. All references must depict the same authorized character in compatible clothing.
- The input-picture aspect ratio must match that section's resolution-node aspect ratio.

Neutral local example names are `face.png`, `body.png`, and `extra.png`. Do not copy private images into this repository or an installation report.

## Stop conditions

Stop and report exact evidence if any target path conflicts, repository or commit is unavailable, required model is absent, license approval is missing, dependency resolution would replace the host runtime, startup reports an error, a required node type is missing, or the visible graph differs from the checks above.

## Completion report

Report the resolved ComfyUI root, launcher Python, host versions, exact custom-node commits, model paths present or missing, startup status, visible missing-node result, selected model names, LoRA off state, and blockers. State explicitly that no workflow was queued.
