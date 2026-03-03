# openclaw-model-card

Generate a readable model list (text + image) from `openclaw.json`, with basic consistency checks.

## Features

- Provider-grouped model table (ID / alias / context / multimodal)
- Default model + fallback chain
- Image model + image fallback chain
- Logic checks (missing model refs, alias conflicts, invalid context)
- Optional Markdown-to-image rendering via `wkhtmltoimage`

## Requirements

- Python 3.8+
- Node.js 18+
- `wkhtmltoimage` in PATH (only for `--image`)

## Install

```bash
npm install
```

## Usage

### Text output

```bash
python3 scripts/show-model-config.py --config /path/to/openclaw.json
```

### Image output

```bash
python3 scripts/show-model-config.py --config /path/to/openclaw.json --image ./model-card.png
```

## Config resolution order

1. `--config /path/to/openclaw.json`
2. `OPENCLAW_CONFIG` env var
3. default paths:
   - `/opt/openclaw-data/conf/openclaw.json`
   - `~/.openclaw/openclaw.json`
   - `./openclaw.json`

## Security notes

- No API keys are required by this tool itself.
- Do **not** commit your real `openclaw.json` if it contains secrets.
- Keep generated outputs and test configs scrubbed before publishing.

## License

MIT
