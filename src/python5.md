# Section 8 : Functions 

A function is a block of reusable code that performs a specific task. Functions allow us to break down complex problems into smaller, more manageable parts. Python provides a simple way to define and use functions.

```python
In this lesson, we will cover:

- Defining a function
- Function parameters
- Return values
- Function scope
- Lambda functions
- Recursive functions
```

## Defining a Function 

To define a function in Python, we use the def keyword followed by the function name, parentheses (), and a colon :. After the colon, we write the code block that should execute when the function is called.

**Syntax:** 

```python 
def function_name():
    # Code to be executed
    print("Hello, this is a function!")
```


**Example**


```python
# Make a fuction that prints "Hello Learners" 

def Greeting(): 
    print("Hello Learners")


```


```python
# Call Greeting() function
Greeting()
```

## Functions Parameters 
Functions can accept inputs, known as **parameters**. These parameters are specified within the parentheses of the function definition.

**Syntax:**
```python
def function_name(parameter1, parameter2):
    # Code that uses the parameters
    print(f"Hello {parameter1}, you are {parameter2} years old.")
```

**Example**


```python
# function name : introduce 
# Parameter  1  : name 
# Parameter  2  : age
def introduce(name, age):
    print(f"Hello {name}, you are {age} years old.")

```


```python
# Calling the function with arguments alice for name / 25 for age
introduce("Alice", 25)  

```

## Return Values 
A function can return a value using the return keyword. This value can then be used elsewhere in the program.

**Syntax:**
```python
def function_name():
    return value
```

**Example**


```python
def add_numbers(a, b):
    return a + b

result = add_numbers(10, 5)
print(f"The sum is: {result}")
```

## Local Scope 
Variables created inside a function are local to that function and cannot be accessed outside of it. This is called local scope. Variables defined outside the function are considered global variables and can be accessed anywhere in the program.

**Example**


```python
def show_local_scope():
    local_variable = "I am local"
    print(local_variable)

show_local_scope()

# Uncommenting the next line will cause an error
# print(local_variable)  # This will give an error because local_variable is not accessible outside the function

```

lets try to print local variable outside 


```python
def show_local_scope():
    local_variable = "I am local"



show_local_scope()

# Uncommenting the next line will cause an error
# print(local_variable)  # This will give an error because local_variable is not accessible outside the function

```

lets make a global variable : global_variable then implement it in our function



```python
global_variable  = "I am global"


def show_local_scope():
    print(global_variable)


show_local_scope()

```

##  Default Parameters
You can assign default values to parameters in a function. This way, if no argument is passed when calling the function, the default value will be used.

**Syntax:**
```python
def function_name(parameter1=default_value):
    # Code using the parameter
    print(parameter1)
```

**Example:**


```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet("Alice")  
greet()         
```

## Lambda Functions
A lambda function is a small anonymous function defined using the lambda keyword. These functions are typically used for short, one-off operations.

**Syntax:**
```python
lambda arguments: expression
```


```python
multiply = lambda x, y: x * y
print(multiply(4, 5))  # Output: 20

```

## Recursive Functions
A recursive function is one that calls itself in its definition. It is often used to solve problems that can be broken down into smaller, similar subproblems (e.g., calculating factorials, traversing trees).

**Syntax:**
```python
def recursive_function():
    # base case
    if condition:
        return result
    # recursive case
    else:
        return recursive_function()
```



**Example**



```python
def factorial(n):
    # Base case: factorial of 0 or 1 is 1
    if n == 0 or n == 1:
        return 1
    # Recursive case
    else:
        return n * factorial(n - 1)

print(factorial(5))  

```

## Functions as Arguments
You can pass functions as arguments to other functions. This allows for greater flexibility and allows for higher-order functions.


**Example:**


```python
def apply_function(f, x):
    return f(x)

def square(n):
    return n * n

result = apply_function(square, 5)
print(result)  # Output: 25
```

## Appling Functions in Bioinformatics

**Example: Calculating GC Content**

This function calculates the GC content of a DNA sequence.

- GC content is the percentage of G and C bases in the sequence.
    
