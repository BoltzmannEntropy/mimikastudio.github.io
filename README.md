# MimikaStudio Website (Agentic MCP Support)

License: Source code is licensed under Business Source License 1.1 (BSL-1.1), and binary distributions are licensed under the Mimika Binary Distribution License. See [LICENSE](LICENSE), [BINARY-LICENSE.txt](BINARY-LICENSE.txt), and the [website License page](license.html).

## Mimika MCP Quickstart

MimikaStudio ships with a local MCP server (`http://127.0.0.1:8010`) that exposes audiobook, TTS, and voice-management tools.

## Shipped Voices And Language Demos

MimikaStudio ships with 8 custom-designed reference voices for Qwen3 voice cloning:
`Alistair`, `Anastasia`, `Beatrice`, `Eleanor`, `Harriet`, `Mikhail`, `Svetlana`, and `Yelena`.

The website now includes a Qwen3 supported-language showcase with Genesis 1:1 demos for every clone language:
English, Chinese, Japanese, Korean, German, French, Russian, Portuguese, Spanish, and Italian.
Each demo names the voice used and includes the transcript directly in the page.

Example JSON-RPC flow used by MCP clients:

```bash
# Start audiobook generation from a local file
curl -s http://127.0.0.1:8010 \
  -H 'Content-Type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"audiobook_generate_from_file","arguments":{"file_path":"/absolute/path/to/document.pdf","title":"Exam Notes","voice":"bf_emma","output_format":"mp3"}}}'

# Poll job status
curl -s http://127.0.0.1:8010 \
  -H 'Content-Type: application/json' \
  -d '{"jsonrpc":"2.0","id":2,"method":"tools/call","params":{"name":"audiobook_status","arguments":{"job_id":"<JOB_ID>"}}}'
```

When complete, the local file is available under `backend/outputs/` and served by the backend (default `http://localhost:7693/audio/...`).

### Codex Example Prompt

```text
Use Mimika MCP tool audiobook_generate_from_file with:
file_path=/absolute/path/to/document.pdf
voice=bf_emma
output_format=mp3
Then poll audiobook_status until completed and return job_id + audio_url.
```

### Claude Code Example Prompt

```text
Call Mimika MCP audiobook_generate_from_file for /absolute/path/to/document.pdf
with voice bf_emma and output_format mp3.
Track audiobook_status every 10 seconds and return the final audio_url.
```

## Stars

[![GitHub Stars](https://img.shields.io/github/stars/BoltzmannEntropy/mimikastudio.github.io?style=social)](https://github.com/BoltzmannEntropy/mimikastudio.github.io/stargazers)

[![Star History Chart](https://api.star-history.com/svg?repos=BoltzmannEntropy/mimikastudio.github.io&type=Date)](https://star-history.com/#BoltzmannEntropy/mimikastudio.github.io&Date)
