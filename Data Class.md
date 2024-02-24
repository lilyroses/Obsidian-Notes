# Data Class
#python 

---

Python data classes provide several built in methods for classes, while requiring much less boilerplate for the developer.

Data class built-in methods include:

- `__init__()` (class instantiation)
- `__repr__()` (print a string representation)
- `__eq__()` (compare objects)

---

*A Python data class is sparse and to the point, while still containing `__init__()`, `__repr__()`, and `__eq__()` built-in methods.*

```Python
# Card dataclass
from dataclasses import dataclass

@dataclass
class Card:
	rank: str
	suit: str
```

*Using the Card data class*

```Python
>>> import Card
>>> ace_of_spades = Card('A', 'Spades')  # The __init__() method
```

```Python
>>> ace_of_spades.rank
'A'
```

*String representation*
```Python
>>> ace_of_spades
Card(rank='A', suit='Spades')  # The __repr__() method
```

*Comparison*
```Python
>>> ace_of_spades == Card('A', 'Spades')  # The __eq__() method
True
```

---

*A regular Python class is much more verbose.*

```Python
# Card regular class

class Card:
	def __init__(self, rank, suit):
		self.rank = rank
		self.suit = suit
```

```Python
>>> import Card
>>> ace_of_spades = Card('A', 'Spades')
```

*No built-in string representation*
```Python
>>> ace_of_spades
<__main__.RegularCard object at 0x7fb6eee35d30>
```

*No built-in comparison methods*
```Python
>>> ace_of_spades == Card('A', 'Spades')
False
```

To make a regular class with the same functionality as a data class, you need to add the following methods:

- `__init__()`
- `__repr__()`
- `__eq__()`

```Python
class Card:
	def __init__(self, rank, suit):
		self.rank = rank
		self.suit = suit

	def __repr__(self):
		return (f"{self.__class__.__name__}"
			    f"(rank={self.rank!r}, suit={self.suit!r})")

	def __eq__(self):
		if other.__class__ is not self.__class__:
			return NotImplemented
		return (self.rank, self.suit) == (other.rank, other.suit)
```