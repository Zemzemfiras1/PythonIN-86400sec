#  Section 3 : Lists

A list is a mutable, ordered collection of items. A list can contain elements of different data types, including numbers, strings, and even other lists.

```
my_list = [item1, item2, item3, ...]
```
 * Items in the list are separated by commas.
 * Lists are ordered, meaning the items have a defined order, and this order will not change unless you specifically reorder them.
 * Lists are mutable, meaning you can change their contents (add, remove, or modify elements)
### Basic Operations on Lists:


##### print the hole list 


```python
my_list = [1, 2, 3, 5,0 ,77]
print(my_list)
```

##### Length of the list:
Use len() to get the number of elements in a list


```python
print(len(my_list))  # Prints the length of the list
```

##### Accessing elements: You can access elements in a list using their index.


```python
print(my_list[0])  # Prints item 1
print(my_list[1])  # Prints item 2
print(my_list[5])  # Prints the last item 
```

##### List Slicing
list slicing allows you to access a portion (sublist) of a list by specifying a range of indices. The syntax for slicing is:
            
            my_list[start:end]

 * start: The index of the first element you want to include in the slice.
 * end: The index of the element where the slice should stop before. (The slice will not include this index.)

- To Better understand it lets print the indexes along with the values is to use the built-in enumerate() function, which returns both the index and the value as a tuple during iteration.



```python
print("my list is : ", my_list)

for index, value in enumerate(my_list):
    print(f"Index {index}: {value}")
```


```python
print(my_list[1:4])

```

Another trick is to start counting comma from where to start and where it should end 
```
my list is :  [1 , 2 , 3 , 5 , 0 , 77]

comma indexes [v 1 v 2 v 3 v 4 v 5 v 6]
```
Lets Try to print the item3 > item 6 



```python
print(my_list[2:6])
```

Start Printing from the first item 


```python
print(my_list[0:])
```

Start Printing from the 3rd item


```python
print(my_list[2:])
```

Print until the 3rd item


```python
print(my_list[:3])
```

Print The last item 


```python
print(my_list[-1])
```

You can also print the entire ist using : 


```python
my_list[:] 
```

##### Add an element (Item) 
You can add elements to the list using **append()** funciton which allow the user to add an element to the end of the list.


```python
my_list.append(100)  # Adds 100 at the end of the list
print(my_list)

```

You can add elements to the list using **insert()** funciton which allow the user to add an element at a specific position (index) in the list.

Syntax : 

```
list.insert(index, element)
```


```python
my_list.insert(1,88)  # Adds 4 at the end of the list
print(my_list)

```


```python
print(my_list)

```

##### Remove an element (Item) 
You can remove elements using remove() which Removes the first occurrence of the specified value from the list


```python
my_list.remove(100)
print(my_list)
```

You can remove elements using del() which deletes an element at a specified index or the entire list.

```
del list[index]
del list[start:end]   # For slicing
del list              # To delete the entire list
```



```python
del my_list[0]
print(my_list)

```

You can remove elements using pop() which removes and returns the element at the specified index (or the last element if no index is provided)
```
list.pop(index)
```


```python
my_list.pop()
print(my_list)

```

---

# Section 4 : Tuples



A tuple is a collection of ordered, immutable elements in Python. Tuples are defined by enclosing elements in parentheses () and are often used for fixed collections of related data.

- Structure :
 ```
 my_tuple = (Value1, Value2, Value3, ....)

 ```
Tuples in Python are immutable, which means you cannot modify a tuple after it is created. This includes adding, removing, or changing individual elements.
Immutability makes tuples:

- Safer to use as constants, preventing accidental changes.
- Hashable, allowing them to be used as keys in dictionaries or elements in sets.

### Creating a tuple
- example 1 : 



```python
tuple1 = (42, "hello", 3.14)
print(tuple1)
```

- example 2 : use tuple() instructor


```python
tuple2 = tuple(["42", "hello", "3.14"])
print(tuple2)
```

### Accessing Tuple Elements

Tuples support indexing to access individual elements


```python
my_tuple = (10, 20, 30, 40)
print(my_tuple[0])  # First element
print(my_tuple[-1]) # Last element
```

### Slicing Tuples



Tuples can also be sliced to create subsets


