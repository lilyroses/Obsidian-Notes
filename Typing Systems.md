# Typing Systems
#programming 

---

## Table of Contents

- [[#Strongly vs. Weakly Typed Languages|Strongly vs. Weakly Typed Languages]]
	- [[#Strongly vs. Weakly Typed Languages#Strongly Typed Languages|Strongly Typed Languages]]
	- [[#Strongly vs. Weakly Typed Languages#Weakly Typed Languages|Weakly Typed Languages]]
- [[#Statically vs. Dynamically Typed Languages|Statically vs. Dynamically Typed Languages]]
	- [[#Statically vs. Dynamically Typed Languages#Statically Typed Languages|Statically Typed Languages]]
	- [[#Statically vs. Dynamically Typed Languages#Dynamically Typed Languages|Dynamically Typed Languages]]

---

## Different Typing Systems

- [[Typing Systems#Strongly vs. Weakly Typed Languages|Strong vs. Weak]]
- [[Typing Systems#Statically vs. Dynamically Typed Languages|Static vs. Dynamic]]

---

## Strongly vs. Weakly Typed Languages

### Strongly Typed Languages

A strongly typed language means **data has a type**, and **type matters when performing operations**.

Compiler/error messages are returned when operating on different types.

Examples of strongly typed languages:
- Haskell
- TypeScript
- Rust
- Python

---

*Attempted concatenation of differing types in Python resulting in `TypeError`*

```python
>>> [] + {}
>>> TypeError: can only concatenate list (not "dict") to list
```

```python
>>> {} + []
>>> TypeError: unsupported operand type(s) for +: 'dict' and list
```

---

### Weakly Typed Languages

A weakly typed language **does not restrict the use of operations to supported types** of data.

You can arbitrarily perform operations on objects of different types. The interpreter infers or changes the data type to force compatibility, resulting in unexpected or unintended results.

Examples of weakly typed languages:
- JavaScript
- Perl

---

*Concatenating differing types in JavaScript is allowed, but doesn't make sense.*

```JavaScript
>>> [] + {}
"[object Object]"
```

```JavaScript
>>> {} + []
0
```

---

## Statically vs. Dynamically Typed Languages

---

### Statically Typed Languages

A statically typed language **embeds the typing information inside variables during build time.**

Sometimes developers must explicitly state the variable type (e.g., `int number_of_episodes` for C). Other times, the compiler infers the type. 
Either way, variables cannot change their type at runtime.

Examples of statically typed languages:
- C, C++, C#
- Fortran
- Go
- Haskell
- Java
- Kotlin
- Pascal
- Scala
- Swift

---

*Defining a Java variable's type as String means that variable can only be a String*

```Java
public class HelloTypes {

	public static void main(String[] args) {

		String thing;
		thing = "Hello World";

		// This would result in an error
		// thing = 42;
	
		System.out.println(thing);

	}
}
```

---

### Dynamically Typed Languages

In a dynamically typed language, **types are bound to actual data** (either the value or the variable itself, depending on the language).

Types aren't known until runtime, and can change at runtime as there is no type information locked to the variable.

Dynamic typing can be a [[Typing Systems#Enhancing Python's Robustness as a Dynamically Typed Language|hindrance to robust code]], as assumptions cannot be made about variables.

Examples of dynamically typed languages:
- Erlang
- JavaScript
- Perl
- PHP
- [[Python]]
- Ruby

---

*Python allows variable types to be arbitrarily changed*

```Python
>>> thing = "Hello"
>>> type(thing)
<class 'str'>

>>> thing = 28.1
>>> type(thing)
<class 'float'>
```

---
#### Enhancing Python's Robustness as a Dynamically Typed Language

- [[Type Hinting]]
- Type checking 
	- [[MyPy]]

---

#### Duck Typing

Duck typing is related to dynamic typing. In duck typing, **class and object types are not checked at all.** 

Instead, the methods and attributes defined by classes and objects are verified.

---

*Calling `len()` on a Python object that defines a `.__len__()` method*

```Python
>>> class TheHobbit:
...     def __len__(self):
...         return 95022
...
...
>>> bilbo = TheHobbit()
>>> bilbo
<__main__.TheHobbit object at 0x108deeef0>

>>> len(the_hobbit)
95022
```

*Some Python objects have a built-in `.__len__()` method*

```Python
>>> my_str = "Hello World"
>>> my_list = [12, 34, 56, 78]
>>> my_dict = {"one": 1, "two": 2, "three": 3}

>>> len(my_str)
11
>>> len(my_list)
4
>>> len(my_dict)
3
```

*Other Python objects do not have a `len()` method*

```Python
>>> my_int = 7
>>> my_float = 3.14

>>> len(my_int)
TypeError: object of type 'int' has no len()

>>> len(my_float)
TypeError: object of type 'float' has no len()
```