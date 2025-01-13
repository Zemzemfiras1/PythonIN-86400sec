# Python Basics

**What is Python?**

Python is a versatile, high-level programming language that is easy to learn and use. It is widely used in various domains such as web development, data science, machine learning, and more....

**Why Use Python?**
- Simple and readable syntax.
- Huge standard library.
- Cross-platform compatibility.



## Section 1: Variables and Data Types



### Variables
In Python, variables are used to store data values, and the type of each variable is automatically determined based on the value assigned to it
- **Example: Variables & its Types**

```python
# int: Integer type, stores whole numbers.
int: 10

# float: Floating-point type, stores numbers with decimal points.
float: 3.14

# complex: Complex number type, stores numbers with both real and imaginary parts.
complex: (1+2j)

# str: String type, stores sequences of characters (text).
str: Hello, World!

# list: List type, an ordered and mutable collection of elements.
list: [1, 2, 3, 'apple']

# tuple: Tuple type, an ordered but immutable collection of elements.
tuple: (1, 2, 3, 'banana')

# dict: Dictionary type, stores key-value pairs.
dict: {'key1': 'value1', 'key2': 42}

# set: Set type, stores unordered collections of unique elements.
set: {1, 2, 3, 4}

# frozenset: Frozenset type, an immutable version of a set.
frozenset: frozenset({1, 2, 3, 4})

# bool: Boolean type, stores either True or False.
bool: True

# bytes: Bytes type, stores immutable sequences of bytes.
bytes: b'Hello'

# NoneType: Represents the absence of a value or a null value.
NoneType: None

```

### Numeric and floats 
    - Create 2 variable a & b , then assign them numeric values eqaul to 77 and 3 


```python
a = 77
b = 3
```

    - print them , Then make 4 new variables :
        - sum_ab           # sum        => + 
        - diff_ab          # Difference => - 
        - prod_ab          # Product    => * 
        - quot_ab          # Qutient    => /


```python
# print the value assined to the variable "a"
print(a) 
print ("The type of the value ",a," is :", type(a))
```


```python
# print the value assined to the variable "b"
print(b) 
print ("The type of the value ",b," is :", type(b))

```


```python
sum_ab = a + b
print(sum_ab)
diff_ab = a - b
print(diff_ab)
prod_ab = a * b
print(prod_ab)
quot_ab = a / b
print(quot_ab)
```


```python
#check the type of the value quot_ab : 
print(type(quot_ab))
```

---

## Section 2 :String Manipulation
Strings are sequences of characters enclosed in either single (') or double (") quotes in Python. String manipulation refers to the various operations you can perform on strings, such as concatenation, slicing, modification, and more. Python provides a variety of built-in methods that allow you to work with strings efficiently.


```python
str1 = "Hello"
str2 = "Learner"

print(type(str1))
print(type(str2))
```

#### Concatination


```python
without_space = str1+str2
print(without_space)
```

Add a space between the 2 strings 


```python
with_space = str1+" "+str2
print(with_space)
```

#### Length
Getting the number of characters in a string using len()


```python
print("Length of Hello = ",len(str1))
print("Length of Learner = ",len(str2))
print("Length of 'Hello Learner' = ",len(with_space)) 

```

#### Upper & Lowercase



```python

print(str1.lower())  # Expected output: hello
print(str2.upper())  # Expected output: LEARNER
```

#### Check for substring


```python
text = "consistency if a picotal key in Learning "
# Check if lazy exist in text ?? 
print("Lazy" in text)  
# Check if Cons exist in text ?? 
print("Cons" in text)  
# Check if consistency exist in text ?? 
print("consistency" in text)  
```

#### Replace Substring 


```python
text = "I love coding with R ."
new_text = text.replace("R", "Python")
print(new_text) 
```

#### Remove Whitspaces 


```python
sentence = "   Python is awesome !"
print(sentence)
clean_sentence = sentence.strip()
print(clean_sentence)
```

#### Split String
Given the string "apple,banana,cherry", split it into a list of fruits.


```python
fruits = "apple,banana,cherry"
print(fruits) 
```


```python
splitted_fruits = fruits.split(",")
print(splitted_fruits)  # Expected output: ['apple', 'banana', 'cherry']
```

#### Join Strings


```python
words = ['I', 'Love', 'snakes']
sentence = " ".join(words)
print(sentence)  
```

#### Count Occurrences


```python
seq = "ATCGGGCATACG"
count = seq.count("G")
print(count)  
```

#### String Slicing
Slicing allows you to extract a portion of a string by specifying the start and end indices. You can also specify a step, which allows you to skip characters.
```
string[start:end:step]
```


- **Basic Slicing**


```python
text = "Python Programming"

# Slicing from index 0 to 5 (exclusive)
result = text[0:5]
print(result)   # This slices the string from index 0 to 4 (because the end index is exclusive).


```

This slices the string from index 0 to 4 (because the end index is exclusive).

- **Slicing with Step**


```python
text = "Python Programming"

# Slicing from index 0 to 12 with a step of 2
result = text[0:12:2]
print(result)  # Output: Pto rg

```

This extracts every second character starting from index 0 up to index 11. The characters selected are "P", "t", "o", " ", "r", "g".

#### Omitting Start and End
You can omit the start and end values to slice from the beginning or to the end of the string:


```python
text = "Python Programming"

# Slicing from the start to index 6 (exclusive)
result1 = text[:6]
print(result1)  # Output: Python
```


```python
# Slicing from index 7 to the end of the string
result2 = text[7:]
print(result2)  # Output: Programming

```

**Explanation:**

[:6] slices from the beginning of the string up to (but not including) index 6.

[7:] slices from index 7 to the end of the string.


#### Negative Indices
In Python, negative indices can be used to slice the string from the end.


```python
text = "Python Programming"

# Slicing from the second last character to the end
result = text[-2:]
print(result)  # Output: ng
```

**Explanation:** Negative indices count from the end of the string. Here -2 starts from the second last character and slices to the end of the string.

#### Reverse Slicing
You can also use negative steps to slice a string in reverse order.


```python
text = "Python Programming"

# Slicing in reverse order
result = text[::-1]
print(result)  # Output: gnimmargorP nohtyP
```

**Explanation:** [::-1] reverses the string by stepping backwards through every character.

---


**ENJOY !!**
