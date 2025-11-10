An f-string (or "formatted string literal") lets you embed variables and expressions directly into a string, making your code more readable [PEP0498]. Introduced in Python 3.6, they are the preferred way to format strings in modern Python, replacing older methods like the `modulo (%)` operator and `.format()`.

## Joining Strings And Integers

When you try to join a string and a number with the `+` operator causes a `TypeError` because `+` doesn't support combining int and str types:
```python
>>> name = "Jack"
>>> score = 95
>>> "Name: " + name + " Score: " + score

Traceback (most recent call last):
    ...
TypeError: can only concatenate str (not "int") to str
```
As the traceback shows,  It's telling you that Python can only concatenate a `str` to another `str`, not an `int`.

To fix this, you can manually convert the number to a string using `str()`, a process called "casting":

```python
>>> name = "Jack"
>>> score = 95
>>> "Name: " + name + " Score: " + str(score)
"Name: Jack Score: 95"
```
This works because By wrapping `score` with `str()`, you turned the integer 95 into the string "95". allowing Python to concatenate only strings without raising a `TypeError`.

![alt text](fstrings.drawio.svg)

## Using the `.format()` Method
Before f-strings, the `.format()` string method was another solution.
With this method, you place curly braces `{}` in your string to act as placeholders. Then, you call the `.format()` method on the string itself, passing in the variables you want to insert.

You can format the previous code using the `.format()` string method:
```python
>>> name = "Jack"
>>> score = 95
>>> "Name: {} Score: {}".format(name, score)
"Name: Jack Score: 95"
```
In this example, the `.format()` method fills the placeholders with the values from the name and score variables, in the order they are listed.

This works, but keeping track of the placeholder order can get confusing, especially when you have many variables. Here come f-strings.

## What Are F-Strings?

An f-string is a string literal prefixed with the letter f or F. This prefix tells Python to look inside the string for special expressions enclosed in curly braces `{}`, and When it see the `{}`, it evaluates the expression inside the braces and automatically handles the type conversion.

You can rewrite the previous example using an f-string:
```python
>>> name = "Jack"
>>> score = 95

>>> f"User: {name} Score: {score}"
"Name: Jack Score: 95"
```
Notice you didn't need `str(score)`. The f-string handled the conversion automatically. The code is much cleaner because the variables are placed directly inside the string.

### Using Expressions Inside F-Strings

The curly braces in an f-string are not limited to just variables. You can place almost any valid Python expression inside them, such as arithmetic operations or function calls.

This allows you to perform calculations or modifications inside the string itself.

```python
>>> item_name = "Laptop"
>>> quantity = 2
>>> price_per_item = 1200

>>> f"Item: {item_name} - Total: ${quantity * price_per_item}"
"Item: Laptop - Total: $2400"
```
The f-string evaluated the expression ‍‍‍`quantity * price_per_item` and inserted the result, `2400`, directly into the final string.
