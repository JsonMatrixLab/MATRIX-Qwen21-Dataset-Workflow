# Install MATRIX Qwen Image 2.1 Dataset Workflow V4

This guide installs package version `1.0.0` into an existing ComfyUI instance without replacing a working installation.

## Requirements

- A working local ComfyUI installation. The build boundary was ComfyUI `0.37.0` plus commit `b33e2b55cae074eca5aec96283cceac19aa249ba` and frontend `1.53.6`.
- Git and the Python environment used by that ComfyUI installation.
- Enough storage and GPU memory for the selected Qwen Image 2.1 files.
- The exact custom-node commits and model files below.

Stop if an existing custom-node folder has uncommitted changes or a different remote. Do not overwrite or merge it automatically.

## 1. Install the custom nodes

Stop ComfyUI first. From the active `ComfyUI/custom_nodes` folder, install clean folders at these commits:

| Folder | Repository | Required commit | Provides |
| --- | --- | --- | --- |
| `MATRIX-LAB-Nodes` | `https://github.com/JsonMatrixLab/MATRIX-LAB-Nodes.git` | `f71fb38dea39f6052ff4e883c18fecc7ec07d199` | `MATRIX_QwenImage21Resolution` |
| `ComfyUI-Fantastic-MiniMaxH3-PromptBuilder` | `https://github.com/Adudeguyman/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder.git` | `23038f5050acdcbb8e938bfd7c87a18d2cc84aab` | `MiniMaxH3MediaLoader`, `MiniMaxH3ReferenceSplitter` |
| `rgthree-comfy` | `https://github.com/rgthree/rgthree-comfy.git` | `449c58fcdd612f7733e54c51f6758ead63fa180b` | Power LoRA Loader, Fast Groups Bypasser, Fast Actions Button |

Example for a new, non-conflicting installation:

```bash
git clone https://github.com/JsonMatrixLab/MATRIX-LAB-Nodes.git ComfyUI/custom_nodes/MATRIX-LAB-Nodes
git -C ComfyUI/custom_nodes/MATRIX-LAB-Nodes checkout f71fb38dea39f6052ff4e883c18fecc7ec07d199

git clone https://github.com/Adudeguyman/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder.git ComfyUI/custom_nodes/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder
git -C ComfyUI/custom_nodes/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder checkout 23038f5050acdcbb8e938bfd7c87a18d2cc84aab

git clone https://github.com/rgthree/rgthree-comfy.git ComfyUI/custom_nodes/rgthree-comfy
git -C ComfyUI/custom_nodes/rgthree-comfy checkout 449c58fcdd612f7733e54c51f6758ead63fa180b
```

Use each repository's installation instructions for Python dependencies, always with the Python interpreter that launches ComfyUI. Review dependency changes before accepting anything that would replace Torch, CUDA, or the ComfyUI core environment.

The required MATRIX node is present in the pinned public commit but not in the latest tagged MATRIX-LAB-Nodes release. Use the commit above.

## 2. Install the models

Download the required files from [MODELS.md](MODELS.md), preserve the exact filenames, and place them under the active ComfyUI root. The two LoRAs are optional for Normal and start off. Turbo's BFS row also starts off.

No model weights are included in this repository.

## 3. Restart and verify

Start ComfyUI through its normal launcher and inspect startup output. Stop on any import or registration error.

Load one file through **Workflow > Open** or by dragging it onto the canvas:

- `workflows/normal/MATRIX-Qwen21-Dataset-V4.json`
- `workflows/turbo/MATRIX-Qwen21-Dataset-V4-Turbo.json`

Confirm that no node is red or missing. Verify the selected model filenames against [MODELS.md](MODELS.md). Do not save over the repository copy during compatibility checks.

## 4. Add the pictures

Open each Fantastic H3 Media Loader panel and add references without gaps:

- HEAD and HEAD 360: face first; extra face views are optional.
- UPPER BODY 360: face first, upper-body/outfit second; further views are optional.
- FULL BODY 360: face first, upper-body second, full-body/outfit-and-shoes third; further views are optional.

The same person and compatible outfit should appear throughout. Example local names are `face.png`, `body.png`, and `extra.png`; the actual names do not matter. The selected resolution aspect ratio must match the input-picture aspect ratio.

## 5. First run

Keep the optional LoRAs off for the documented defaults. Choose which section rows are enabled, inspect their prompts and save paths, then queue only with the operator's approval. Generated files normally appear below `ComfyUI/output/dataset/`.

## Update or uninstall

For an update, clone a new version into staging, inspect it, and ask before replacing an existing folder. Never merge versions in place.

To uninstall, stop ComfyUI and remove only the three folders you installed for this workflow. Preserve shared node packs, model files, workflows, outputs, and user settings unless the owner explicitly requests their removal.
