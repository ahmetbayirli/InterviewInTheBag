---
id: top_101
title: Object-Oriented Programming Principles
tags: [fundamentals, oop, interview-essential]
fun_fact: "Smalltalk was one of the first truly object-oriented languages, developed at Xerox PARC."
---

# Object-Oriented Programming (OOP) Principles 

OOP is a programming paradigm based on the concept of **"objects"**, which can contain data (attributes) and code (methods). It aims to implement real-world entities like inheritance, hiding, and polymorphism in programming. It uses classes as blueprints to create reusable, modular, and organized code, representing real-world entities. Key, foundational pillars include encapsulation, inheritance, polymorphism, and abstraction.

**Real-World Analogy:** In the real world, every object has properties, functions, and a state. Similarly, in OOP:
	- **Attributes (Properties):** Define what the object *is* (e.g., Brand, Color).
	- **Functions (Methods):** Define what the object *does* (e.g., Drive, Brake).
	- **State:** Defines the object's condition at a specific time (e.g., Current Speed, Fuel Level).
---

## 1. Encapsulation (Data Hiding)
Encapsulation is the bundling of data and the methods that operate on that data into a single unit (class). It restricts direct access to some of an object's components.

* **Key Concept:** Use `private` variables and `public` getters/setters.
* **Why?** It protects the internal state of an object from unauthorized access and keeps the code modular.
* **Interview Tip:** If asked "Why not just use public variables?", answer: *"To maintain control over data validation and protect the object's integrity (Invariants)."*

---

## 2. Inheritance
Inheritance allows a class (subclass/child) to acquire the properties and behaviors of another class (superclass/parent).

* **Key Concept:** The `extends` keyword in Java.
* **Why?** It promotes **code reusability** and establishes a "is-a" relationship.
* **Interview Tip:** Be careful with the "Diamond Problem" (multiple inheritance). Remember that Java solves this by not allowing multiple class inheritance but allowing multiple **interface** implementation.

---

## 3. Polymorphism (Many Forms)
Polymorphism allows objects of different classes to be treated as objects of a common superclass. 

**Types:**
    1. **Static (Compile-time):** Method Overloading (same name, different parameters). Multiple methods in the same class share the same name but have different parameters (type or number)
    2. **Dynamic (Runtime):** Method Overriding. A child class provides a specific implementation of a method already defined in its parent class. The method to be executed is determined at runtime based on the object type, not the reference type
    3. **Subtype Polymorphism**: A function can work with a base class interface, while the runtime ensures the correct overridden method runs for the specific subclass
**Example:** A single `Shape` interface with `draw()` implemented differently by `Circle`, `Square`, and `Triangle` classes.
 **Benefits:** 
    - **Flexibility:** Easily add new subclasses without changing existing code.
    - **Code Maintenance:** Reduces complexity by allowing generic code to handle various types.
    - **Consistency:** A uniform interface is used for different underlying forms.



---

## 4. Abstraction
Abstraction is the process of hiding the implementation details and showing only the essential features of the object. It reduces complexity, improves maintainability, and enables users to interact with objects through simplified, high-level interfaces

* **Key Concept:** `abstract` classes and `interfaces`.
* **Simplifying Complexity:** By focusing on what an object does rather than how it does it, code becomes more manageable.
* **Real-World Analogy:** A car driver uses a steering wheel and pedals (the interface) without needing to understand the intricate details of the internal engine mechanism.
* **Interview Tip:** "When to use an Interface vs. an Abstract Class?" 
    * Use **Interface** for "can-do" (behavior) capabilities.
    * Use **Abstract Class** for "is-a" (identity) relationships.
* **Abstract Classes:** These act as blueprints, restricting the instantiation of objects and enforcing structure on subclasses.
* **Interfaces:** Similar to abstract classes, these define a contract that implementing classes must follow.
* **Benefits:** Promotes modularity, enhances code readability, and facilitates easier maintenance.
* **Abstraction vs. Encapsulation:** 
	* Abstraction is a design-level process that hides _complexity
	* Encapsulation is an implementation-level mechanism that hides _data_ (using private fields) 
---

