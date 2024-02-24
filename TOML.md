# TOML
#python


---

## TOML Basics

- **TOML:** Tom's Obvious Minimal Language
	- All keys are strings
	- No null type

- [[Configuration Files]] format (`.toml`)
	- `pyproject.toml` to build packages

- [[Pydantic]]: type annotations to validate data types at runtime

```TOML
# tic_tac_toe.toml

[user]
background_color = "white"

	[user.player_x]
	symbol = "X"
	color = "blue"
	
	[user.player_o]
	symbol = "O"
	color = "green"

[constant]
board_size = 3

[server]
url = "https://tictactoe.example.com"
```

---

### TOML Validation

There is currently no schema validation for TOML files.

Options:
- Typechecker (e.g. [[pydantic]])
-  Taplo (validate TOML against JSON schemas)
	- Get via: *Even Better TOML* VSCode extension

---

## Installation

`tomllib` comes with Python >= 3.11

For `tomli` installation:
```shell
(venv) $ python -m pip install tomli
```

---

### Automate TOML Version

- To read TOML files with Python, use:
	- `tomllib` (newer, comes with Python as of >= 3.11)
	- `tomli`

To use `tomllib` on Python >= 3.11 and `tomli` everywhere else, you need to:

1. Add specification to `requirements.txt`

*requirements.txt*
```python
tomli >= 1.1.0 ; python_version < "3.11"
```

2. Change `tomli` imports

```python
try:
	import tomllib
except ModuleNotFoundError:
	import tomli as tomllib
```

---

## Using TOML Files with Python

### Example

*Example TOML file for tic_tac_toe.py*
```TOML
# tic_tac_toe.toml

[user]
player_x.color = "blue"
player_o.color = "green"

[constant]
board_size = 3

[server]
url = "https://tictactoe.example.com"
```

*config directory structure*
```
config/
|__ __init__.py
|__ tic_tac_toe.toml
```

*__init__.py contents*
```python
# __init__.py

import pathlib
try:
	import tomllib
except ModuleNotFoundError:
	import tomli as tomllib

path = pathlib.Path(__file__).parent / "tic_tac_toe.toml"
with path open(mode="rb") as fp:
	tic_tac_toe = tomllib.load(fp)
```

*Test out the config*
```python
>>> import config
>>> config.path
WindowsPath('C:/Users/lilyr/code/projects/tic_tac_toe/config/tic_tac_toe.toml')
```

*Use the config in another module*
```python
# tic_tac_toe.py

from config import tic_tac_toe as CFG

# Use CFG as a dictionary
```