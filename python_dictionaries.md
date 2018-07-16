# This file contains some tips and tricks for using Dictionaries easier
Python dictionaries are one of the easiest ways to express relationships in python.

## What is a Dictionary?
A dictionary ocntains a key-value pair. For every key in a dictionary, there is a value.
Anything within a `{}` is a dictionary and the keys and values are seperated using `:`. Each key-value pair in the dictionary is seperated by a `,`.

### Creating a Dictionary
```python
d={'India':'Delhi', 'France':'Paris', 'Germany':'Berlin', 'Brazil':'Brasilia', 'Spain':'Madrid'}
```
If you have two lists and you want to create a dictionary out of them, then use `zip` (refer to `python_loops.md`)
```python
countries=['India', 'France', 'Germany', 'Brazil', 'Spain']
cities=['Delhi', 'Paris', 'Berlin', 'Brasilia', 'Madrid']
d=dict(zip(countries, cities))
```
This means that you can also use `enumerate` to make a dict out of position of the list:
```python
d=dict(enumerate(countries))
```

### Iterating through a Dictionary
To get the keys of a Dictionary:
```python
for k in d:
    print(k)
```

**Note**: Do **NOT** change the Dictionary values when Iterating through like this. The better way to do that is:
```python
for k in d.keys():
    if len(k)>5:
        del d[k]
```

`d.keys()` creates a copy of the keys making it safe to mutate the original dictionary. The above snippet also shows how to delete a key value pair from the dictionary.

The above methods only return the key. To get the values, do this:
```python
for k, v in d.items():
    print(f"Country {k} has capital {v}")

#Do Not Do this
for k in d:
    print(f"Country {k} has capital {d[k]}")
```

The second method will have to rehash the keys every time, thus making it slow.  
`items` returns the whole list meaning it uses ore memory. `iteritems` returns an iterator to the items, so it occupies less space.

```python
for k, v in d.iteritems():
    print(f"Country {k} has capital {v}")
```

### Counting with Dictionaries
```python
#The Easiest way to count


```