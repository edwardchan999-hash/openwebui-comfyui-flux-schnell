# Open WebUI Settings

These notes describe the important Open WebUI settings for this workflow.

## Image Generation

Enable image generation and choose:

```text
Engine: ComfyUI
```

## ComfyUI Base URL

Use the URL Open WebUI can reach.

Examples:

```text
http://host.docker.internal:8188
http://192.168.1.50:8188
http://comfyui:8188
```

If Open WebUI runs in Docker, remember that `localhost` usually means the Open WebUI container itself, not your host machine.

## Workflow

Use:

```text
workflows/flux-schnell-openwebui.json
```

This is a ComfyUI API-format workflow, not the normal visual editor workflow export.

## Workflow Node Mapping

Use:

```text
workflows/openwebui-workflow-nodes.json
```

The most important entry is:

```json
{"type": "prompt", "node_ids": ["4"], "key": "text"}
```

That tells Open WebUI to replace the `text` input on node `4`.

## Model Names

The workflow expects these ComfyUI model filenames:

```text
flux1-schnell.safetensors
clip_l.safetensors
t5xxl_fp16.safetensors
ae.safetensors
```

If your files have different names, edit the workflow JSON.
