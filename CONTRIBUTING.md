# Contributing to CLI-Anything

Thank you for your interest in contributing to CLI-Anything! This guide will help you get started.

## Types of Contributions

We welcome three main categories of contributions:

### A) CLIs for New Software

Adding a new CLI harness is the most impactful contribution. Before submitting a PR, ensure the following are in place:

1. **`<SOFTWARE>.md`** — the SOP document exists at `<software>/agent-harness/<SOFTWARE>.md` describing the harness architecture.
2. **`SKILL.md`** — the AI-discoverable skill definition exists inside the Python package at `cli_anything/<software>/SKILL.md`.
3. **Tests** — unit tests (`test_core.py`, passable without backend) and E2E tests (`test_full_e2e.py`) are present and passing.
4. **`README.md`** — the project README includes the new software with a link to its harness directory.
5. **`repl_skin.py`** — an unmodified copy from the plugin exists in `utils/`.

### B) New Features

Feature contributions improve existing harnesses or the plugin framework. Examples include new CLI commands, output formats, backend improvements, or cross-platform fixes.

- Open an issue first to discuss the feature before starting work.
- Follow existing code patterns and conventions in the target harness.
- Include tests for any new functionality.

### C) Bug Fixes

Bug fixes resolve incorrect behavior in existing harnesses or the plugin.

- Reference the related issue in your PR (e.g., `Fixes #123`).
- Include a test that reproduces the bug and verifies the fix.
- Ensure all existing tests for the affected harness still pass.

## Development Setup

Each generated CLI lives in `<software>/agent-harness/` and is an independent Python package:

```bash
# Clone the repo
git clone https://github.com/HKUDS/CLI-Anything.git
cd CLI-Anything

# Install a harness in editable mode
cd <software>/agent-harness
pip install -e .

# Run tests
python3 -m pytest cli_anything/<software>/tests/ -v
```

### Requirements

- Python 3.10+
- Click 8.0+
- pytest 7.0+

## Code Style

- Follow PEP 8 conventions.
- Use type hints where practical.
- All CLI commands must support the `--json` flag for machine-readable output.

## Commit Messages

Use clear, descriptive commit messages following the conventional format:

```
feat: add Krita CLI harness
fix: resolve Blender backend path on macOS
docs: update README with new software entry
test: add unit tests for Inkscape layer commands
```

## Running Tests

```bash
# Unit tests (no backend software needed)
python3 -m pytest cli_anything/<software>/tests/test_core.py -v

# E2E tests (requires real backend installed)
python3 -m pytest cli_anything/<software>/tests/test_full_e2e.py -v

# All tests for a harness
python3 -m pytest cli_anything/<software>/tests/ -v
```

## Submitting a Pull Request

1. Fork the repository and create a feature branch from `main`.
2. Make your changes following the guidelines above.
3. Ensure all tests pass for any harnesses you modified.
4. Push your branch and open a Pull Request against `main`.
5. Fill out the PR template completely.

## Questions?

If you have questions, feel free to open a [Discussion](https://github.com/HKUDS/CLI-Anything/discussions) or an issue tagged with `type: question`.
