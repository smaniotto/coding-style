# Coding Style

Look ma, I can code with *style*.

This guide aims to document coding styles for the languages that I use, currently Python. Since I'm mostly using Django, the examples may be from it.

It is open for the community contribution, just make a pull request and lets discuss it.

> Good code is like a good joke: It needs no explanation. Russ Olsen.

## Summary
1. [Python](#python)
1. [References](#references)
1. [License](#license)

## 1. Python
Based on [PEP8](https://www.python.org/dev/peps/pep-0008/) and [Django](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/).

### Python Summary
1. [Python Syntax](#python-syntax)
1. [Python Variables](#python-variables)
1. [Python Documentation](#python-documentation)

### 2.1 Python Syntax
Line width should have a maximum of 79 characters.

When calling a method or class, use named arguments.
```python
# Good
members = get_members(
    first_name='Bob',
    last_name='Dev',
    age=30
)

# Bad
members = get_members('Bob', 'Dev', 30)
```

In a method or class argument list, omit the last comma.
```python
# Good
members = get_members(
    first_name='Bob',
    last_name='Dev',
    age=30
)

# Bad
members = get_members(
    first_name='Bob',
    last_name='Dev',
    age=30,
)
```

When calling a method or class, put the arguments in a new indented line if the width is more then 79 characters.
```python
# Good
members = get_members(
    first_name='Bob',
    last_name='Dev',
    age=30
)

# Good
members = get_members(age=30)

# Bad
members = get_members(first_name='Bob', last_name='Dev', profile_page='example.com/bod', age=30)
```

Use simple if statements:
```python
# Good
if conditional:
    return True
return False

# Bad
if conditional:
    return True
else:
    return False
```

If the statement is nice and short, simplify more:
```python
# Good
return True if conditional else False

# Bad
if conditional:
    return True
else:
    return False
```

### 2.2 Python Variables
Always use declarative and meaningful variable names. Don't bother with long names:
```python
# Good
members = get_members(30)


# Bad
a = get_members(age=30)
```

Use declarative and meaningful names even in loop counters, indexes and iterables unpacking.
```python
# Good
for id, first_name in user.items():
    print(id, first_name)

# Bad
for i, n in user.items():
    print(i, n)

```

### 2.3 Python Documentation
In classes, use just a simple docstring for description:
```python
# Good
class Foo(Object):
    """
    Does this and does that.
    """
    ...

# Bad
class Foo(Object):
    ...

```

In methods, use docstrings to describe its function, arguments and return value:
```python
# Good
def Foo(self, first_name, age):
    """ 
    Does this and does that.
        
    Arguments:
    <string> first_name -- User irst_name.
    <int> -- User age.

    Returns:
        User information if success. False otherwhise.
    """ 
    ...

# Bad
def Foo(self, first_name, age):
    ...
```

When declaring class attributes outside the `__init__` method, comment on each logical block:
```python
# Good
class Foo(Object):
    # User information
    first_name = 'Bob'
    age = 30

    # User social media
    twitter_profile = '@bob'
    facebook_profile = 'facebook.com/bob'

# Bad
class Foo(Object):
    first_name = 'Bob'
    twitter_profile = '@bob'
    age = 30
    city = 'New York'
    facebook_profile = 'facebook.com/bob'
    address = 'Wall Street'
```

In a file outside the project defaults (like Django's models.py, views.py), use a docstring at its beginning to describe the utility:
```python
# Good
# file helpers/picture.py
"""
This module have utilities to create, manage and destroy pictures.
"""
...

# Bad
# file helpers/picture.py
...

```

## 3. References
Was inspired by [LFeh/coding-style](https://github.com/LFeh/coding-style).

## 4. License
[MIT License](https://opensource.org/licenses/MIT).
