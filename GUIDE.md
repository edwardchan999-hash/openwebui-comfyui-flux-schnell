# Open WebUI + ComfyUI + Flux Schnell Guide

The critical mapping for this workflow is:

```json
{"type": "prompt", "node_ids": ["4"], "key": "text"}
```

Node `4` is the `CLIPTextEncode` node, and `text` is the input that Open WebUI must replace with the user's prompt.

## Files

```text
workflows/flux-schnell-openwebui.json
workflows/openwebui-workflow-nodes.json
docs/open-webui-settings.md
docs/troubleshooting.md
```

## Requirements

- Open WebUI with image generation enabled.
- ComfyUI reachable from Open WebUI.
- Flux Schnell model files installed in ComfyUI:
  - `flux1-schnell.safetensors`
  - `clip_l.safetensors`
  - `t5xxl_fp16.safetensors`
  - `ae.safetensors`

## Quick Setup

1. In Open WebUI, enable image generation.
2. Choose `ComfyUI` as the image generation engine.
3. Set your ComfyUI base URL, for example `http://YOUR-COMFYUI-HOST:8188`.
4. Use `workflows/flux-schnell-openwebui.json` as the ComfyUI workflow.
5. Use `workflows/openwebui-workflow-nodes.json` as the workflow node mapping.
6. Save settings and generate an image.

## Common Failure

If every prompt generates the same image, Open WebUI is probably not replacing the placeholder prompt in the ComfyUI workflow.

Check that the prompt mapping points to node `4` with key `text`.

More detail: [Troubleshooting](docs/troubleshooting.md)