```python
my_tuple = (0, 1, 2, 3, 4, 5)
print(my_tuple[1:4])  # Elements from index 1 to 3
print(my_tuple[:3])   # First three elements
```

### Concatenation


```python
t1 = (1, 2)
t2 = (3, 4)
t3 = t1 + t2
print(t3) 

```

### Repetition 


```python
t = (1, 2)
print(t * 3)  

```

### Unpacking

Assign tuple elements to variables:


```python
t = (1, 2, 3)
a, b, c = t
print(a, b, c)  

```

### occurrences
 Using count(): Returns the number of occurrences of a value.


```python
t = (1, 2, 2, 3)
print(t.count(2))  

```

### Indexing 

Using index(): Returns the index of the first occurrence of a value.



```python
print(t.index(3))   

```

### Converting Between Tuples and Other Types

Convert a list to a tuple:


```python
lst = [1, 2, 3]
t = tuple(lst)
print(t) 
```

Convert a tuple to a list:


```python
t = (1, 2, 3)
lst = list(t)
print(lst)  

```

###  Nested Tuples


```python
t = ((1, 2), (3, 4))
print(t[0])  
print(t[0][1])   
```

### Comparison

tuples are compared lexicographically, meaning they are compared element by element from left to right until a difference is found.

**Key Notes on Tuple Comparisons:**

 - If the first elements are equal, the comparison moves to the next elements.
 - If all elements are equal up to the shorter tuple's length, the shorter tuple is considered smaller.
 - Lexicographic comparison mimics how words are compared in a dictionary.



```python
t1 = (1, 2, 3)
t2 = (0, 1, 4)
print(t1 < t2)  # Output: False

```

Tuple Comparison Process
Given:

t1 = (1, 2, 3)

t2 = (0, 1, 4)

Compare the first elements:

t1[0] is 1, and t2[0] is 0.

Since 1 > 0, the comparison stops here.

The result of the comparison is determined solely by this first element comparison: 1 > 0.

Outcome : Since t1[0] > t2[0], the condition t1 < t2 is False.


```python
(1, 2, 3) < (1, 2, 4)  # True because 3 < 4

```


```python
(1, 2) < (1, 2, 0)     # True because shorter tuples are compared only to their length

```


```python
(0, 4, 5) < (1, 2, 3)  # True because 1 > 0

```

### Deleting Tuples 


```python
t = (1, 2, 3)
del t
print(t)
```

---

#  Section 5 : Sets


**What are Sets?**
- A set is a collection of unique and unordered elements in Python.
- Defined using `{}` or the `set()` function.
  

- Create an empty set named myset : 


```python
my_set = set()

# print my_set 
print(my_set)

# check my_set type 
print(type(my_set))
```

### Adding Elements to Sets

- Lets create a simple set which contains these n° 1,2,3,4,5  :


```python
my_set = {1, 2, 3, 4, 5}
print(my_set)

```

- Add add an element  to my set eg. 5 


```python
new_set = my_set.add(0)  
print(new_set)  
```

**Explanation :**  The reason new_set = my_set.add(5) gives you None is that the .add() method in Python does not return any value; it modifies the set in place. When a method doesn't return anything explicitly, Python implicitly returns None.
- Lets try 


```python
my_set.add(0)  
print(my_set)  
```

- Adding multiple elements to a set using the update()


```python
print("Initial set :",my_set)

# Add multiple elements
my_set.update([6, 7, 8])

print("Updated set :", my_set)

```

### Removing Elements from Sets

- To remove an element for a set , you may use either .remove() which Raises a KeyError if the element is not found.
- Use Case: When you're certain the element exists in the set.



```python
print("Initial set : ", my_set)
```


```python
# Remove n° 3
my_set.remove(3)
print(my_set)
```

- **Re-run the above cell and checkout what is the output**

- To remove an element for a set , you may use either .discard() Does not raise an error if the element is not found; it simply does nothing.
- Use Case: When you're not sure if the element exists and want to avoid errors.


- **Try to remove the non-existant element "3" removed before** 


```python
# Remove n° 3
my_set.discard(3)
print(my_set)
```

