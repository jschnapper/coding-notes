# Python Basics

**What are Python types and their shortened Python name**
* Integer : int
* Floating point : float
* Strings : str
* Lists : list
* Dictionaries : dict
* Tuples : tup
  * Ordered, immutable sequence of heterogenous objects (Wrapped with parenthesis)
* Sets : set
  * Unordered collection of unique objects 
* Booleans : bool
  * True or False (capitalized)


**How is slicing represented?**
`[start:stop:step]`
Step defaults to `1`

**How would you get the length of a string?**
`len()`

**Properties of Strings**

*Strings are immutable*
```python
# BAD
name = "Pot"
name[0] = "N" # ERROR, TypeError, `str` does not support item assignment`

# GOOD
name = "Pot"
last_letters = name[1:]
new_name = "D" + last_letters # output: Dot
```

*String multiplication*
```python
letter = 'e'
letter * 4 # output: 'eeee'
```

*Common methods*
* `.split()` splits the string into a list. Defaults to splitting by whitespace if no argument given, removing from the list what it is splitting on

**String Formatting for Printing**
* Two kinds of methods
  * `.format()`
  * `f-strings` (formatted string literals)

**String Format Method**
Put `{}` in place of insertions and call `.format()` with arguments of what to replace the braces with
`'String here {} then als {}'.format('something1', 'something2')`

Can also adjust by index
```python
"The {} {} {}".format("fox", "brown","quick")
# "The fox brown quick"

"The {2} {1} {0}".format("fox", "brown", "quick")
# "The quick brown fox"

"The {0} {0} {0}".format("fox", "brown", "quick")
# "The fox fox fox"

"The {q} {b} {f}".format(f="fox", b="brown", q="quick")
# "The quick brown fox"
```

**Float Format Method**
`{value:width.precision f}` (I believe `f` is for float)
`width`: amount of whitespace, space for number to take up 
`precision`: decimal accuracy

```python
result = 104.12345
"result is {r:10.2f}".format(r=result)
# result is      104.12 
```

**f-string format**
```python
name = "bob"
f"hello, my name is {name}"
# "hello, my name is bob"
```

**Even older formatting method**
`%s` for string
`%d` for int

```python
"%s %s" % ("pot", "dot")
# "pot dot"

"hello %s" % "world"
# "hello world"

"%d %d" % (1, 2)
# 1 2


```