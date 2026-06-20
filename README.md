# Python Project Template

[![Code Quality](https://github.com/JacobPEvans/python-template/actions/workflows/ci.yml/badge.svg)](https://github.com/JacobPEvans/python-template/actions/workflows/ci.yml)
[![Python Tests](https://github.com/JacobPEvans/python-template/actions/workflows/tests.yml/badge.svg)](https://github.com/JacobPEvans/python-template/actions/workflows/tests.yml)
[![Code Coverage](https://codecov.io/github/JacobPEvans/python-template/graph/badge.svg?token=IFMKOLPQE9)](https://codecov.io/github/JacobPEvans/python-template)

A minimal Python project template following modern best practices and industry
standards. Use it as the starting point for a new Python package: clone it,
rename the `hello_world` package, and replace the example code with your own.

**License:** [Apache License 2.0](LICENSE)
**Python Version:** 3.11+

## Features

- Modern Python packaging with `pyproject.toml`
- Automated testing with pytest and coverage
- Dual GitHub Actions workflows (testing + code quality)
- Pre-commit hooks for code quality enforcement
- Type hints and mypy type checking
- Code formatting and linting with Ruff
- Pre-configured `.gitignore`
- Enforced 100% code coverage

## Installation

### Prerequisites

- Python 3.11 or higher
- Git

### Steps

1. **Clone this repository**

   ```bash
   git clone <repository-url>
   cd python-template
   ```

2. **Create and activate a virtual environment**

   ```bash
   # Windows
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1

   # Linux/macOS
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   > **Note**: We use `.venv` as the directory name to match common conventions
   > and ensure it's ignored by git.

3. **Install dependencies**

   ```bash
   # Development installation (includes dev dependencies)
   pip install -e ".[dev]"

   # Or just production dependencies
   pip install -e .
   ```

   > **Note**: The `-e` flag installs in "editable" mode, so changes to your code
   > take effect immediately.

4. **Set up pre-commit hooks (required for contributing)**

   ```bash
   # Pre-commit is already installed with dev dependencies.
   # Install the git hook scripts:
   pre-commit install

   # (Optional) Run on all files to test the setup
   pre-commit run --all-files
   ```

   > **Note**: Pre-commit hooks run automatically on every commit and may
   > auto-fix formatting issues.

## Usage

Run the hello world application:

```bash
python -m hello_world.main
```

Or import and use it in your code:

```python
from hello_world import greet

print(greet("Python"))  # Output: Hello, Python!
```

## Project Structure

```text
python-template/
├── .github/
│   └── workflows/
│       ├── tests.yml          # GitHub Actions - Testing
│       └── ci.yml             # GitHub Actions - Code Quality
├── src/
│   └── hello_world/
│       ├── __init__.py        # Package initialization
│       └── main.py            # Main application code
├── tests/
│   ├── __init__.py            # Test package initialization
│   └── test_main.py           # Unit tests
├── .gitignore                 # Git ignore rules
├── .pre-commit-config.yaml    # Pre-commit hooks configuration
├── README.md                  # Project documentation
├── pyproject.toml             # Modern Python packaging & tool config
├── pytest.ini                 # Pytest configuration
└── requirements-dev.txt       # Development dependencies
```

## Development

### Running Tests

```bash
# Run all tests
pytest

# Run tests in verbose mode
pytest -v

# Run a specific test file
pytest tests/test_main.py -v
```

### Coverage

This project enforces **100% code coverage**. Pull requests that drop below
100% are rejected automatically by GitHub Actions. Verify locally before
committing:

```bash
# Same invocation as CI / CodeCov — fails under 100%
pytest --cov --cov-branch --cov-report=xml --cov-fail-under=100

# Generate a browsable HTML coverage report
pytest --cov=src/hello_world --cov-report=html
```

### Code Quality

Two GitHub Actions workflows guard quality, mirrored locally by pre-commit:

- **`tests.yml`** — runs pytest with coverage across Python 3.11–3.13.
- **`ci.yml`** — enforces formatting, linting, and type checking with
  auto-fixing and validation.

Pre-commit runs the same formatting and linting (Ruff) and type
checking (mypy) on every `git commit`. If a check fails, the commit is blocked
until the issue is fixed; formatters auto-fix many issues for you.

```bash
pre-commit install        # one-time setup
pre-commit run --all-files
```

## Contributing

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/amazing-feature`).
3. Run tests with coverage before committing (see [Coverage](#coverage)).
4. Commit your changes (`git commit -m 'Add some amazing feature'`).
5. Push to the branch (`git push origin feature/amazing-feature`).
6. Open a Pull Request.

---

> Part of a [larger ecosystem of ~40 repos](https://docs.jacobpevans.com) —
> see how it all fits together.