**Summary**
| Method      | Behavior if the element is not in the set | Raises Error? | Use Case                                |
|-------------|-------------------------------------------|---------------|----------------------------------------|
| `.remove()` | Raises a `KeyError`.                      | Yes           | Use when you're sure the element exists. |
| `.discard()` | Does nothing.                            | No            | Use when you're not sure if the element exists. |


### Membership Testing
Check if an element exists in a set using the `in` keyword.



```python
print(my_set)
print(3 in my_set)  
print(6 in my_set)  
```

### Mathematical Operations
Mathematical Operations on Sets :
1. Union (`|` or `.union()`)
2. Intersection (`&` or `.intersection()`)
3. Difference (`-` or `.difference()`)
4. Symmetric Difference (`^` or `.symmetric_difference()`)


```python
set_a = {1, 2, 3, 4}
set_b = {3, 4, 5, 6}
```

**Union**


```python
print("set_a",set_a)
print("set_b",set_b)

print("Union:", set_a | set_b)

```

**Intersection**


```python
print("set_a",set_a)
print("set_b",set_b)

print("Intersection:", set_a & set_b)

```

**Difference**


```python
print("set_a",set_a)
print("set_b",set_b)

# This returns elements that are in set_a but not in set_b
# unique to set_a 

print("Difference (A - B):", set_a - set_b) 

#This returns elements that are in set_b but not in set_a.
# unique to set_b

print("Difference (B - A):", set_b - set_a)
```

**Symmetric Difference**


```python
#The symmetric difference consists of the parts of A and B that do not overlap.
print("Symmetric Difference:", set_a ^ set_b)

```

###  Copying Sets
Copying sets is essential when you want to work with a new set derived from an existing set without altering the original set. Without copying, any modifications to the new set would also affect the original set (if both sets reference the same memory location). By creating a copy, you ensure that the original data remains unchanged.


```python
original_set = {1, 2, 3}
copy_set = original_set  # No copying, both refer to the same set
copy_set.add(4)

print("Original Set:", original_set)  # Output: {1, 2, 3, 4}
print("copy Set:", copy_set)           # Output: {1, 2, 3, 4}

```

- remove the element 4 from the copied set 


```python
print("Original Set:", original_set)
print("copy Set:", copy_set)     
copy_set.remove(4)
print("modified_set :",copy_set)

```

### Sets as Filters

- Create an empty set named set_with_duplicates containing {1, 2, 2, 3, 4, 4, 5}: 


```python
set_with_duplicates = {1, 2, 2, 3, 4, 4, 5}
print("Set removes duplicates and only let unique element:", set_with_duplicates)
```

---

##  Summary 


#### Key Differences Between List, Tuple, and Set

| **Feature**           | **List**                                   | **Tuple**                                 | **Set**                                   |
|------------------------|--------------------------------------------|-------------------------------------------|-------------------------------------------|
| **Definition**         | Ordered, mutable collection of elements.  | Ordered, immutable collection of elements.| Unordered, mutable collection of unique elements. |
| **Syntax**             | Defined using square brackets `[]`.       | Defined using parentheses `()`.           | Defined using curly braces `{}` or the `set()` function. |
| **Order**              | Maintains the order of elements.          | Maintains the order of elements.          | Does not maintain any specific order.     |
| **Mutability**         | Mutable: Can add, remove, or modify elements. | Immutable: Elements cannot be changed after creation. | Mutable: Can add or remove elements, but not change individual values. |
| **Duplicates**         | Allows duplicate elements.                | Allows duplicate elements.                | Does not allow duplicate elements.        |
| **Performance**        | Slower than tuples due to mutability.      | Faster than lists for iterations due to immutability. | Faster lookups and membership tests due to hashing. |
| **Use Case**           | Suitable for collections that may change. | Suitable for fixed collections of data.   | Suitable for collections of unique items. |
| **Methods**            | Extensive: e.g., `append()`, `remove()`.  | Limited: e.g., `count()`, `index()`.      | Specialized: e.g., `add()`, `remove()`, `union()`, `intersection()`. |
| **Homogeneity**        | Can store heterogeneous elements.          | Can also store heterogeneous elements.    | Can also store heterogeneous elements, but all elements must be hashable. |
| **Example**            | `[1, 2, 3]`                               | `(1, 2, 3)`                               | `{1, 2, 3}` or `set([1, 2, 3])`           |


---
## ENJOY !!
