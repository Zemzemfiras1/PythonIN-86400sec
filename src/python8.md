# Section 11 : File Handling 

File handling is an essential part of programming that involves creating, reading, writing, and manipulating files. Python provides built-in functions and modules to perform file handling operations efficiently. 

## Checking File Existence

Before performing file operations, it’s good practice to check if a file exists.


### Using os Module


```python
import os 

if os.path.exists('README.md'):
    print('File exists... ')
else: print('File Not Found')
```

### Using os Module


```python
from pathlib import Path

myfile = Path('README.md')

if myfile.exists(): 
    print('File exists... ')
else: print('File Not Found')
```

### Exception Handling


```python
try:
    with open('exercices.txt', 'r') as file:
        print(file.read())
except FileNotFoundError:
    print('File not found.')
except IOError as e:
    print(f'An error occurred: {e}')

```

## Opening and Closing Files

To open a  file python uses the **open()** fuction .

**Syntax**

```python
file = open('filename', mode)
```

* **filename** :Name of the file to be opened.
* **mode** : Specifies the mode in which the file is opened (e.g., read, write).

    * ***Common file modes:***

        - 'r' : Read (default mode). File must exist.

        - 'w' : Write. Creates a new file or truncates an existing one.

        - 'x' : Create. Fails if the file exists.

        - 'a' : Append. Adds to the end of the file.

        - 'b' : Binary mode.

        - 't' : Text mode (default).

        - '+' : Open for both reading and writing.
     

**Method 1**


```python
# open file in read mode 'r'
file = open("shortstory.txt","r")
# Read file content
file.read()
```

---
if we add "file.close()" to the above cell the file will be closed 


```python
# open file in read mode 'r'
file = open("shortstory.txt","r")
# Read file content 
file.read()
file.close()
```

Note that printing content file is different to read mode as we could print a file content of closed file 


```python
# open file in read mode 'r'
file = open("shortstory.txt","r")
# Read file content 
print(file.read())
file.close()
```

---
**Method 2 : Using with Statement (Preferred Method)**

The with statement ensures the file is closed automatically:



```python
with open('shortstory.txt', 'r') as file: 
    content = file.read()
    print(content) # File is closed after this block
```

---
## Reading Files

Python provides multiple methods to read files based on requirements... 

### Reading the Entire File 
Reads the entire file content as a string



```python
with open('shortstory.txt', 'r') as file:
    content = file.read()
    print(content)

```

---
### Read Line by Line

Useful for processing files line by line


```python
with open('shortstory.txt', 'r') as file:
    for line in file:
        print(line)  # Removes newline character \n

```

---
Returns all lines as a list of strings


```python
with open('shortstory.txt', 'r') as file:
    lines = file.readlines()
    print(lines)

```

---
### Read Fixed Number of Characters


```python
with open('shortstory.txt', 'r') as file:
    content = file.read(110)  # Reads the first 110 characters
    print(content)
```

---
## Writing to Files

### Writing New Content


```python
# as we dont have a practiceFile.txt in our directory 
# 'w' will automatically create a new file 

with open('practiceFile.txt', 'w') as file:
    file.write("this is a new line ")    
```


```python
with open('practiceFile.txt', 'r') as file:
    print(file.read())
```

---
Write another line : "Date: coming soon" 


```python
with open('practiceFile.txt', 'w') as file:
    file.write("Title : Nextflow Course")
    
```


```python
with open('practiceFile.txt', 'r') as file:
    print(file.read())
    
```

### Appending Content

To avoid overwriting in your file, and append content use 'a' mode and the newline character ( \n ) (optional)


```python
with open('practiceFile.txt', 'a') as file:
    file.write('\nDate: coming soon.')

```


```python
with open('practiceFile.txt', 'r') as file:
    print(file.read())
    
```

### Writing Multiple Lines


```python
lines = ['\nFiras Zemzem ', '\nzemzemfiras@gmail.com \n']
with open('practiceFile.txt', 'a') as file:
    file.writelines(lines)  # Writes a list of strings

```


```python
with open('practiceFile.txt', 'r') as file:
    print(file.read())
    
```

## File Positioning

Python provides methods to manipulate the file pointer during reading or writing


**file.seek()** : Moves the file pointer!

    - 0 (default): Start of the file.

    - 1: Current position.
    
    - 2: End of the file.


```python
# Corrected code
with open('practiceFile.txt', 'a+') as file: # Allows both writing(appending) and reading
    file.write("Tunisia")
    file.seek(0)  # Move pointer to the start of the file
    print(file.read())  # Read the content to verify

```

### File Copying

Copy the contents of one file to another


```python
with open('practiceFile.txt', 'r') as src, open('ContactINFO.txt', 'w') as dest:
    dest.write(src.read())

```

## CSV File Handling

## Loading the Dataset

### Using csv.reader 

when you want to iterate over rows as lists.


```python
import csv

with open('employee_records.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

```

###  Using csv.DictReader

**csv.DictReader** reads the file into dictionaries where the keys are the column headers.


```python
import csv

with open('employee_records.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row)

```

---
**csv.DictReader** is particularly useful if you want to access specific fields by their names.


```python
with open('employee_records.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(f"Name: {row['Name']}, \t Department: {row['Department']}, \t Salary : {row['Salary']}")
```

## Add lines 


```python
import csv

# Add a new row to the CSV file
new_row = [9, 'Bob Brown', 'Engineering', 70000, '2024-01-15']

# Open the file in append mode ('a') to add a new row
with open('employee_records.csv', 'a', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(new_row)

# Read and print the content of the CSV file
with open('employee_records.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

```

## Filtering rows based on conditions


```python
import csv

with open('employee_records.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        if row['Department'] == 'Engineering':
            print(row)

```

## Sorting and grouping data


```python
import csv

with open('employee_records.csv', 'r') as infile, open('sorted_employees.csv', 'w', newline='') as outfile:
    reader = csv.DictReader(infile)
    sorted_data = sorted(reader, key=lambda x: int(x['Salary']), reverse=True)

    writer = csv.DictWriter(outfile, fieldnames=reader.fieldnames)
    writer.writeheader()
    writer.writerows(sorted_data)

```

## Check for Missing Data


```python
import csv

# Open the CSV file for reading
with open('employee_records.csv', 'r') as file:
    reader = csv.reader(file)
    
    # Track if any missing data is found
    missing_data_found = False

    # Check each row for missing data
    # Iterates through the rows in the CSV file, 
    # starting the row numbering from 1 (useful for reporting row numbers).

    for row_number, row in enumerate(reader, start=1):
       # print (row_number)
        
        if any(field.strip() == '' for field in row):  # Check for empty or whitespace-only fields
           #print (row_number)
            print(f"Missing data found in row {row_number}: {row}")
            missing_data_found = True

    if not missing_data_found:
        print("No missing data found in the CSV file.")

```

---


## ENJOY !!