- Args:

    - sequence (str): A string representing the DNA sequence (e.g., 'ATGCGT').
    
    - Returns:
      float: The GC content as a percentage.



```python
def gc_content(sequence):
    
    gc_count = sequence.count('G') + sequence.count('C')
    return (gc_count / len(sequence)) * 100

sequence = "ATGCGTACG"
gc_percentage = gc_content(sequence)
print(f"GC content: {gc_percentage:.2f}%")

```

**Example: Counting Nucleotides in a DNA Sequence**

This function counts the occurrences of each nucleotide in a DNA sequence.
    
- Args:

  - sequence (str): A string representing the DNA sequence (e.g., 'ATGCGT').
    
  - Returns:
    dict: A dictionary with counts for 'A', 'T', 'C', and 'G'.


```python
def count_nucleotides(sequence):
    return {'A': sequence.count('A'),
            'T': sequence.count('T'),
            'C': sequence.count('C'),
            'G': sequence.count('G')}

sequence = "ATGCGTACG"
nucleotide_counts = count_nucleotides(sequence)
print(f"Nucleotide counts: {nucleotide_counts}")

```

**Example: Finding a Subsequence in a DNA Sequence**

 This function checks if a given subsequence is found in a DNA sequence.
    
- Args:
    - sequence (str): The DNA sequence to search within.
     
    - subsequence (str): The subsequence to search for.
    
- Returns: bool: True if subsequence is found, False otherwise.


```python
def find_subsequence(sequence, subsequence):
    if subsequence in sequence:
        return True
    else:
        return False

sequence = "ATGCGTACG"
subsequence = "CGT"
found = find_subsequence(sequence, subsequence)
print(f"Subsequence found: {found}")

```

**Example: Translating DNA to Protein**
This function translates a DNA sequence into a protein sequence.
    It translates each codon (3 nucleotides) into an amino acid.
    
- Args:

  - dna_sequence (str): The DNA sequence to translate.
    
  - Returns: str: The corresponding protein sequence.


```python
def translate_dna_to_protein(dna_sequence):
    codon_table = {
        "ATA": "I", "ATC": "I", "ATT": "I", "ATG": "M",
        "ACA": "T", "ACC": "T", "ACG": "T", "ACT": "T",
        "AAC": "N", "AAT": "N", "AAA": "K", "AAG": "K",
        "AGC": "S", "AGT": "S", "AGA": "R", "AGG": "R",
        "CTA": "L", "CTC": "L", "CTG": "L", "CTT": "L",
        "CCA": "P", "CCC": "P", "CCG": "P", "CCT": "P",
        "CAC": "H", "CAT": "H", "CAA": "Q", "CAG": "Q",
        "CGA": "R", "CGC": "R", "CGG": "R", "CGT": "R",
        "GTA": "V", "GTC": "V", "GTG": "V", "GTT": "V",
        "GCA": "A", "GCC": "A", "GCG": "A", "GCT": "A",
        "GAC": "D", "GAT": "D", "GAA": "E", "GAG": "E",
        "GGA": "G", "GGC": "G", "GGG": "G", "GGT": "G",
        "TCA": "S", "TCC": "S", "TCG": "S", "TCT": "S",
        "TTC": "F", "TTT": "F", "TTA": "L", "TTG": "L",
        "TAC": "Y", "TAT": "Y", "TAA": "*", "TAG": "*",
        "TGC": "C", "TGT": "C", "TGA": "*", "TGG": "W",
        "CTA": "L", "CTC": "L", "CTG": "L", "CTT": "L",
    }
    
    protein = ""
    # Iterate over the sequence in steps of 3 nucleotides (codons)
    for i in range(0, len(dna_sequence), 3):
        codon = dna_sequence[i:i+3]
        if codon in codon_table:
            protein += codon_table[codon]
    
    return protein

dna_sequence = "ATGGCCAAGGTTTAA"
protein_sequence = translate_dna_to_protein(dna_sequence)
print(f"Protein sequence: {protein_sequence}")

```

---
## ENJOY !!
