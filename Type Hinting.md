# Type Hinting
#python 

---

*See also: Python PEP 484*

```Python
def headline(text: str, is_aligned: bool = True) -> str:
	if is_aligned:
		return f"{text.title()}\n{'-' * len(text)}"
	else:
		return f"{text.title()}".center(50, "o")
```

```Python
>>> 
```