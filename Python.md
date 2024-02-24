# Python

---

## About

- **[[Strong vs. Weak Programming Languages#Strongly Typed|Strongly]]** typed
- [[Dynamically]] typed

---

## Tools

### Typechecking

- [[Type Annotations]]
- [[Type Hinting]]
- [[MyPy]]

### Linters

- Pylint
- flake8
- autopep

---

## Modules

*mod.py*
```Python
# mod.py
s = "It's a beautiful morning."
n = [123, 456, 789]

def foo(arg):
	print(f"arg = {arg}")

class Bar:
	pass
```

Defined in `mod.py`:
- `s` = string
- `a` = list of ints
- `foo` = a function 
- `Bar` = a class

To import the objects in `mod.py` :

```Python
>>> import mod
>>> print(mod.s)
"It's a beautiful morning."
>>> mod.a
[123, 456, 789]
>>>mod.foo([
>>>
>>>])
```

---

## GUI Apps

- [[Tkinter]]
- [[PyInstaller]]
