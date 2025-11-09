# F-strings

<!-- F-strings provide a way to embed expressions inside string literals, using a minimal syntax. It should be noted that an f-string is really an expression evaluated at run time, not a constant value. In Python source code, an f-string is a literal string, prefixed with ‘f’, which contains expressions inside braces. The expressions are replaced with their values. Some examples are: -->

An f-string, or "formatted string literal", prefixed with ‘f’, lets you embed variables and expressions directly inside a string, replacing them with their values, making your code cleaner and more readable [[PEP0498]](https://peps.python.org/pep-0498).

The f-string was introduced in Python 3.6 to be the standard and preferred method for string formatting in modern Python after the modulo (%) operator and the string .format() method.



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

Before f-strings, the `.format()` strings method was another solution, but it can be verbose and lacks the flexibility of f-strings. You can format the previous code using it:

```python
>>> name = "Jack"
>>> score = 95
>>> "Name: {} Score: {}".format(username, score)
"Name: Jack Score: 95"
```

in this example, you embed the values of the variables into the curly braces `{}` which are acting as placeholders. The `format()` method then fills your placeholders with the variables `username` and `score`, in the order they are listed.

This works, but who can remember the order of the placeholders? especially in a dozen of variables. Here comes the f-strings.



## What Are F-Strings?



An f-string is a string literal prefixed with the letter f or F. This prefix tells Python to look inside the string for special expressions enclosed in curly braces {}.



When Python sees these, it evaluates the expression inside the braces and automatically handles the type conversion for you.



Let's rewrite our example using an f-string.



```python

username = "Alex"

score = 95



# Using an f-string

message = f"User: {username} Score: {score}"

print(message)

```



Notice that we did not need to use str(score). The f-string processor saw the integer variable score and converted it to a string for us. This results in cleaner code that is more readable because the variables are placed directly where their values will appear.



## Using Expressions Inside F-Strings



The curly braces in an f-string are not limited to just variables. You can place almost any valid Python expression inside them, such as arithmetic operations or function calls.



This allows you to perform calculations or modifications inside the string itself.



```python



item_name = "laptop"

quantity = 2

price_per_item = 1200



# Expressions are calculated inside the braces

total_cost_message = f"Item: {item_name.upper()} - Total: ${quantity * price_per_item}"

print(total_cost_message)

```





As you can see, Python first ran item_name.upper() to get 'LAPTOP' and calculated 2 * 1200 to get 2400 before inserting them into the final string.



Controlling Format with Specifiers



One of the most useful features of f-strings is the ability to control the formatting of the output. You can do this by adding a colon (:) after the expression, followed by a "format specifier."



A very common use case is controlling the number of decimal places for a float (a number with a decimal). This is critical for displaying prices.



Here, :.2f means "format as a fixed-point number (f) with 2 decimal places (.2)."



```python

pi = 3.14159265

price = 49.9



print(f"The value of pi is approximately {pi:.2f}")

print(f"The total price is ${price:.2f}")

```





This code rounds pi to 3.14 and ensures the price also displays two decimal places (49.90), which is ideal for currency.



Handling Literal Braces



If you need to include literal curly braces {} in your f-string (for example, if you are printing a dictionary), you can do so by "doubling them up."



```python

item = "dictionary"



print(f"A Python {item} is created with {{}}.")

```





This code will output: A Python dictionary is created with {}. The {{ is converted to a single { and }} is converted to a single }.



Conclusion



F-strings streamline the process of embedding data into strings. They solve the common TypeError problem by handling type conversions automatically, allow you to embed simple expressions, and provide a powerful way to control output format.



For new Python code (version 3.6 and higher), f-strings are the recommended approach for string formatting.