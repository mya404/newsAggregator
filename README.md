# newsAggregator

A small, extensible Python-based news aggregator that fetches articles from RSS/Atom feeds, deduplicates and normalizes items, and provides simple CLI and export options.

**Status:** Draft — basic runner in `main.py` with room for plugins and exporters.

**Highlights**
- Fetches multiple feeds concurrently
- Normalizes feed items (title, link, published date)
- Pluggable exporters (JSON, SQLite, etc.)

## Features

- Multi-feed polling
- Deduplication by URL and content hash
- Optional persistence (file or database)
- Simple CLI for running and one-shot fetching

## Tech

- Python 3.11+
- Suggested libs: `feedparser`, `aiohttp`, `requests`, `sqlite3` (stdlib)

## Requirements

- Python 3.11 or newer
- A working internet connection to fetch feeds

## Installation

Recommended: create a virtual environment.

Using pip with an editable install (if you later add dependencies to `pyproject.toml`):

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e .
```

If you use Poetry (project contains `pyproject.toml`):

```bash
poetry install
poetry run python main.py
```

If you prefer a minimal one-off install, ensure required packages are installed, for example:

```bash
pip install feedparser aiohttp
python main.py
```

## Usage

Basic run (defaults):

```bash
python main.py
```

If your runner accepts a config file (recommended), create `config.yaml` with feed list and options. Example config:

```yaml
feeds:
	- https://example.com/rss
	- https://another.site/feed
poll_interval: 3600  # seconds
output: data/articles.json
```

Then run:

```bash
python main.py --config config.yaml
```

Notes:
- `main.py` is the CLI entrypoint. If you have added flags, run `python main.py --help` for available options.
- Exporters can write JSON, CSV, or persist to SQLite depending on configuration.

## Configuration

- Provide a YAML or JSON config with feed URLs and exporter settings.
- Keep credentials (if any) out of the repo; use environment variables for secrets.

## Development

- To run tests (if added): `pytest`
- Linting: `ruff .` or `flake8`
- Formatting: `black .`

Suggested workflow for contributors:

1. Fork the repo
2. Create a feature branch
3. Add tests for new behavior
4. Open a PR with a clear description

## Contributing

Contributions are welcome. Please open issues for feature requests or bugs. For code changes, follow the development workflow above and keep changes focused.

## Roadmap / Ideas

- Add OAuth-authenticated feed support
- Add a web UI for reading and filtering
- Add tagging and per-feed scheduling
- Add Docker image for easy deployment

## License

This project is released under the MIT License. Replace with your preferred license if needed.

## Contact

Open an issue or reach out to the maintainer listed in the repository metadata.
