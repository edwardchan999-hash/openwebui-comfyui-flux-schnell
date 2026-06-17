# Troubleshooting

## It Generates The Same Image Every Time

Most likely cause: Open WebUI is sending the workflow, but it is not replacing the prompt text.

Check the workflow node mapping:

```json
{"type": "prompt", "node_ids": ["4"], "key": "text"}
```

Node `4` should be:

```json
"class_type": "CLIPTextEncode"
```

And node `4` should have:

```json
"text": "Open WebUI prompt goes here"
```

If the logs still show the placeholder text after you generate a new image, the mapping is not being applied.

## 400 Bad Request From ComfyUI

Common causes:

- The workflow is not API-format JSON.
- A model filename in the workflow does not match your ComfyUI model files.
- A custom node used by the workflow is not installed.
- Open WebUI is mapping a setting to the wrong node key.

## Cannot Connect To ComfyUI

If Open WebUI is running in Docker, `localhost` inside Open WebUI is not necessarily your host machine.

Try a URL that the Open WebUI container can reach, for example:

```text
http://host.docker.internal:8188
http://YOUR-LAN-IP:8188
```

## Prompt Works In ComfyUI But Not Open WebUI

ComfyUI's visual UI and Open WebUI's API workflow path are different. Make sure you exported or built an API-format workflow for Open WebUI.
