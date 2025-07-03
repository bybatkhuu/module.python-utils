# potato_utils

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/bybatkhuu/module.python-utils/2.build-publish.yml?logo=GitHub)](https://github.com/bybatkhuu/module.python-utils/actions/workflows/2.build-publish.yml)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/bybatkhuu/module.python-utils?logo=GitHub&color=blue)](https://github.com/bybatkhuu/module.python-utils/releases)

This is a short description of the project.

## ✨ Features

- Python module/package
- Configuration
- Test
- Build
- Documentation
- Scripts
- Examples
- CI/CD

---

## 🛠 Installation

### 1. 🚧 Prerequisites

- Install **Python (>= v3.10)** and **pip (>= 23)**:
    - **[RECOMMENDED] [Miniconda (v3)](https://www.anaconda.com/docs/getting-started/miniconda/install)**
    - *[arm64/aarch64] [Miniforge (v3)](https://github.com/conda-forge/miniforge)*
    - *[Python virutal environment] [venv](https://docs.python.org/3/library/venv.html)*

[OPTIONAL] For **DEVELOPMENT** environment:

- Install [**git**](https://git-scm.com/downloads)
- Setup an [**SSH key**](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) ([video tutorial](https://www.youtube.com/watch?v=snCP3c7wXw0))

### 2. 📥 Download or clone the repository

[TIP] Skip this step, if you're going to install the package directly from **PyPi** or **GitHub** repository.

**2.1.** Prepare projects directory (if not exists):

```sh
# Create projects directory:
mkdir -pv ~/workspaces/projects

# Enter into projects directory:
cd ~/workspaces/projects
```

**2.2.** Follow one of the below options **[A]**, **[B]** or **[C]**:

**OPTION A.** Clone the repository:

```sh
git clone https://github.com/bybatkhuu/module.python-utils.git && \
    cd module.python-utils
```

**OPTION B.** Clone the repository (for **DEVELOPMENT**: git + ssh key):

```sh
git clone git@github.com:bybatkhuu/module.python-utils.git && \
    cd module.python-utils
```

**OPTION C.** Download source code:

1. Download archived **zip** file from [**releases**](https://github.com/bybatkhuu/module.python-utils/releases).
2. Extract it into the projects directory.

### 3. 📦 Install the package

[NOTE] Choose one of the following methods to install the package **[A ~ F]**:

**OPTION A.** [**RECOMMENDED**] Install from **PyPi**:

```sh
# Install from staging TestPyPi:
pip install -i https://test.pypi.org/simple -U potato_utils

# Or install from production PyPi:
# pip install -U potato_utils
```

**OPTION B.** Install latest version directly from **GitHub** repository:

```sh
pip install git+https://github.com/bybatkhuu/module.python-utils.git
```

**OPTION C.** Install from the downloaded **source code**:

```sh
# Install directly from the source code:
pip install .

# Or install with editable mode:
pip install -e .
```

**OPTION D.** Install for **DEVELOPMENT** environment:

```sh
pip install -r ./requirements/requirements.dev.txt
```

**OPTION E.** Install from **pre-built release** files:

1. Download **`.whl`** or **`.tar.gz`** file from [**releases**](https://github.com/bybatkhuu/module.python-utils/releases)
2. Install with pip:

```sh
# Install from .whl file:
pip install ./potato_utils-[VERSION]-py3-none-any.whl

# Or install from .tar.gz file:
pip install ./potato_utils-[VERSION].tar.gz
```

**OPTION F.** Copy the **module** into the project directory (for **testing**):

```sh
# Install python dependencies:
pip install -r ./requirements.txt

# Copy the module source code into the project:
cp -r ./src/potato_utils [PROJECT_DIR]
# For example:
cp -r ./src/potato_utils /some/path/project/
```

## 🚸 Usage/Examples

### Simple

[**`examples/simple/main.py`**](https://github.com/bybatkhuu/module.python-utils/blob/main/examples/simple/main.py):

```python
## Standard libraries
import sys
import logging

## Internal modules
from potato_utils import MyClass


logger = logging.getLogger(__name__)


def main() -> None:
    logging.basicConfig(
        stream=sys.stdout,
        level=logging.INFO,
        datefmt="%Y-%m-%d %H:%M:%S %z",
        format="[%(asctime)s | %(levelname)s | %(filename)s:%(lineno)d]: %(message)s",
    )

    # Pre-defined variables (for customizing and testing)
    _items = [0.1, 0.2, 0.3, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
    _config = {
        "min_length": 4,
        "max_length": 10,
        "min_value": 0.0,
        "max_value": 1.0,
        "threshold": 0.7,
    }

    # Main example code
    logger.info(f"Items before cleaning: {_items}")
    _my_object = MyClass(items=_items, config=_config)
    _items = _my_object()
    logger.info(f"Items after cleaning: {_items}")

    logger.info("Done!\n")
    return


if __name__ == "__main__":
    main()
```

👍

---

## ⚙️ Configuration

[**`templates/configs/config.yml`**](https://github.com/bybatkhuu/module.python-utils/blob/main/templates/configs/config.yml):

```yaml
potato_utils:
  min_length: 2
  max_length: 100
  min_value: 0.0
  max_value: 1.0
  threshold: 0.5
```

### 🌎 Environment Variables

[**`.env.example`**](https://github.com/bybatkhuu/module.python-utils/blob/main/.env.example):

```sh
# ENV=development
# DEBUG=true
```

---

## 🧪 Running Tests

To run tests, run the following command:

```sh
# Install python test dependencies:
pip install -r ./requirements/requirements.test.txt

# Run tests:
python -m pytest -sv -o log_cli=true
# Or use the test script:
./scripts/test.sh -l -v -c
```

## 🏗️ Build Package

To build the python package, run the following command:

```sh
# Install python build dependencies:
pip install -r ./requirements/requirements.build.txt

# Build python package:
python -m build
# Or use the build script:
./scripts/build.sh
```

## 📝 Generate Docs

To build the documentation, run the following command:

```sh
# Install python documentation dependencies:
pip install -r ./requirements/requirements.docs.txt

# Serve documentation locally (for development):
mkdocs serve
# Or use the docs script:
./scripts/docs.sh

# Or build documentation:
mkdocs build
# Or use the docs script:
./scripts/docs.sh -b
```

## 📚 Documentation

- [Docs](https://github.com/bybatkhuu/module.python-utils/blob/main/docs)
- [Home](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/README.md)

### Getting Started

- [Prerequisites](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/getting-started/prerequisites.md)
- [Installation](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/getting-started/installation.md)
- [Configuration](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/getting-started/configuration.md)
- [Examples](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/getting-started/examples.md)
- [Error Codes](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/getting-started/error-codes.md)

### [API Documentation](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/api-docs/README.md)

### Development

- [Test](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/test.md)
- [Build](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/build.md)
- [Docs](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/docs.md)
- [Scripts](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/scripts/README.md)
- [CI/CD](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/cicd/README.md)
- [File Structure](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/file-structure.md)
- [Sitemap](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/sitemap.md)
- [Contributing](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/contributing.md)
- [Roadmap](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/dev/roadmap.md)

### [Release Notes](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/release-notes.md)

### [Blog](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/blog/index.md)

### About

- [FAQ](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/about/faq.md)
- [Authors](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/about/authors.md)
- [Contact](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/about/contact.md)
- [License](https://github.com/bybatkhuu/module.python-utils/blob/main/docs/pages/about/license.md)

---

## 📑 References

- <https://packaging.python.org/en/latest/tutorials/packaging-projects>
- <https://python-packaging.readthedocs.io/en/latest>
