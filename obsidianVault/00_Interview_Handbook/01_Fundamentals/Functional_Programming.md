---
id: top_103
title: Functional Programming
tags:
  - fundamentals
  - fp
  - interview-essential
---

# Functional Programming (FP)
Functional Programming is a declarative programming paradigm where programs are constructed by applying and composing **functions**. It treats computation as the evaluation of mathematical functions and avoids **changing-state** and **mutable data**.

---

## 1. Core Principles of FP

To master FP, you must understand these five "pillars" that differ from the traditional OOP approach:

### **First-Class and Higher-Order Functions**
Functions are "first-class citizens," meaning they can be assigned to variables, passed as arguments, and returned from other functions.
**Higher-Order Function:** A function that takes another function as a parameter (e.g., `.map()`, `.filter()`).

### **Pure Functions**
A function is "pure" if:
1. It always returns the same output for the same input.
2. It has **no side effects** (it doesn't change global variables, write to disk, or modify the input).

### **Immutability**
In FP, data does not change. Instead of modifying an existing object, you create a **new** object with the updated values. This eliminates a whole category of bugs related to "shared mutable state."

### **Declarative vs. Imperative**
**Imperative:** You tell the computer *how* to do it (loops, state changes).
**Declarative:** You tell the computer *what* you want (transformations).


---

## 2. Functional Programming in Modern Java (Streams API)

Java 8+ brought FP to the forefront of the ecosystem. Here is how we translate OOP logic into FP logic:

**The OOP Way (Imperative):**
````java
List<String> result = new ArrayList<>();
for (User u : users) {
    if (u.getAge() > 18) {
        result.add(u.getName().toUpperCase());
    }
}
````

**The FP Way (Declarative):**
````java
List<String> result = users.stream()
	.filter(u -> u.getAge() > 18) // Predicate 
	.map(u -> u.getName().toUpperCase()) // Function 
	.collect(Collectors.toList());
````

## 3. Key FP Vocabulary

- **Lambda Expression:** An anonymous function (e.g., `(x, y) -> x + y`).
- **Closure:** A function that "remembers" the environment in which it was created.
- **Currying:** Breaking down a function that takes multiple arguments into a series of functions that each take a single argument.
- **Memoization:** An optimization technique where you store the results of expensive function calls and return the cached result when the same inputs occur again.

---

# Interview Questions

1. **What is a "Side Effect" in Functional Programming?**
	   A side effect is any change in the state of the application that is observable outside the called function other than its return value. Examples include:
	   - Modifying a global variable.
	   - Modifying an argument passed by reference.
	   - Printing to the console or saving to a database.
	   - Throwing an exception. In "Pure" FP, we try to isolate side effects to the very edges of the application.
 2. **Why is Immutability important in Multi-threaded environments?**
    Immutability is the ultimate solution to **Thread Safety**. If an object cannot change after it is created, multiple threads can read it simultaneously without the risk of a "Race Condition." You don't need `synchronized` blocks or locks because there is no "shared mutable state" to protect.
3.  **What is the difference between _map_ and _flatMap_?**
	   **map:** Transforms each element in a stream into exactly one other element. **flatMap:** Used when each element in the original stream can be transformed into **another stream** (or list). It then "flattens" those multiple streams into a single stream. Analogy: _map_ is like painting every house on a street; _flatMap_ is like opening the front door of every house and bringing everyone inside out into the street.

---

> [!TIP] 
> **Senior Insight:** Don't try to make everything "Pure." In real-world systems, you need side effects to save data and show UI. The goal is to keep your **Business Logic** functional and pure, while pushing the **I/O and State** to the infrastructure layer.

---
