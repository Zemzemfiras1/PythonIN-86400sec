# Section 10 : Class 

## what is it !!! 
A class is a blueprint for creating objects. Objects are instances of a class, and they bundle together data (attributes) and behavior (methods) to model real-world entities.

**Syntax**
```python
class ClassName:
    # Attributes and methods go here
```

## Class's Components 

### Constructor (__init__)
The constructor is a special method that is called automatically when an object is created. It initializes the object’s attributes.


```python
class MyClass: 
    def __init__(self, name, age):
        self.name = name  # Assigning the value to self.name
        self.age = age    # Assigning the value to self.age

    def greeting(self):
        return f"Hello, {self.name}"


# Instantiate the class with the correct arguments
person1 = MyClass("Mario", 30)

print(person1.name)
print(person1.age)

# Call the greet method to see the result
print(person1.greeting())


```

### Atributes 

Attributes in a class are variables or data that are associated with a class and its objects. They are used to store information relevant to the class and its instances. Attributes can be broadly categorized as:

- Instance Attributes: Unique to each object and set in the constructor.

- Class Attributes: Shared by all objects of the class.


```python
class MyClass:
    class_attribute = "Shared by all instances"  # Class attribute

    def __init__(self, name):
        self.name = name  # Instance attribute

```

**Class Attribute:**

- Class attributes are accessed through the class itself or through any instance. However, modifying a class attribute through an instance will modify it only for that specific instance, not the class itself.
  
    - These are attributes that are shared across all instances of a class.
      
    - They are defined within the class but outside any methods.
    
    - Class attributes are accessed using the class name or an instance of the class.


```python
class MyClass:
    class_attribute = "Shared by all instances"  # Class attribute

    def __init__(self, name):
        self.name = name  # Instance attribute

# Creating instances
obj1 = MyClass("Alice")
obj2 = MyClass("Bob")

# Accessing the class attribute via the class
print(MyClass.class_attribute)  # Shared by all instances

# Accessing the class attribute via an instance
print(obj1.class_attribute)  # Shared by all instances
print(obj2.class_attribute)  # Shared by all instances

```

**Instance Attribute:**

- Instance attributes are unique to each object created from the class and can only be accessed through the instance.
  
    - These are attributes specific to an instance of a class.
    
    - They are typically defined in the __init__ method and are prefixed with self.
    
    - Each instance of the class has its own copy of the instance attributes.




```python
# Accessing the instance attribute
print(obj1.name)  # Alice
print(obj2.name)  # Bob
```


```python
# Modifying the class attribute via an instance
obj1.class_attribute = "Modified by obj1"
print(obj1.class_attribute)  # Modified by obj1 (specific to obj1)
print(obj2.class_attribute)  # Shared by all instances (not modified for obj2)
```

**Creating an Object** 

**Syntax**
```python
Object = Class_Name(Attributes)
```


```python
# Define a class
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute

    def introduce(self):  # Instance method
        return f"My name is {self.name}, and I am {self.age} years old."

# Create an object (instance of Person)
person1 = Person("BatMan", 25)


# Access attributes
print(person1.name)  # Output: BatMAn
print(person1.age)   # Output: 25
```


```python
# Call a method
print(person1.introduce())  # Output: My name is Alice, and I am 25 years old.

```

### Methods

Methods are functions defined within a class. They define the behavior of objects. Methods take self as the first argument to access object attributes.

**Instance Methods:**

    Work with an instance of the class (self refers to the instance).


```python
class MyClass:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return f"Hello, {self.name}!"

print(MyClass("SuperMan").greet())

# or Object = Class_Name(Attributes)
person = MyClass("BatMan")
print(person.greet())
```

**Class Methods:**

    Work on the class itself. Use @classmethod and the cls parameter.


```python
class MyClass:
    class_attribute = "Hello, World!"

    @classmethod
    def class_method(cls, param):
        print(f"Class Attribute: {cls.class_attribute}")
        print(f"Parameter: {param}")

# Call the class method
MyClass.class_method("Example")


```

**Static Methods:**

    Do not depend on instance or class. Use @staticmethod.


```python
class Example:
    class_attribute = "Shared"

    def __init__(self, value):
        self.instance_attribute = value

    @classmethod
    def class_method(cls):
        return f"Class Attribute: {cls.class_attribute}"

    @staticmethod
    def static_method():
        return "This is a static method"

# Usage
obj = Example("Unique Value")
print(obj.class_method())  # Output: Class Attribute: Shared
print(obj.static_method())  # Output: This is a static method

```

**Inheritance**
  
Inheritance allows a class (child class) to inherit attributes and methods from another class (parent class).


```python
# Parent class
class Animal:
    def __init__(self, species):
        self.species = species

    def make_sound(self):
        return "Some generic sound"

# Child class
class Dog(Animal):
    def make_sound(self):
        return "Woof!"

# Create an instance of Dog
dog = Dog("Canine")
print(dog.species)  # Output: Canine
print(dog.make_sound())  # Output: Woof!

```

**Encapsulation**

Encapsulation restricts access to some attributes or methods to ensure they are not modified directly.

- Use a single underscore (_) for protected attributes.

- Use a double underscore (__) for private attributes.



```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

# Create an account
account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # Output: 1500

```

**Polymorphism**

- Polymorphism allows methods to have the same name but behave differently based on the object.
  


```python
class Cat:
    def make_sound(self):
        return "Meow"

class Dog:
    def make_sound(self):
        return "Woof"

animals = [Cat(), Dog()]
for animal in animals:
    print(animal.make_sound())  # Output: Meow, Woof

```

**Example**  


```python
class Car:
    # Class attribute
    wheels = 4

    # Constructor
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

    # Instance method
    def display_details(self):
        return f"{self.year} {self.brand} {self.model}"

# Create instances
car1 = Car("Toyota", "Camry", 2020)
car2 = Car("Honda", "Civic", 2018)

# Access attributes and methods
print(car1.display_details())  # Output: 2020 Toyota Camry
print(car2.display_details())  # Output: 2018 Honda Civic

```

## Summary of Key Terms

| **Term**         | **Description**                                                               |
|-------------------|-------------------------------------------------------------------------------|
| **Class**         | A blueprint for creating objects.                                            |
| **Object**        | An instance of a class.                                                      |
| **Attribute**     | A variable that holds data for the object.                                   |
| **Method**        | A function defined in a class that operates on objects.                      |
| **Constructor**   | The `__init__` method used to initialize object attributes.                  |
| **Inheritance**   | A way to create a new class using an existing class as a base.               |
| **Encapsulation** | Restricting access to certain attributes or methods.                         |
| **Polymorphism**  | Allowing methods to have the same name but behave differently in different contexts. |


---


## ENJOY !!
