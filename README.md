# template-python-poetry

## Steps

```sh
rye pin 3.11
rye init
```

## Edit `pyproject.toml` as needed.

### hatching

Default. No need to edit.

### setuptools

<https://setuptools.pypa.io/en/latest/userguide/package_discovery.html>

```toml
[build-system]
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"
```

```toml
[tool.setuptools]
packages = ["<your_package_name>"]
```

```toml
[tool.setuptools.package-dir]
"" = "src"
```

sample 1

```toml
[build-system]
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"

[tool.setuptools]
packages = ["hoge"]

[tool.setuptools.package-dir]
"" = "src"
```

sample 2

```toml
[build-system]
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"

[tool.setuptools]
packages = ["ansiblelint.rules.custom.ansible_lint_custom_strict_naming"]

[tool.setuptools.package-dir]
"ansiblelint.rules.custom.ansible_lint_custom_strict_naming" = "src/rules"
```

### Linter and Formatter

```toml
[tool.black]
line-length = 120

[tool.isort]
profile = "black"
line_length = 120
force_single_line = true
import_heading_stdlib = "Standard Library"
import_heading_thirdparty = "Third Party Library"
import_heading_firstparty = "First Party Library"
import_heading_localfolder = "Local Library"

[tool.mypy]
python_version = "3.11"
strict = true

# disallow_any_expr = true
disallow_any_decorated = true
disallow_any_explicit = true
disallow_any_unimported = true
warn_incomplete_stub = true
warn_unreachable = true

show_error_codes = true
enable_error_code = "ignore-without-code"


[tool.pytest.ini_options]
minversion = "6.0"
addopts = [
    "-rxX",
    "--capture=no",
    "-pno:logging",
    # "--cov",
    # "--cov-append",
    # "--cov-report=term-missing",
]
testpaths = "test"
python_files = ["tests.py", "test_*.py", "*_tests.py"]
```

## Add developer tools

```sh
rye add --dev \
    black \
    flake8 \
    autoflake8 \
    isort \
    mypy \
    nox \
    pytest
```

## Check your python version and update some config

- `noxfile.py`
  - directory
  - python version
  - `PYTHONPATH`
- `pyproject.toml`
  - mypy's `python_version`

If you use this github template, update `README.md` .
