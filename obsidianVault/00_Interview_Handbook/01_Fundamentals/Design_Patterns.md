---
id: top_106
title: Design Patterns
tags:
  - fundamentals
  - gof
  - interview-essential
---
# Design Patterns

Design patterns are typical solutions to common problems in software design. They are not "off-the-shelf" code, but blueprints that you can customize to solve a particular design problem.

---

## 1. Creational Patterns
*Focus: How objects are created, hiding the creation logic from the requester.*

### **Factory Method**
Defines an interface for creating an object but lets subclasses decide which class to instantiate. It promotes loose coupling by eliminating the need to bind application-specific classes into the code.
* **Real Life:** A Logistics app. A `Transport` factory creates `Truck` objects for land and `Ship` objects for sea without the client knowing the specific class.

### **Abstract Factory**
Provides an interface for creating families of related or dependent objects without specifying their concrete classes. It’s a "Factory of Factories."
* **Real Life:** A UI toolkit. A `GUIFactory` creates a `WinButton` and `WinCheckbox` for Windows, or `MacButton` and `MacCheckbox` for macOS.

### **Builder**
Separates the construction of a complex object from its representation, allowing the same construction process to create different representations. Useful when an object has many optional parameters.
* **Real Life:** Ordering a Pizza. You use a `PizzaBuilder` to step-by-step add `cheese`, `pepperoni`, and `crustType` instead of having a constructor with 20 arguments.

### **Prototype**
Creates new objects by copying an existing object (the prototype) rather than creating from scratch. This is efficient when object creation is expensive.
* **Real Life:** Cell Division. Instead of building a new cell from atoms, an existing cell clones itself to create an identical copy.

### **Singleton**
Ensures a class has only one instance and provides a global point of access to it.
* **Real Life:** A Database Connection Pool or a Configuration Manager. You only want one instance managing the connection limit for the entire app.

### **Object Pool**
Manages a cache of objects that are kept ready for use, rather than being created and destroyed on demand.
* **Real Life:** Thread Pools. Instead of spawning a new OS thread for every task (expensive), the system grabs an idle thread from the pool.

### **Dependency Injection (Modern)**
A pattern where an object receives its dependencies from an external source rather than creating them itself.
* **Real Life:** A Car doesn't build its own Engine. An `Engine` is "injected" into the `Car` at the factory, allowing the car to run with a Petrol or Electric engine interchangeably.

---

## 2. Structural Patterns
*Focus: How classes and objects are composed to form larger structures.*

### **Adapter**
Allows incompatible interfaces to work together. It acts as a wrapper between two objects.
* **Real Life:** A Power Adapter. It allows a three-prong UK plug to connect to a two-prong EU socket.

### **Bridge**
Decouples an abstraction from its implementation so that the two can vary independently.
* **Real Life:** Remote Controls. A `Remote` (Abstraction) works with any `Device` (Implementation). You can upgrade the remote features without changing how the TV works.

### **Composite**
Lets you compose objects into tree structures to represent part-whole hierarchies. It treats individual objects and compositions uniformly.
* **Real Life:** File Systems. A `Folder` can contain `Files` or other `Folders`. Both are treated as "File System Entities."

### **Decorator**
Attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.
* **Real Life:** Coffee Orders. You start with a `SimpleCoffee` and "decorate" it with `Milk`, then `Sugar`, then `WhippedCream`. Each layer adds cost and behavior.

### **Facade**
Provides a simplified interface to a large body of code, such as a class library or complex subsystem.
* **Real Life:** A Home Theater System. You press one "Movie Mode" button (Facade) which triggers the TV, Lights, Soundbar, and Netflix all at once.

### **Flyweight**
Reduces the cost of creating and manipulating a large number of similar objects by sharing as much data as possible.
* **Real Life:** Text Editors. Instead of each character storing its own font and size, they all point to a shared "Style" object for "Arial 12pt."

### **Proxy**
Provides a surrogate or placeholder for another object to control access to it (Lazy loading, Security, Logging).
* **Real Life:** A Credit Card. It is a proxy for your actual Bank Account. It controls access and authorizes the transaction without moving the physical cash immediately.

---

## 3. Behavioral Patterns
*Focus: Communication between objects and how they assign responsibilities.*

### **Chain of Responsibility**
Passes a request along a chain of handlers. Each handler decides either to process the request or to pass it to the next handler.
* **Real Life:** Automated Phone Support. "Press 1 for Sales (Handler 1), 2 for Tech Support (Handler 2)." If Sales can't help, they transfer you to a Supervisor.

### **Command**
Turns a request into a stand-alone object that contains all information about the request. This allows for parameterization, queuing, and "Undo" operations.
* **Real Life:** A Restaurant Waiter. The "Order" is a Command object. It moves from the table to the kitchen, can be queued, or cancelled.

### **Interpreter**
Defines a grammatical representation for a language and an interpreter to deal with this grammar.
* **Real Life:** Scientific Calculators. They interpret the string `(5 + 3) * 2` into a tree of operations to calculate the result.

### **Iterator**
Lets you traverse elements of a collection without exposing its underlying representation (List, Stack, Tree).
* **Real Life:** A TV Channel Remote. You press "Next" to see the next channel without needing to know the frequency or the list of all available channels.

### **Mediator**
Restricts direct communications between objects and forces them to collaborate only via a mediator object. It reduces coupling.
* **Real Life:** Air Traffic Control. Pilots don't talk to each other; they all talk to the Tower (Mediator) to avoid collisions.

