# Section 7 : Control flow statements 

Control flow statements dictate the order in which instructions in a program are executed. Python provides several mechanisms for controlling flow:

- **Conditional Statements:** Execute different blocks of code based on conditions.
- **Loops:** Repeat code execution under specified conditions.

## Conditional Statements

Conditional statements in Python allow you to execute certain blocks of code based on whether a condition is True or False. These conditions are evaluated using comparison operators or boolean expressions, which can help in making decisions in your code. The main conditional statements in Python are if, if-else, and if-elif-else.

### If-Else Statements 
If-else statements allow your program to make decisions based on certain conditions.

**Syntax** 

```python
if condition:
    # Code block executed if condition is True
else:
    # Code block executed if condition is False

```


**Basic If-Else Example**


```python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is less than or equal to 5")

```

**Example: Check for a Specific DNA Base**

write a Python program to check if a DNA sequence contains the base A (adenine)


```python
dna_sequence = "ATCGGATCGA"

if "A" in dna_sequence:
    print("The sequence contains adenine (A).")
else:
    print("The sequence does not contain adenine (A).")

```

### If-Elif-Else Example:
Sometimes, you need to check multiple conditions. This is where elif (else if) comes into play. It allows you to check multiple conditions in sequence.

```python
if condition1:
    # Code block executed if condition1 is True
elif condition2:
    # Code block executed if condition1 is False and condition2 is True
else:
    # Code block executed if all the above conditions are False
```


**Basic If-Else Example**


```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: F")

```

**Example: Classify DNA Sequence Based on Length**

use if-elif-else to classify DNA sequences based on their length (e.g., short, medium, long sequences).


```python
dna_sequence = "ATGCGTACG"

if len(dna_sequence) < 50:
    print("This is a short DNA sequence.")
elif len(dna_sequence) <= 200:
    print("This is a medium-length DNA sequence.")
else:
    print("This is a long DNA sequence.")

```

##  Loops in Python

Loops are used to repeatedly execute a block of code. Python provides two types of loops: for loops and while loops


### For Loop

The for loop is generally used when you know the number of iterations you want to perform or when you're working with a sequence of elements (such as a list, string, or tuple).

```python
for variable in sequence:
    # Code block to execute
```


**Basic Example**


```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)

```

**Example: Counting Specific Bases in a DNA Sequence**

We can use a for loop to iterate over a DNA sequence and count the occurrence of each base


```python
dna_sequence = "ATCGGATCGA"
count_A = 0
count_T = 0
count_C = 0
count_G = 0

for base in dna_sequence:
    if base == "A":
        count_A += 1
    elif base == "T":
        count_T += 1
    elif base == "C":
        count_C += 1
    elif base == "G":
        count_G += 1

print(f"A: {count_A}, T: {count_T}, C: {count_C}, G: {count_G}")

```

#### For Loop with Range


Hint : The range() function generates a sequence of numbers, which can be used with for loops.

```python
for i in range(start, stop, step):
    # Code block to execute
```
**example**


```python
for i in range(1, 6):  # Range from 1 to 5
    print(i)

```

**example : Extracting Substrings from DNA Sequence**

You can use a for loop combined with range() to extract specific sections of a DNA sequence (substrings).


```python
dna_sequence = "ATCGGATCGA"

# Extract every 3rd base from the DNA sequence
for i in range(0, len(dna_sequence), 3):
    print(dna_sequence[i:i+3])  # Extracts a substring of length 3

```

#### Nested For Loops

You can have one for loop inside another. This is useful for iterating over multi-dimensional data structures like lists of lists.


```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

for row in matrix:
    for element in row:
        print(element)

```

### While Loop

A while loop repeatedly executes a block of code as long as a specified condition is True.

```python
while condition:
    # Code block to execute as long as condition is True
```

**Example**


```python
count = 0
while count < 5:
    print(count)
    count += 1  # Increase count by 1 in each iteration

```

**Example: Searching for a Pattern in a DNA Sequence**
    
You can use a while loop when you need to iterate through a sequence and search for specific patterns, such as a certain motif in a DNA sequence.


```python
dna_sequence = "ATCGGATCGAATGATGCTAG"
pattern = "ATG"
index = 0

while index < len(dna_sequence):
    index = dna_sequence.find(pattern, index)
    if index == -1:  # No more occurrences found
        break
    print(f"Pattern '{pattern}' found at index {index}")
    index += len(pattern)  # Move past the found pattern

```

## Break Statements

The break statement is used to exit the current loop (either for or while) prematurely when a specific condition is met. After the break statement is executed, the control moves to the first statement after the loop.



