# Table of Contents
- [SOLID principles](#solid)
- [Continous Delivery](#cd)
- [Continous Integration](#ci)

## SOLID principles <a name="solid"></a>
- **Single responsibility principle**:<br />
A class should only have responsibility over a single part of the functionality provided by the software.<br />
Consider a module that compiles and prints a report. Imagine such a module can be changed for two reasons. First, the content of the report could change. Second, the format of the report could change. These two things change for very different causes; one substantive, and one cosmetic. The single responsibility principle says that these two aspects of the problem are really two separate responsibilities, and should therefore be in separate classes or modules. It would be a bad design to couple two things that change for different reasons at different times.<br />
The reason it is important to keep a class focused on a single concern is that it makes the class more robust. Continuing with the foregoing example, if there is a change to the report compilation process, there is greater danger that the printing code will break if it is part of the same class.<br />
- **Open closed principle**:<br />
classes should be open for extension, but closed for modification. that is, such an entity can allow its behaviour to be extended without modifying its source code.<br />
A class is closed, since it may be compiled, stored in a library, baselined, and used by client classes. But it is also open, since any new class may use it as parent, adding new features. When a descendant class is defined, there is no need to change the original or to disturb its clients.<br />
Open for extension means that we should be able to add new features or components to the application without breaking existing code.<br />
Closed for modification means that we should not introduce breaking changes to existing functionality, because that would force you to refactor a lot of existing code<br />
- **Liskov substitution principle**:<br />
Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.<br />
If S is a subtype of T, then objects of type T in a program may be replaced with objects of type S without altering any of the desirable properties of that program<br />
In other words, as simple as that, a subclass should override the parent class methods in a way that does not break functionality from a client’s point of view.<br />
 - **Interface segregation principle**:<br />
A client should never be forced to implement an interface that it doesn’t use or clients shouldn’t be forced to depend on methods they do not use.<br />
Many client-specific interfaces are better than one general-purpose interface.<br />
Think about whether your abstractions are reusable and composable, and whether your objects are encapsulated and cohesive<br />
- **Dependency Inversion Principle**:<br />
Entities must depend on abstractions not on concretions. It states that the high level module must not depend on the low level module, but they should depend on abstractions.<br />
Use an adpater or interface to decouple different layers of the system.<br />
Abstractions should not depend on details. Details should depend on abstractions<br />
It means that if the details change they should not affect the abstraction. The abstraction is the way clients view an object. Exactly what goes on inside the object is not important. Lets take a car for example, the pedals and steering wheel and gear lever are abstractions of what happens inside the engine. They do not depend on the details though because if someone changes my old engine for a new one I should still be able to drive the car without knowing that the engine changed.<br />
The details on the other hand MUST conform to what the abstraction says. I would not want to implement an engine that suddenly causes the brakes to double the speed of the car. I can re-implement brakes any way I want as long as externally they behave the same way.<br />
## Continous Delivery <a name="cd"></a>
Continuous delivery (CD or CDE) is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time and, when releasing the software, doing so manually. It aims at building, testing, and releasing software with greater speed and frequency. The approach helps reduce the cost, time, and risk of delivering changes by allowing for more incremental updates to applications in production. A straightforward and repeatable deployment process is important for continuous delivery.<br />
## Continous Integration <a name="ci"></a>
continuous integration (CI) is the practice of merging all developer working copies to a shared mainline several times a day.<br />
The main aim of CI is to prevent integration problems, referred to as "integration hell" in early descriptions of XP. CI is not universally accepted as an improvement over frequent integration, so it is important to distinguish between the two as there is disagreement about the virtues of each.<br />
Another factor is the need for a version control system that supports atomic commits, i.e. all of a developer's changes may be seen as a single commit operation. There is no point in trying to build from only half of the changed files.<br />
