# Model files and licenses

Paths are relative to the active ComfyUI root. Download only the workflow you intend to run. Preserve every exact filename; do not rename another file to satisfy a selector.

## Required files

| Applies to | File | Target folder | Official pinned download | License |
| --- | --- | --- | --- | --- |
| Normal | `qwen_image_2.1_int8_convrot.safetensors` | `models/diffusion_models/` | [Comfy-Org/Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/diffusion_models/qwen_image_2.1_int8_convrot.safetensors) | Qwen Research License; non-commercial |
| Turbo | `qwen_image_2.1_turbo_int8_convrot.safetensors` | `models/diffusion_models/` | [Comfy-Org/Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/a8342359c61979b06a8dafb1a47991fe1f30e994/diffusion_models/qwen_image_2.1_turbo_int8_convrot.safetensors) | Qwen Research License; non-commercial |
| Both | `qwen3vl_8b_int8_convrot.safetensors` | `models/text_encoders/` | [Comfy-Org/Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/text_encoders/qwen3vl_8b_int8_convrot.safetensors) | Qwen Research License; non-commercial |
| Both | `qwen_image_2.1_vae_bf16.safetensors` | `models/vae/` | [Comfy-Org/Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/9a44dbdb47cefd046be9c0a13476192f34c8db8e/vae/qwen_image_2.1_vae_bf16.safetensors) | Qwen Research License; non-commercial |

The Qwen Research License permits non-commercial research or evaluation use. Commercial use requires a separate license from the model owner. Review the [official Qwen Image 2.1 license](https://huggingface.co/Qwen/Qwen-Image-2.1/blob/main/LICENSE) before downloading or using the weights.

## Optional LoRAs

These rows are saved **off** and are not required for the documented default paths.

| Applies to | File | Target folder | Official pinned download | License |
| --- | --- | --- | --- | --- |
| Normal and Turbo | `bfs_head_v1.1_qwen_2.1.safetensors` | `models/loras/` | [BFS Best Face Swap](https://huggingface.co/Alissonerdx/BFS-Best-Face-Swap/resolve/0ca3913ade4b4ada458d60c232354e8586c4c181/bfs_head_v1.1_qwen_2.1.safetensors) | MIT |
| Normal only | `p_qwen_image_2.1_8step_v0.1.safetensors` | `models/loras/` | [Pruna Qwen Image 2.1](https://huggingface.co/PrunaAI/Pruna-Qwen-Image-2.1/resolve/113e63bb993001b3411eb3470b84fc444040cd7e/p_qwen_image_2.1_8step_v0.1.safetensors) | Qwen Research License; non-commercial |

The Pruna adapter is a Qwen Image 2.1 derivative and retains the Qwen Research License restrictions. The BFS model card declares MIT.

## Optional Turbo alternative

The Turbo note also identifies `qwen_image_2.1_turbo_bf16.safetensors` as a higher-memory alternative to the selected INT8 checkpoint. Place it in `models/diffusion_models/` and select it manually only if your system can support it: [official pinned download](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/a8342359c61979b06a8dafb1a47991fe1f30e994/diffusion_models/qwen_image_2.1_turbo_bf16.safetensors). It uses the Qwen Research License and is not required by the distributed JSON.

## Redistribution boundary

This repository redistributes no model, text-encoder, VAE, or LoRA weights. Each download remains governed by its source license and terms. A working URL does not replace license review.
