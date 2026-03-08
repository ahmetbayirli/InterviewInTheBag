---
id: top_102
title: SOLID Design Principles
tags: [fundamentals, clean-code, architecture]
fun_fact: "The SOLID acronym was introduced by Michael Feathers, based on principles collected by Robert C. Martin (Uncle Bob)."
---

# SOLID Design Principles

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