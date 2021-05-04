# A Brief Summary of SOLID Principles 
## (based on the course created by Steve Smith - [ardalis.com](https://ardalis.com/))


## S*OLID - SRP - Single Responsibility Principle: Each software module should have one and only one reason to change.
### SRP violation symptoms: 
Low cohesion of a class, i.e. certain class members (fields, properties,
methods etc.) can be splitted into groups that process tasks of different types, e.g. logging and
authentication. Each task type has its own “axis of changes”. As a consequence, the more “axises of
changes” a class has the more often its source code is going to be changed.
### Solution: 
Keep classes small, focused and testable. Strive for high cohesion - all class members
should be engaged with one another in order to process tasks of a certain type. If class members can
be divided into loosely related groups, provided that each group processes tasks of a different type,
this may be a good reason for splitting the class into smaller, cohesive classes that would
encapsulate each group of fields, properties, methods etc. to process tasks of only one type. Strive
for loose coupling - avoid "new" inside a class, "new" is glue.


## SO*LID - OCP - Open/Closed Principle: Software entities (classes, modules, functions etc.) should be open for extension, but closed for modification.
### OCP violation symptoms: 
A class has a hard coded logic for processing the tasks that will highly
likely need new functionality in the future, i.e. an “axis of changes” is in place. In such a situation it is
easier to introduce bugs into a class as you tend to modify its source code over and over again.
### Solution: 
Method parameters that extend method’s logic, inheritance (create virtual method inside a
base class and override this virtual method inside a subclass), programming technique called
“Dependency Injection” or DI, C# extension methods, such design patterns as: Decorator, Proxy,
Strategy, Visitor. Strive for loose coupling - avoid "new" inside a class, "new" is glue. Implement new
features with new classes rather than modifying existing classes.


## SOL*ID - LSP - Liskov Substitution Principle: Subtypes must be substitutable for their base types.
### LSP violation symptoms: 
Type checks with “is” or “as”, null checks or NotImplementedException
exist within polymorphic code, meaning the code that should work with either base type or its
subtype.
### Solution: 
When inheriting a base type, ensure base type’s invariant (rules that are always true for the
type) are enforced in a subtype. Follow the “Tell, Don’t Ask” principle, meaning don’t “Ask” instances
for their type and then conditionally perform different actions, but instead, encapsulate that logic in the
type itself and “Tell” it to perform an action. Use Null Object design pattern to create a substitutable
NullObjectType that implements all interface members of a given base type.


## SOLI*D - ISP - Interface Segregation Principle: Clients should not be forced to depend on methods they do not use.
### ISP violation symptoms: 
Large interfaces with lots of members. NotImplementedException is used
for partial implementation of a larger interface. Client code uses just a small subset of a larger
interface.
### Solution: 
Let your client code define an interface it needs. When designing a type, prefer a small,
cohesive interface to a large, “fat” one. Split large interfaces into small, cohesive ones where possible
and then inherit those small interfaces in a larger original interface to avoid breaking changes. In case
a large interface is controlled by a third-party library or SDK and it is impossible to change its source
code, use such design patterns as: Adapter, Bridge, Fasade.


## SOLID* - DIP - Dependency Inversion Principle: High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.
### DIP violation symptoms: 
Direct use of low-level dependencies (e.g. database, file system, email
sending/receiving, web API hosting/consuming, configuration settings, system clock) in high-level
code (more abstract code that encapsulates business rules and is process-oriented rather than
detail-oriented). Usually, DIP violation will take the form of static calls and creating instances of
low-level classes inside high-level classes using “new” keyword. DIP violation causes: tight coupling,
difficulties with isolation and testing, code duplication.
### Solution: 
Most classes should depend on abstractions, not implementation details. Use an
abstraction instead of concrete implementation and pass it to a class constructor as a dependency.
DIP often goes hand-in-hand with the programming technique called “Dependency Injection” or DI,
that is when dependencies get “injected” as constructor parameters, properties, or method
parameters. A constructor injection is the most preferable option, because it follows Explicit
Dependencies Principle, meaning that a class should explicitly require its dependencies through its
constructor. This approach allows leveraging an IOC (Inversion of Control) container to construct
types. Strive for loose coupling, "new" is glue.
