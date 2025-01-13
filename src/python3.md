# Section 6 : Dictionaries
A Python dictionary is an unordered collection of items. It is a collection of key-value pairs, where each key is unique, and the value can be any Python object.

```python
my_dict = {key1: value1, key2: value2, key3: value3 ... }

    or

my_dict = dict(key1=value1, key2=value2, key3=value3 ...)
```


### Creating a Dictionary
To create a dictionary, you can use curly braces {} or the dict() constructor.


```python
my_dict_exp1 = {'name': 'Alice', 'age': 25, 'city': 'New York'}
print(my_dict_exp1)

```


```python
my_dict_exp2 = dict(name='Firas', work='PhD Student', city='Tunisia')
print(my_dict_exp2)

```

### Accessing Values by Key
**using square brackets []**

You can access the value associated with a specific key by using square brackets [].


```python
print(my_dict_exp1['name'])  

```

**Using the get() Method**

The get() method returns the value for the given key if it exists, otherwise, it returns None (or a default value if provided).




```python
# get the value assigned to the key age in my_dict_exp1

print(my_dict_exp1.get('age')) 
```


```python
# get the value assigned to the key gender in my_dict_exp1

print(my_dict_exp1.get('gender')) 
```


```python
# get the value assigned to the key age then gender in my_dict_exp1
# if the value do not exist return a text 'notfound ha ha ha'

print(my_dict_exp1.get('age','not found ha ha ha')) 
print(my_dict_exp1.get('gender','not found ha ha ha')) 
```

**Accessing Keys**
keys() - Returns a view of all keys in the dictionary.


```python
print(my_dict_exp1.keys())    

```

**Accessing Values**
values() - Returns a view of all values in the dictionary.


```python
print(my_dict_exp1.values()) 
```

**Accessing Items**
keys() - Returns a view of all keys in the dictionary.


```python
print(my_dict_exp1.items())
```

### Modifying Dictionaries
**Adding Items**

You can add new key-value pairs by simply assigning a value to a new key.


```python
my_dict_exp2['email'] = 'zemzemfiras@GMail.com'
print(my_dict_exp2)
```

**Updating Items**

You can change the value of an existing key by assigning a new value.


```python
my_dict_exp2['email'] = 'zemzemfiras@gmail.com'
print(my_dict_exp2)
```

---

Now we are only using this exmaple 


```python
my_dict_exp2 = dict(name='Firas', work='PhD Student', city='Tunisia', email='zemzemfiras@gmail.com')
print(my_dict_exp2)
```

**Removing Items**

Use the del keyword to remove a key-value pair.


```python
del my_dict_exp2['city'] 
print(my_dict_exp2)

```

use the pop() method to remove and return a value


```python
removed_value = my_dict_exp2.pop('name')  # Removes 'name' and returns 'Alice'
print("removed value is :",removed_value)

```

**Clearing Dictionaries**


```python
my_dict_exp1.clear()  # The dictionary is now empty
print(my_dict_exp1)
```

### Nested Dictionaries
A nested dictionary is simply a dictionary that contains other dictionaries as values. This allows for hierarchical data representation, making it useful for complex data structures where values themselves are dictionaries or require grouping into logical structures.

**Importance of Nested Dictionaries:**

- **Hierarchical Data Representation:** They allow the representation of complex data structures, such as organizational structures, configuration settings, and nested objects in APIs.

- **Grouping and Categorizing:** Nested dictionaries help to group related data together, which makes it easier to work with and access.

- **Improved Readability:** They make code more readable and structured, especially when dealing with multidimensional data, such as JSON-like objects.

- **Efficient Storage and Access:** They help in organizing data efficiently, where each dictionary within the main dictionary can hold its own set of key-value pairs.

**Basic Example of a Nested Dictionary**

A simple case where one dictionary contains another dictionary as a value.

Inside the nested dictionary 'address', we have keys like 'street', 'city', and 'zip'.


```python
person = {
    'name': 'Alice',
    'age': 30,
    'address': {
        'street': '123 Main St',
        'city': 'Wonderland',
        'zip': '12345'
    }
}

# Accessing nested dictionary values
print(person['address']['city'])  # Output: Wonderland

```

**Creating Databases with Nested Dictionaries**

 an example of storing data about multiple students, where each student has their own dictionary.


```python
students = {
    'student1': {
        'name': 'Alice',
        'age': 20,
        'grades': {
            'math': 90,
            'english': 85
        }
    },
    'student2': {
        'name': 'Bob',
        'age': 22,
        'grades': {
            'math': 80,
            'english': 88
        }
    }
}
print(students)
```

Accessing a nested Dictionary


```python
# print Student 1 nested Dict

print(students['student1'])
```


```python
# print Student 2 nested Dict

print(students['student2'])
```

Accessing a value in nested dictionary 


```python
# Accessing Bob's age
print(students['student2']['age'])  

```


```python
# Accessing the grade of Alice (student1) in Math
print(students['student1']['grades']['math']) 


```

**Configurations with Nested Dictionaries**

Nested dictionaries are often used to represent complex configuration files, like settings for a web application.


```python
config = {
    'database': {
        'host': 'localhost',
        'port': 5432,
        'user': 'admin',
        'password': 'securepass'
    },
    'logging': {
        'level': 'DEBUG',
        'log_file': '/var/log/app.log'
    }
}
print(config)
```

**Species Characteristics and Habitats**


```python
# Accessing database configurations

print(config['database']['host'])  # Output: localhost
print(config['logging']['log_file'])  # Output: /var/log/app.log

```


```python
species_data = {
    'lion': {
        'classification': 'Mammal',
        'habitat': {
            'continent': 'Africa',
            'environment': 'Savanna',
            'climate': 'Tropical'
        },
        'diet': 'Carnivore',
        'conservation_status': 'Vulnerable'
    },
    'elephant': {
        'classification': 'Mammal',
        'habitat': {
            'continent': 'Africa',
            'environment': 'Grasslands',
            'climate': 'Tropical'
        },
        'diet': 'Herbivore',
        'conservation_status': 'Endangered'
    },
    'penguin': {
        'classification': 'Bird',
        'habitat': {
            'continent': 'Antarctica',
            'environment': 'Coastal',
            'climate': 'Polar'
        },
        'diet': 'Carnivore',
        'conservation_status': 'Least Concern'
    },
    'kangaroo': {
        'classification': 'Mammal',
        'habitat': {
            'continent': 'Australia',
            'environment': 'Outback',
            'climate': 'Arid'
        },
        'diet': 'Herbivore',
        'conservation_status': 'Near Threatened'
    }
}


print(species_data)
```


```python
# Accessing specific information:
# 1. Access the habitat of the elephant
elephant_habitat = species_data['elephant']['habitat']
print(f"Elephant Habitat: {elephant_habitat}")
# Output: Elephant Habitat: {'continent': 'Africa', 'environment': 'Grasslands', 'climate': 'Tropical'}

# 2. Access the conservation status of the lion
lion_status = species_data['lion']['conservation_status']
print(f"Lion Conservation Status: {lion_status}")
# Output: Lion Conservation Status: Vulnerable

# 3. Access the diet of the penguin
penguin_diet = species_data['penguin']['diet']
print(f"Penguin Diet: {penguin_diet}")
# Output: Penguin Diet: Carnivore
```

---

**ENJOY !!**
