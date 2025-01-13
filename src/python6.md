# Section 9 : Error Handling

Error handling is a critical part of writing reliable Python code. In this course, we'll dive deep into Python's error-handling mechanism, starting from the basics and moving towards advanced topics like custom exceptions, context managers, and logging errors. By the end of this course, you'll have a solid understanding of how to manage errors effectively in your Python programs.

# Basics of Error Handling

**What are Errors and Exceptions?** 

- **Errors:** Critical problems that are typically not recoverable (e.g., syntax errors, system-level issues).
  
- **Exceptions:** Conditions that arise during the execution of a program but can be handled and recovered from.

# Try-Except Block
The try-except block is the fundamental building block of error handling in Python. It allows you to catch and handle exceptions that occur during the execution of a program. By using try-except, you can prevent your program from crashing and provide meaningful responses to errors.

**Why Use try-except?**

- Prevent your program from crashing due to runtime errors.
- Gracefully handle unexpected situations and provide meaningful error messages.
- Allow execution of alternative logic when errors occur.

**Syntax:**
```python
try:
    # Code that might raise an exception
except ExceptionType:
    # Code to handle the exception
```

Lets try to print this code : 



```python
print(10 / 0)

```

By using try-except, you can prevent your program from crashing and provide meaningful responses to errors.


```python
try:
    result = 10 / 0
except:
    print("An error occurred.") # if it causes an error print "An error occurred."

```

## Using the Exception Object
To access details about the exception, use the as keyword.


```python
try:
    x = 10 / 0                    # will crach and provide an error
except ZeroDivisionError as e:    # if it is an error print details about it without crashing.
    print(f"Error occurred: {e}")
```

## Multiple except Blocks
You can use multiple except blocks to handle different types of exceptions.



```python

try:
    x = int("hello")  # Will raise a ValueError
except ZeroDivisionError:
    print("Division by zero error")
except ValueError:
    print("Invalid input: Could not convert to an integer")

```

## Generic Exception Handling

To handle any exception, use except Exception. While it's better to catch specific exceptions, this can be useful for debugging.

**Syntax:**
```python
try:
      # Code that might raise an exception
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

**Example 1**


```python
try:
    result = 10 / "a"  # TypeError
except Exception as e:
    print(f"An unexpected error occurred: {e}")

```

**Example 2: Reading a File Safely**


```python
try:
    with open("file.txt", "r") as file:
        data = file.read()
except FileNotFoundError:
    print("Error: The file does not exist.")
except PermissionError:
    print("Error: You do not have permission to access this file.")

```

or making it more general 


```python
try:
    with open("file.txt", "r") as file:
        data = file.read()
except Exception as e:
    print(f"Error: {e}")
```

# Else and Finally
The **else** and **finally** clauses add more control and flexibility to Python's try-except mechanism, allowing you to handle code execution in different scenarios, such as when no exception occurs or when cleanup operations are needed.

## Else Clause
The else block is executed only if no exception occurs in the try block. This is useful for separating error handling (except) from normal execution when everything works as expected.

- **If an exception occurs**: The else block is skipped.
- **If no exception occurs**: The else block is executed.

**Syntax**
```python
try:
    # Code that might raise an exception
except ExceptionType:
    # Code to handle the exception
else:
    # Code to execute if no exception occurred
```


```python
try:
    result = 10 / 2 # No exception occurs
except ZeroDivisionError:
    print("Error: Division by zero.")
else:
    print(f"Division successful, result is {result}")

```

## finally Clause
The finally block is executed no matter what, whether an exception is raised or not. This is useful for cleanup actions, like closing a file or releasing a resource.

**Syntax**
```python
try:
    # Code that might raise an exception
except ExceptionType:
    # Code to handle the exception
finally:
    # Code to execute regardless of what happens
```

**Example**


```python
try:
    x = int(input("Enter the numerator: "))
    y = int(input("Enter the denominator: "))
    div = x / y  # Perform division
except ValueError as e:
    print(f"Error: Invalid input. Please enter integers only. {e}")
except ZeroDivisionError as e:
    print(f"Error: Cannot divide by zero. {e}")
else:
    print(f"Division was successful: {x}/{y} = {div}")
finally:
    print("This will always execute.")

```

# raise Statement in Python
The raise statement in Python is used to explicitly raise an exception. It allows you to signal that something unexpected has occurred and gives you control over the error being raised.

- **ExceptionType:** The type of exception you want to raise (e.g., ValueError, TypeError, KeyError, or a custom exception).
- **Error message:** An optional message providing more details about the error.



**Syntax**
```python
raise ExceptionType("Error message")
```


**Example 1 : Input Validation**


```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    print(f"Valid age: {age}")

```


```python
# Test the function
try:
    validate_age(-5)
except ValueError as e:
    print(f"Error: {e}")

```

**Example 2: Raising TypeError**


```python
def add_numbers(a, b):
    if not isinstance(a, (int, float)) or not isinstance(b, (int, float)):
        raise TypeError("Both arguments must be numbers")
    return a + b

# Test the function
try:
    result = add_numbers(10, "20")
except TypeError as e:
    print(f"Error: {e}")

```

**Reraising an Exception**

If you want to re-raise an exception that you've caught, you can use raise without specifying an exception. This is useful for adding context to an error before passing it on.




```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Handling ZeroDivisionError")
    raise
```

**Using raise with a Cause**
    
The raise statement can be used with a from keyword to link a new exception to an original one. This is helpful for debugging complex issues.


```python
try:
    int("abc")  # Raises ValueError
except ValueError as e:
    raise TypeError("Conversion error occurred") from e

```

# Using Assert for Debugging
The assert statement is a debugging tool in Python used to test assumptions in your code. It helps ensure that a condition is true at a specific point in the program. If the condition evaluates to False, assert raises an AssertionError and optionally displays an error message.

**Syntax**
```python
    assert condition, "Error message (optional)"
```

- condition: A boolean expression that you expect to be True.
- "Error message": Optional; describes why the assertion failed.

If the condition evaluates to False:
   - An AssertionError is raised.
   - The optional error message (if provided) is displayed.

**When to Use assert**
- To test assumptions in your code while developing or debugging.
- To ensure inputs to a function meet certain criteria.
- To check the state of variables at critical points in your code.


**Example** 


```python
x = 10
assert x > 0, "x must be positive"
print("Assertion passed!")

```

Try a negative x 


```python
x = -5
assert x > 0, "x must be positive"
print("Assertion passed!")

```

**Example 2 :**


```python
assert 2 + 2 == 4, "Math error"
assert 2 + 2 == 5, "Math error"  # This will raise AssertionError

```

**Validating Function Input**


```python
def divide(a, b):
    assert b != 0, "Denominator cannot be zero"
    return a / b

# Test the function
print(divide(10, 2))  # Valid
print(divide(10, 0))  # Raises AssertionError

```

**Example 3 : Checking Data Integrity**


```python
data = [1, 2, 3, 4]
assert all(isinstance(x, int) for x in data), "All elements in the list must be integers"
print("Data is valid!")

```

# Handling Signals and External Errors
Signals are a mechanism used by operating systems to notify a process of an event. Python's signal module allows you to handle these signals gracefully.

**Common Use Cases for Signals**
- Handling Ctrl+C (keyboard interrupt) gracefully.
- Responding to timeouts or resource limits.
- Coordinating between processes in multiprocessing or parallel programs.
Note : This part will be developped in another part.

---

## ENJOY !! 