### **Memento**
Allows capturing and externalizing an object's internal state so that the object can be restored to this state later (Undo).
* **Real Life:** Save Slots in Video Games. You save your progress (Memento) and can "Restore" back to that exact state if you lose.

### **Observer**
Defines a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing.
* **Real Life:** YouTube Subscriptions. When a Creator (Subject) uploads a video, all Subscribers (Observers) get a notification.

### **State**
Lets an object alter its behavior when its internal state changes. The object will appear to change its class.
* **Real Life:** A Vending Machine. Its behavior for "Push Button" changes depending on whether it's in the `NoMoneyState` or `HasMoneyState`.

### **Strategy**
Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
* **Real Life:** Google Maps. You can choose a `DrivingStrategy`, `WalkingStrategy`, or `CyclingStrategy` to get from A to B.

### **Template Method**
Defines the skeleton of an algorithm in a superclass but lets subclasses override specific steps of the algorithm without changing its structure.
* **Real Life:** Making Tea vs Coffee. The "Template" is: Boil water -> Steep/Brew -> Pour in cup -> Add condiments. Only the "Steep/Brew" step changes.

### **Visitor**
Separates an algorithm from the object structure on which it operates. It allows adding new operations to existing object structures without modifying them.
* **Real Life:** A Tax Inspector. The Inspector (Visitor) visits different Businesses (Objects) and calculates tax differently for each, without the businesses changing their internal code.

---

## 4. Architectural & Enterprise Patterns (Modern)

### **Repository**
Mediates between the domain and data mapping layers using a collection-like interface for accessing domain objects.
* **Real Life:** A Library Catalog. You ask for a book by ID. You don't care if the book is in the main hall or the basement storage (SQL or NoSQL).

### **Unit of Work**
Maintains a list of objects affected by a business transaction and coordinates the writing out of changes.
* **Real Life:** An E-commerce Checkout. You update stock, create an invoice, and deduct balance. All must succeed together or fail together as one unit.

### **Service Locator**
Encapsulates the processes involved in obtaining a service with a strong abstraction layer.
* **Real Life:** A Concierge in a Hotel. You don't find the laundry or taxi yourself; you ask the Concierge to locate the service for you.

### **Data Mapper**
A layer of mappers that moves data between objects and a database while keeping them independent of each other.
* **Real Life:** An ORM (like Hibernate). It maps your Java `User` class to a SQL `users` table row.

### **Pub-Sub (Asynchronous)**
A messaging pattern where senders (publishers) do not send messages directly to specific receivers (subscribers), but instead characterize published messages into classes without knowledge of which subscribers there may be.
* **Real Life:** Radio Broadcasting. The station broadcasts a signal. Anyone with a radio tuned to that frequency receives it.

---

# Interview Questions

1. **What is the difference between the **Observer** and **Pub-Sub** patterns?**
	   In **Observer**, the Subject maintains a direct list of its observers, and they are usually in the same memory space (synchronous). In **Pub-Sub**, there is a third-party "Message Broker" (like RabbitMQ or Kafka) between the publisher and subscriber. They never know each other exists (asynchronous).

2. **What is the difference between **Strategy** and **State** patterns?**
	   They have the same structure (a class delegating to a "behavior" object), but the **intent** differs. **Strategy** is usually set once by the client (e.g., "Use PayPal"). **State** transitions happen automatically within the object (e.g., "From Pending to Shipped").
3. **When should you use a **Builder** instead of a **Factory**?**
	   Use **Factory** when the creation is a one-step process (e.g., "Give me a Truck"). Use **Builder** when the creation involves many steps or complex configurations (e.g., "Give me a House with 4 rooms, a pool, and a garage").
4. **What is the "Gang of Four" (GoF)?**
	   It refers to the four authors (Gamma, Helm, Johnson, and Vlissides) of the 1994 book *Design Patterns: Elements of Reusable Object-Oriented Software*, which defined the original 23 patterns.
5. **Why is **Singleton** often considered an "Anti-Pattern"?**
	   It introduces global state into an application, which makes unit testing difficult (states persist between tests) and can hide dependencies between classes.
6. **How does the **Decorator** pattern follow the Open/Closed Principle?**
	   It allows you to extend the behavior of an object (Open for extension) without modifying the original class's source code (Closed for modification).
7. **What is the **Composite** pattern's primary benefit?**
	   It allows clients to treat individual objects and groups of objects identically. This simplifies code when dealing with tree structures like UI components or file systems.
8. **What is a **Facade**, and how does it differ from an **Adapter**?**
	   A **Facade** simplifies a complex interface for convenience. An **Adapter** changes an interface to make it compatible with another interface. One is for *simplicity*, the other for *compatibility*.
9. **Explain the **Bridge** pattern using an example.**
	   The Bridge pattern separates abstraction from implementation. For example, a `Shape` (Circle/Square) is the abstraction, and `Renderer` (Vector/Raster) is the implementation. You can add a `Triangle` or a `3DRenderer` without breaking each other.
10. **What is **Lazy Initialization**, and which pattern uses it?**
	Lazy initialization means delaying the creation of an object until the first time it is needed. The **Proxy** pattern and **Singleton** pattern frequently use this to save memory and startup time.

---

> [!TIP]
> **Senior Insight:** Don't "pattern-match" your code before you have a problem. Design patterns are solutions to *existing* complexity. If you apply a pattern too early, you might end up with "Over-Engineering" and unnecessary layers of abstraction.

---