# Third tool: `write_note`

I added `write_note` so the agent can persist a result after reading input and calculating it. Its description says that it appends text, accepts only `.txt` paths under `outputs/`, and should be used only when the user explicitly asks to save or record something. These details are part of the interface: “append” prevents the model from assuming that existing text will be replaced, the path and extension constraints describe the tool's safety boundary, and the explicit-request condition discourages unnecessary writes. The implementation also rejects empty content, content over 4,000 characters, and paths that escape `outputs/`.

## Run

Set `OPENAI_API_KEY`, `OPENAI_BASE_URL`, and `AGENT_MODEL` in the shell without writing their secret values to this repository. For OpenRouter, `OPENAI_BASE_URL` is `https://openrouter.ai/api/v1`.

From this directory, run:

```bash
python first_agent.py "Read notes.txt, calculate the requested total, and save it with write_note using the path result.txt."
```
