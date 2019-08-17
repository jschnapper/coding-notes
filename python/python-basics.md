# Python Basics

**What are Python types and their shortened Python name**
* Integer : int
* Floating point : float
* Strings : str
* Lists : list
  * Can store mixed object types
  * ordered sequence of elements
* Dictionaries : dict
  * unordered
  * can't be sorted
* Tuples : tup
  * Ordered, immutable sequence of heterogenous objects (Wrapped with parenthesis)
* Sets : set
  * Unordered collection of unique objects 
* Booleans : bool
  * True or False (capitalized)
* NoneType
  * A none object
  * Common return value for functions that don't return anything
  * Can instantiate variables this way
    * `a = None`


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

**Lists**

* In place sort with `.sort()` (doesn't return new list but sorts original list)
* `.reverse()` is also in-place
* `.pop()` returns the item at the end of the list and mutates the original list
  * `.pop()` defaults to last item (i.e. `.pop(-1)`) but you can pop any index

**Dictionaries**

* Wrap key in quotes if a string, but can also have key as an int
* Unordered, can't be sorted 
* `d.keys()` returns the list of keys
* `d.values()` returns the list of values
* `d.items()` returns each pair wrapped in parenthesis (as a list of tuples)

**Tuples**
* Count the number of times a value occurs: `.count()`, example: `('a', 'a', 'b').count('a') # returns 2`
* `.index()` returns first index of item passed in occurs
* Immutable and ordered
* Only two methods `index` and `count`
  * Can concatenate by adding tuples together
```Python
tuple = (1,2)
new_tuple = (1,2) + (3,) # make sure to include the comma
# new tuple (1,2,3)
```

**Sets**
* represented with brackets like dictionary, but no key-value pairing
* unordered and unique
* Add to set with `.add()` and it will only add if its unique
* If converting a list to a set, it will remove repeated elements
* Create or convert something to a set with `set()`
* Can convert strings to a set


### Input/Output
* Open a files with `open(path/to/file)`
* `.read()` outputs file as a single string (with `\n` representing new lines)
  * A read occurs one at a time, it's a cursor scanning the file and ending at the end
  * So if you attempt to read again, it won't output anything because cursor is at the end of the file
  * Use `.seek(0)` to reset cursor at the beginning before reading again
* `.readLines()` will separate each line of the file into its own element of a list (the `\n` still persists though)
* When open file, make sure to close it with `.close()` on the file saved as a variable (i.e. `myFile = open(path_to_file.txt)` then `myFile.close()`)

Another way to open and close:
```Python
with open("file.txt") as my_file:
  contents = my_file.read()

contents
# will print out contents as a single string
# Don't need to manually close the file
```
`open` defaults to `mode='r'`. To write to the file, need to say `open("file.txt", mode='w')`
* `w` overwrites files (or create new file if passed in file doesn't exist)
* `a` appends more lines to the end of a file
* `r+` is reading and writing
* `w+` is writing and reading (overwrites existing files or creates a new file)
