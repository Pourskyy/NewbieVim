# Python modelling model
> Initializing the project  

```
my_project/  
│  
├── src/  
│   └── my_project/  
│       ├── __init__.py  
│       └── main.py  
├── tests/  
│   └── test_main.py  
├── pyproject.toml  
├── .pre-commit-config.yaml  
├── README.md  
└── .gitignore  
```
  
To start the project:  
```bash
mkdir my_project
cd my_project
mkdir src
mkdir src/my_project
touch src/my_project/__init__.py
touch src/my_project/main.py
mkdir tests
touch tests/test_main.py
touch pyproject.toml
touch .pre-commit-config.yaml
touch README.md
touch .gitignore
```
  
Then you need your `Local Environment`  
```bash
python3 -m venv .venv
source .venv/bin/activate
```
  
> Inside `pyproject.toml`  
> Defines project name/version/dependencies  
> Configure `black`, `isort`, `flake8`, `mypy` settings directly  
> Ensures consistent formatting, linting, type checking  
```toml
[build-system]
requires = ["setuptools>=42", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "my_project"
version = "0.1.0"
description = "A cool modeling project."
authors = [
  { name="Your Name", email="your@email.com" }
]
dependencies = [
  "pandas>=2.0",
  "numpy>=1.22",
  "scikit-learn>=1.3",
  "matplotlib",
  "seaborn"
]

[tool.black]
line-length = 88

[tool.isort]
profile = "black"

[tool.flake8]
max-line-length = 88
extend-ignore = "E203"

[tool.mypy]
python_version = "3.10"
strict = true
```
  
> Inside `.pre-commit-config.yaml`  
> Format code with `black`  
> Lint code with `flake8`  
> Type check code with `mypy`  
> Fix small issues like missing end-of-file newline  
```yaml
repos:
  - repo: https://github.com/psf/black
    rev: 23.3.0
    hooks:
      - id: black

  - repo: https://github.com/pre-commit/mirrors-flake8
    rev: v6.0.0
    hooks:
      - id: flake8

  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v0.991
    hooks:
      - id: mypy

  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: check-added-large-files
      - id: end-of-file-fixer
      - id: trailing-whitespace
```
  
Install All Required Tools
```bash
pip install black isort flake8 mypy pre-commit
pip install pandas numpy scikit-learn matplotlib seaborn
```
  
Now activate the hooks  
```bash
pre-commit install
```
> [!NOTE]
> Now every time you git commit, these checks will run automatically  
> If code isn’t formatted properly or type hints are wrong, the commit will fail until you fix it  
  
> You can manually run checks too  
```bash
pre-commit run --all-files
```
  
*EXPLANATION*  
`.venv/` &rarr; &rarr; &rarr; &rarr; &rarr; A local Python Environment (isolated from system)  
`pyproject.toml` &rarr; &rarr; &rarr; &rarr; Defines dependencies and configures code styles tools  
`.pre-commit-config.yaml` &rarr; &rarr; &rarr; Defines automated checks that trigger before each commit  
`pre-commit` &rarr; &rarr; &rarr; &rarr; &rarr; The tool that runs hooks automatically before each commit  
`black`, `flake8`, `mypy`, `isort` &rarr; Tools to format, lint, type-check and sort imports  
