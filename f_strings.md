An f-string, or "formatted string literal" lets you embed variables and expressions directly inside a string, replacing them with their values, making your code cleaner and more readable [[PEP0498]](https://peps.python.org/pep-0498).

The f-string was introduced in Python 3.6 to be the standard and preferred method for string formatting in modern Python after the `modulo (%)` operator and the string `.format()` method.


## Joining strings and integers

When you try to join a string (like "Name: ") and a number (like 95) using the `+` operator, you will get a TypeError, because the `+` operator is not supported for int  and str:

```python
>>> name = "Jack"
>>> score = 95
>>> "Name: " + name + " Score: " + score

Traceback (most recent call last):
    ...
TypeError: can only concatenate str (not "int") to str
```

You need to manually convert the number to a string using the `str()` function (called casting) to concate them.

```python
>>> name = "Jack"
>>> score = 95
>>> "Name: " + name + " Score: " + str(score)
"Name: Jack Score: 95"
```

The `str(score)` fixed the issue by `casting` the integer 95 into the string "95".

![alt text](fstrings.drawio.svg)

Before f-strings, the `.format()` strings method was another solution, You can format the previous code using the `.format()` string method:

```python
>>> name = "Jack"
>>> score = 95
>>> "Name: {} Score: {}".format(username, score)
"Name: Jack Score: 95"
```

in this example, you embed the values of the variables into the curly braces `{}` which are acting as placeholders. The `format()` method then fills your placeholders with the values of the variables `username` and `score`, in the order they are listed.

This works, but who can remember the order of the placeholders? especially in a dozen of variables. Here comes the f-strings.

## What Are F-Strings?

An f-string is a string literal prefixed with the letter f or F. This prefix tells Python to look inside the string for special expressions enclosed in curly braces `{}`.

When Python sees these, it evaluates the expression inside the braces and automatically handles the type conversion for you.

You can rewrite the previous example using an f-string:
```python
>>> username = "Jack"
>>> score = 95

>>> f"User: {username} Score: {score}"
"Name: Jack Score: 95"
```

You don't need to use `str(score)`. The f-string processor saw the integer variable score and converted it to a string for you. This results in cleaner code that is more readable because the variables are placed directly where their values will appear.

## Using Expressions Inside F-Strings

The curly braces in an f-string are not limited to just variables. You can place almost any valid Python expression inside them, such as arithmetic operations or function calls.

This allows you to perform calculations or modifications inside the string itself.

```python
>>> item_name = "Laptop"
>>> quantity = 2
>>> price_per_item = 1200

>>> f"Item: {item_name} - Total: ${quantity * price_per_item}"
"Item: Laptop - Total: $2400"
```

In this example, Python first ran `item_name.upper()` to get `'Laptop'` and calculated `2 * 1200` to get `2400` before inserting them into your final string.