**Syntax 1 :**

```python
for item in iterable:
    # code block
    if condition_to_break:
        break  # Exit the loop if the condition is met
    # other code

```
**Syntax 2 :**
```python
while condition:
    # code block
    if condition_to_break:
        break  # Exit the loop if the condition is met
    # other code

```

###  Break in a for loop 

The following example finds the first occurrence of the number 5 in a list of numbers and then exits the loop using the break statement.


```python
numbers = [1, 3, 5, 7, 9, 5, 11]
for number in numbers:
    if number == 5:
        print("Found the number 5!")
        break  # Exit the loop after finding the first 5

```

### Break in a while loop

This example demonstrates the use of break in a while loop, which exits once the variable count exceeds 5.


```python
count = 0
while count <= 5:
    print(count)
    if count == 3:
        break  # Exit the loop when count is 3
    count += 1

```

**Example: Stop Searching for Pattern After a Certain Number of Occurrences**



```python
dna_sequence = "ATGCGATGCTGATGGAAT"
pattern = "ATG"
occurrence_limit = 2
count = 0
index = 0

while count < occurrence_limit:
    index = dna_sequence.find(pattern, index)
    if index == -1:  # No more occurrences found
        break
    print(f"Pattern '{pattern}' found at index {index}")
    count += 1
    index += len(pattern)  # Move past the found pattern

```

## Continue Statement

The continue statement is used to skip the current iteration of a loop and move to the next iteration. It is often used when you want to skip certain conditions but continue processing the remaining items.



**Syntax1:**

```python
while condition:
    # code block
    if condition_to_skip:
        continue  # Skip the rest of the code and move to the next iteration
    # other code

```

**Syntax2:**

```python
for item in iterable:
    # code block
    if condition_to_skip:
        continue  # Skip the rest of the code and move to the next iteration
    # other code
```

### Continue in a for loop

The following example skips the number 5 in the list of numbers, but prints the rest.



```python
numbers = [1, 3, 5, 7, 9, 5, 11]
for number in numbers:
    if number == 5:
        continue  # Skip the rest of the loop when number is 5
    print(number)

```

### Continue in a while loop

This example skips the iteration when the variable count is 3, but continues the loop for other values.



```python
count = 0
while count <= 5:
    count += 1
    if count == 3:
        continue  # Skip the iteration when count is 3
    print(count)

```

**Example: Skip a Specific Base in a DNA Sequence**


```python
dna_sequence = "ATCGGATCGA"
for base in dna_sequence:
    if base == "G":
        continue  # Skip 'G' bases
    print(base)

```

## Practice 

### EXercice 1 : 
Write a program that checks if a given DNA sequence contains both "ATG" (start codon) and "TAA" (stop codon).



```python
dna_sequence = input("Enter DNA sequence: ")

if "ATG" in dna_sequence and ("UAG" in dna_sequence or "UAA" in dna_sequence or "UGA" in dna_sequence):
    print("The sequence contains both the start and stop codons.")
else:
    print("The sequence does not contain both start and stop codons.")

```

### Exercice 2 :

Write a program to count how many times the codon "ATG" appears in a DNA sequence.




```python
dna_sequence = "ATGCGATGCTGATGGAAT"
count_ATG = 0
#print(len(dna_sequence))
#print(range(len(dna_sequence) - 2))

for i in range(len(dna_sequence) - 2):  # Loop through the sequence
    #print(i)
    #print(dna_sequence[i:(i+3)])
    if dna_sequence[i:i+3] == "ATG":
        count_ATG += 1

print(f"Codon 'ATG' appears {count_ATG} times.")

```

### Exercice 3 : 

Write a program that continuously asks the user for DNA sequences and checks if the sequence is valid (only contains A, T, C, G) until a valid sequence is entered.


```python
valid_bases = set("ATCG")
while True:
    dna_sequence = input("Enter a DNA sequence: ")
    if set(dna_sequence.upper()).issubset(valid_bases):
        print("Valid DNA sequence.")
        break
    else:
        print("Invalid DNA sequence. Please enter only A, T, C, and G.")

```

### Exercice 4 : 

Write a program that stops when it finds the first "CG" pair in a DNA sequence and skips all other "CG" pairs.



```python
dna_sequence = "ATGCGATGCGCGT"
index = 0

while index < len(dna_sequence):
    index = dna_sequence.find("CG", index)
    if index == -1:  # No more occurrences found
        break
    print(f"'CG' found at index {index}")
    index += 2  # Move past the found "CG"

```

---
## Enjoy
