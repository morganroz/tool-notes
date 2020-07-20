# Object Oriented Programming in Python

- [Concepts](#concepts)
<!-- - [Tutorial](#course-notes) -->
- [Resources](#resources)

## Concepts

#### class vs. instance attributes  

- Instance attribute
	- Variable belonging to one *object* 
	- Defined inside of the constructor
- Class attribute
	- Variable belonging to a *class*
	- It is shared between all objects of that class
	- Defined outside of the constructor
	- Can be accessed as a class property as well as an instance property

#### public vs. private attributes  

- Public attibute
	- All members in a python class are public by default
	- Can be accessed in the class methods and outside of the class
- Protected attribute
	- Prefix the variable with an underscore (```self._name```)
- Private attribute
	- Only available for the members of the class and not outside of the class
	- Prefix the variable with two underscores (```self.__name```)
	- Any attempt to touch the variable will result in an AttributeError
	- This isn't truly private, though, and there are ways to access it

#### class vs. instance methods  

- Instance methods
	- Take ```self``` as a parameter which points to the object
	- Can freely access attributes and methods on the same object
	- Can also access the class itself through ```self.__class__``` attribute and modify the class state
- Class methods
	- Decorate with ```@classmethod``` to flag it
	- Take ```cls``` as a parameter that points to the class
	- Can't modify an object isntance state but can modify the class state which applies to all instances of that class
- Static methods
	- Decorate with ```@staticmethod``` to flag it
	- Don't take ```self``` or ```cls```, so they can't change an instance or the class
	- Mainly used as a way to namespace your methods
	- Work like regular functions but belong to the class's and every instance's namespace

#### public vs. private methods

- Private methods
	- Only accessible from within the class
	- Used to hide the inner functionality from the outside
	- Prefix the method with a double underscore.
- Public methods
	- Accessible outside of the class


#### inheritance vs. composition  

- Inheritance
	- Models an 'is a' relationship
	- A subclass is derived from/extends a super class
- Composition
	- Models a 'has a' relationship
	- Allows you to add an object to another object

<!-- ## Tutorial Notes

Encapsulation: bundling data with code operating on it  
Class: blueprint for objects that outlines states and behaviors  

attribute call: obj.attr  
method call: obj.method()  

#### Class Creation

```help(object)``` gives you information on that object and the methods/attributes it has (if in docstring).

##### Basic Example
```python3
Class myClass:
	
	def class_method(self, new_attr):
		print("My attribute is " + new_attr)

# to create some objects
c1 = myClass()
c1.class_method("My Attribute")
```

```self``` is like ```this``` in C++ and should be the first argument in any class method.

Calling something like, ```c1.class_method("My Attribute")``` actually means ```myClass.class_method(c1, "My Attribute")```.

##### Adding an attribute to a class
```python3
Class myClass:
	
	def set_name(self, name):
		self.name = name

# to create some objects
c1 = myClass()
c1.set_name("Morgan")
```

To add a -->

## Resources

1. [Real Python](https://realpython.com/python3-object-oriented-programming/)
2. [Python Documentation](https://docs.python.org/3/tutorial/classes.html)
4. [GeeksforGeeks](https://www.geeksforgeeks.org/private-methods-in-python/)
3. [Code Fellows](https://codefellows.github.io/sea-python-401d4/lectures/inheritance_v_composition.html)

