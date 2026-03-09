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

---

## Interview Questions

1. **What is the difference between Abstraction and Encapsulation. **
	* Abstraction is a design-level process that hides _complexity
	* Encapsulation is an implementation-level mechanism that hides _data_ (using private fields) 
2. **What is the "Diamond Problem" in OOP, and how does Java handle it?**
   The **Diamond Problem** is an ambiguity that arises when a class inherits from two or more classes that have a common ancestor. Imagine a base class A with a method performAction(). Classes B and C both inherit from A and override performAction() with their own specific logic. If Class D were allowed to inherit from both B and C (Multiple Inheritance), and we called d.performAction(), the compiler wouldn't know which version to execute—the one from B or the one from C ?
   Java solves the Diamond Problem through a two-layered approach that prioritizes simplicity and predictability: 
	1. **Class Level: Strict Single Inheritance**
	Java strictly prohibits a class from extending more than one class. This design choice fundamentally eliminates the possibility of the Diamond Problem in the traditional sense, as there is only ever one path for state and behavior inheritance between classes.
	2. **Interface Level: Explicit Conflict Resolution (Java 8+)**
	With the introduction of Default Methods in Java 8, a class can inherit conflicting method implementations from two different interfaces. Java resolves this using the following three rules:
	* **Rule 1: Class Wins Over Interface**
		If a class extends a base class and implements an interface that both provide a method with the same signature, the implementation in the class (or its parent) always takes precedence.
	* **Rule 2: Sub-interface Wins Over Super-interface**
		If interface B extends interface A, and both have a default method, the implementation in the more specific interface (B) is chosen.
	* **Rule 3: Explicit Override (The Manual Resolution)**
		If two independent interfaces (InterfaceA and InterfaceB) provide the same default method and there is no inheritance relationship between them, the compiler will throw a Compile-Time Error. The developer must resolve the ambiguity manually by overriding the method in the subclass.
3. **What is the difference between an Abstract Class and an Interface in Modern Java?**
   Abstract classes could have state and behavior, while Interfaces could only have method signatures. Since **Java 8, 9, and 11**, this boundary has blurred, but key architectural differences remain.
	   * A class can extend only one abstract class.	A class can implement multiple interfaces.
	   * Abstract class can have instance variables (fields) to maintain state.	Interface cannot have instance variables (only public static final constants).
	   * Abstract class methods	can have any access modifier (private, protected, etc.). Interface methods are public by default (private methods allowed since Java 9).
	   * Abstrace class can have constructors.	Interfaces cannot have constructors.
	   * Abstract class provides a base for "is-a" relationships. Interface provides a contract for "can-do" capabilitie
4. **What is the "Fragile Base Class" problem?**
	   The **Fragile Base Class** problem is an architectural pitfall in OOP where modifications to a base class (superclass) unintentionally break the functionality of derived classes (subclasses).
5. **Why "Fragile Base Class" problem happens?**
	* **Tight Coupling:** Subclasses depend on the internal implementation details of the base class. 
	* **Inappropriate Overriding:** A developer changes a method in the base class to call another method, which the subclass has already overridden, leading to infinite loops or unexpected side effects.
6. **What is the solution for "Fragile Base Class" problem?**
	   Modern software engineering suggests favoring **Composition over Inheritance**. By using composition, you limit the exposure of internal logic and reduce the risk of breaking downstream components	
7. **What is the difference between Composition and Inheritance?**
	   These are two ways to reuse code and define relationships between classes.
	- **Inheritance (Is-A):**
		- Represents a strict hierarchy (e.g., `Car` **is a** `Vehicle`).
		- Achieved via the `extends` keyword.
		- **Cons:** Creates tight coupling; changes in the parent affect all children.
	- **Composition (Has-A):**
		- Represents a relationship where one class contains an instance of another (e.g., `Car` **has an** `Engine`).
		- Achieved by defining a member variable of another class type.
		- **Pros:** Flexible and decoupled. You can swap the "Engine" at runtime (Dependency Injection).
     **Senior Principle:** Always start with **Composition**. Only move to **Inheritance** if you are certain that a strict, permanent hierarchical relationship exists and that you need to take advantage of polymorphism across that specific hierarchy.