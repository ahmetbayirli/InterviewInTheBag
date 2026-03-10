---
id: top_105
title: SOLID Principles
tags:
  - fundamentals
  - clean-code
  - architecture
fun_fact: The SOLID acronym was introduced by Michael Feathers, based on principles collected by Robert C. Martin (Uncle Bob).
---

# SOLID Principles

SOLID is a mnemonic acronym for five design principles intended to make software designs more understandable, flexible, and maintainable. These principles are the backbone of professional software engineering.

---
## 1. S: Single Responsibility Principle (SRP)
> "A class should have one, and only one, reason to change."

**The Core:** A class should do one thing and do it well. If a class has multiple responsibilities, they become coupled, leading to fragile designs.
- **Bad:** A `User` class that handles data validation, database persistence, and email notifications.
- **Good:** Split into `User` (Model), `UserRepository` (Persistence), and `EmailService` (Communication).

---
## 2. O: Open/Closed Principle (OCP)
> "Software entities should be open for extension, but closed for modification."

**The Core:** You should be able to add new functionality without touching existing, tested code.
- **Method:** Use Interfaces and Abstraction.
- **Example:** Instead of adding an `if-else` inside a `PaymentProcessor` for every new currency, create a `PaymentStrategy` interface. New currencies just implement the interface without changing the processor.

---
## 3. L: Liskov Substitution Principle (LSP)
> "Objects of a superclass should be replaceable with objects of its subclasses without breaking the application."

**The Core:** A subclass must fulfill the "contract" of its parent. It should not withdraw or change expected behaviors.
- **Classic Violation:** The Square-Rectangle problem. If a `Square` inherits from `Rectangle` but breaks the logic of independent width/height setting, it violates LSP.
- **Interview Tip:** "Is-a" relationship is not enough; "Behavioral Compatibility" is mandatory.

---

## 4. I: Interface Segregation Principle (ISP)
> "Clients should not be forced to depend upon interfaces that they do not use."

**The Core:** Better to have many specific interfaces than one general-purpose "Fat Interface."
- **Example:** If you have an `IMachine` interface with `print()`, `scan()`, and `fax()`, a simple printer shouldn't be forced to implement `fax()`. Split them into `IPrinter`, `IScanner`, and `IFax`.

---
## 5. D: Dependency Inversion Principle (DIP)
> "High-level modules should not depend on low-level modules. Both should depend on abstractions."

**The Core:** Depend on **Interfaces**, not **Concrete Classes**. This decouples your system components.
- **Example:** A `Notification` class should not depend on `GmailService` directly. It should depend on an `IMessageService` interface. This allows you to swap Gmail for SendGrid or SMS without changing the `Notification` logic.

---
## Interview Questions
1. How is Lyskov Substitution Principle different from simple Polymorphism?
	   Polymorphism is a language feature (how to override); LSP is a design rule (when to override). LSP ensures that the derived class is a true "subtype" that doesn't violate the caller's expectations.
2. What is the difference between Dependency Inversion (DIP) and Dependency Injection (DI)?
	   DIP is the principle (the "what" — decoupling). DI is the technique (the "how" — passing the dependency via constructor or setter). You use DI to achieve DIP.
3. Does the Liskov Substitution Principle (LSP) conflict with the Open/Closed Principle (OCP)?
	No, they do not conflict. In fact, they are complementary. While it may superficially seem like OCP (extending behavior) might lead to an LSP violation (changing behavior), they actually work together to ensure that extensions are safe and predictable.
	**The Relationship:**
		   -  OCP tells us how to organize our code so it can grow: by adding new subclasses or implementations instead of modifying existing ones.
		   - LSP tells us what those new subclasses are allowed to do: they must adhere to the contract established by the parent class.
	**Why the "Conflict" is a Misunderstanding:**
	The perceived conflict usually arises from a narrow interpretation of "extension."
	 **Violation of LSP:** If you create a subclass that changes the fundamental "contract" of the parent (e.g., a JsonStorage class that extends XmlStorage but throws an error when XML is expected), you have technically "extended" the system (adhering to OCP), but you have broken the correctness of the system (violating LSP).
	 **Harmonious Design:** To follow both, you must define the parent's contract broadly enough to be extensible. If the parent is DataStorage, then JsonStorage and XmlStorage both fulfill the contract "Store Data" without breaking the expectations of the caller.
---