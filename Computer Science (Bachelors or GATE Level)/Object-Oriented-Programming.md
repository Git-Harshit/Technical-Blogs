# Object-Oriented Programming (OOP)

[Object-Oriented Programming](https://en.wikipedia.org/wiki/Object-oriented_programming) is a paradigm that structures software as objects with attributes and behaviours.

## OOP concepts

* Abstraction - Hiding of complex details and displaying only the necessary top-level features.

* Encapsulation - Wrapping up of data (attributes) and member functions into a single unit of class.

* Inheritance - Taking up (adopting/inheriting) the attributes and behaviours from the Base/Parent class(es). This allows the Derived/Child class to re-use code, extend its functionality and establish a hierarchical relationship among other classes.
    - Public Inheritance: Public members of the base class remain public in the derived class. Protected members of the base class remain protected in the derived class. Private members of the base class are not accessible in the derived class.
    - Protected Inheritance: Public and protected members of the base class become protected in the derived class. Private members of the base class are not accessible in the derived class.
    - Private Inheritance: Public and protected members of the base class become private in the derived class. Private members of the base class are not accessible in the derived class.

* Polymophism - Meaning "many forms", allowing multiple forms of the method functions based upon the object it is working upon. Different forms of a function are possible by means of overloading and overriding (applicable to functions and operators).

* Hierarchy - Order of Inheritance (Single, Multiple, Multi-Level).

* Classes and Objects - A class is a blueprint/template for creating objects (a particular data structure), providing initial values for state (member variables) and implementations of behavior (member functions or methods). An object is an instance of a class.

Access specifiers of class in C++: Public, Protected, Private.

For C++ struct inheritance, default access specifier of Base struct is Public. In class inheritance, default access specifier of Base class is Private. In C, structs can not inherit. Also, C++ structs can contain member function definitions, but C does not support it directly and a function pointer may be its rough equivalent.

# Object-Oriented Analysis and Design (OOAD)

Software Development approach that models systems using objects.

## Object-Oriented Analysis (OOA)

Understanding system requirements and identifying objects, the attributes, and behaviours.

## Object-Oriented Design (OOD)

Defining the interaction of objects, structuring them into classes, and designing relationships to build the system.