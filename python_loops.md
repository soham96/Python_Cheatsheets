# This file contains some tips and tricks for making looping in python faster and easier

## Types of loops

* `for` Loop:

    
    ```python
    for i in range(5):
        print(i)
    ```
* `while` Loop:
    ```python
    counter=0
    while i<5:
        counter=counter+1
        print(counter)
    ```

## `for` Loop Tips and Tricks

### Basics of Looping:
The `for` loop is used to loop over the items in an object and unlike loops in Java or C/C++, they do not have an iterator or even need iterators.

```python
countries=['India', 'France', 'Germany', 'Brazil', 'Spain']

#Instead of doing
for i in range(len(countries)):
    print(countries[i])

#Just do this!
for country in countries:
    print(countries)
```

*Note:* `range` used to previously generate the whole list. This made it memory inefficient. `xrange` can create the values to be iterated one at a time. However, in python3 `xrange` was replaced with `range`.

### To get the indices
If you want access to both the objects in the collection and its indices then use `enumerate`

```python
for i, country in enumerate(countries):
    print(f"The {i}th country is {country}")
```

### Looping Backwards
You could loop backwards like this:
```python
for i in range(len(countries)-1, -1, -1):
    print countries[i]
```
Or, you can make it more readable and easier by doing this:
```python
for country in reversed(countries):
    print(country)
```

### Multiple Collections
To loop over multiple lists use `zip`
```python
cities=['Delhi', 'Paris', 'Berlin', 'Brasilia', 'Madrid']

for city, country in zip(cities, countries):
    print(f"Capital of {country} is {city}")
```

*Note:* `zip` creates a new list and stores it in memory along with the original lists. `izip` is more memory efficient. `izip` replaced `zip` in python3.

### Looping in custom order
To loop over a collection in a sorted manner:
```python
for country in sorted(countries):
    print(country)

#To lopp in the reverse manner:
for country in sorted(countries, reverse=True):
    print(country)
```

To loop over in any other manner like lengthwise:
```python
for country in sorted(countries, key=len):
    print(country)

#To sort based on lower case letters
for country in sorted(countries, key=str.lower):
    print(country)
```

### Exiting from a `for` loop
Instead of using flag variables and break statements, we can use the `else` clause of the python `for` loop:

```python
for i, value in enumerate(countries):
        if value == 'Spain':
            break
    else:
        print("Not Found)
    print(i)
```

The `else` part of the `for` loop is run only when the `for` loop does not encounter a `break` statement. So, in the above example, since "Spain" exists in the `countries` list, the `break` statement will be encountered and the position will be printed out. If "Spain" were not found, then the `for` loop will not encounter the `break` and run the `else` clause and print "Not Found" 

###Exiting without using `if` statements
Using sentinel values we can call an iterable until a certain value is reached
```python
blocks = []
for block in iter(partial(f.read, 32), sentinel=''):
    blocks.append(block)
```
`iter` creates an iterable of its first argument and it calls it until the senitnel value(second parameter) is reached

## References
* Raymond Hettinger's Awesome talk: "Transforming Code into Beautiful, Idiomatic Python" at <https://www.youtube.com/watch?v=OSGv2VnC0go>