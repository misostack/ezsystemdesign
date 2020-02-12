# System Design

> System Design is the process of defining the **<u>architecture</u>**, **<u>modules</u>**, **<u>interfaces</u>**, and **<u>data</u>** for a system to satisfy specified requirements.

!["System Design Visualization"][system_design_visualization]

## A. Design

### I. Patterns

Why design patterns is important and the main purpose of

> ### Any fool can write code that a computer can understand. Good programmers write code that humans can understand

> ### Refactoring: Improving the Design of Existing Code, 1999

> ### The goals, as always, is to have a codebase that is loosely coupled and high cohesive, so that changes are easy, fast and safe to make

- Domain Driven Design ( DDD )
- Hexagonal Architecture (HEX)
- CQRS
- Onion Architecture
- The Clean Architecture ( CA )

#### 1.1. Domain Driven Design

- Target : learn about the main concepts and apply DDD pattern in development.
- Sample project: Students tracking
- Technical stacks: PHP, Laravel, MySQL, Angular, Heroku, Vultr
- Flow: Read and understand the main concepts of DDD -> Make an app with simple MVC based on Laravel -> Then Refactoring with the design pattern that had been learned from DDD

#### Definition

- Domain : A sphere of knowledge, influence or activity. The subject area to which user applies a program is the domain of software.
- Model : A system of abstractions that describes selected aspects of a domain and can be used to solve problems to that related domain.
- Context : the setting in which a word or statement appears that determines its meaning. Statements about a model can only be understood in a context
- Bounded Context : a description of a boundary(typically a subsytem or the work of a particular team) within which a particular model is defined and applicable.
- Ubiquitous Language : A language structured around the domain and used by all team members within a bounded context to connect all the activities of team with the software.

#### Putting the Model to Work

Domain Driven Design is an approach to the development of complex software in which we:

1. **Focus on core domain**
2. **Explore models in a creative collaboration of domain practitioners and software practitioners**
3. **Speak a ubiquitous language within an explicitly bounded context**

#### Continuous Integration

> Once the bounded context has been defined, we must keep it sound.

When the number of people are working on the bounded context, there is tendency for model to fragment. The bigger team the bigger problem, but as few as there or four people can encounter serious problems.

Therefore:

> **Institute a process of merging code frequently and other implementation artifacts frequently with automated tests to flag fragment quickly**

#### Model Driven Design

> **Tightly	relating the code	to an	underlying model gives	 the code	meaning	and	makes	the	model	relevant.**

#### Hands-on Modelers

> **Any technical person contributing to the model must spend some time touching the code, whatever primary role he or she plays on the project. Anyone responsible for changing code must learn to express a model through the code. Every developer must be involved in some level of discussion about the model and have contact with domain experts. Those who contribute in different ways must consciously engage those who touch the code in a dynamic exchange of model ideas through the ubiquitous language.**

#### Refactoring Toward Deeper Insight

> **Traditionally, refactoring is described in terms of code transformations with technical motivations. Refactoring can also be motivated by an insight into the domain and a corresponding refinement of the model or its expression in code.**

### Building Blocks of a Model-Driven Design

- Layered	Architecture

#### Layered Architecture

> In an object-oriented program, UI, database, and other support code often gets written directly into the business objects. Additional business logic is embedded in the behavior of UI widgets and database scripts. This happens because it is the easiest way to make things work, in the short run.

Therefor:

- **<u>Isolate</u>** the expression of the **domain model** and the **business logic**
- **Eliminate** any dependency on **infrastructure**, **user interface**, or even **application logic** that is not business logic.
- **Partition**	a	complex	program	**into layers**
- Develop	a	design	within	each	layer	that	is	
cohesive	and	that	**depends	only	on	the	layers	below**
- Follow	standard	architectural	patterns	
to	 provide	 loose	 coupling	 to	 the	 layers	 above
- **Concentrate	all	the	code related to	the <u>domain model</u> in one layer** and **<u>isolate</u>** it from the **<u>user interface</u>**, **<u>application</u>**, and **<u>infrastructure</u>** code.
- The domain objects, free of the responsibility of displaying themselves, storing themselves, managing application tasks, and so forth, can be focused on expressing the domain model. This allows a model to evolve to be rich enough and clear enough to capture essential business knowledge and put it to work.

>> The key goal here is **<u>isolation</u>**. Related patterns, such as **“Hexagonal Architecture”** may serve as well or better to the degree that they allow our domain model expressions to avoid dependencies on and references to other system concerns

**Example**:

- UI Layer or Presentation Layer : Responsible for showing information to the user and interpreting the
user’s commands. The external actor might sometimes be another computer system rather than a human user.

==> Usually is view ( in MVC )

- Application Layer : Defines the jobs the software is supposed to do and directs the expressive domain objects to work out problems. The tasks this layer is
responsible for are meaningful to the business or necessary for
interaction with the application layers of other systems. This layer is
kept thin. It does not contain business rules or knowledge, but only
coordinates tasks and delegates work to collaborations of domain
objects in the next layer down. It does not have state reflecting the
business situation, but it can have state that reflects the progress of a
task for the user or the program

==> Usually is the controller layer ( in MVC )

- Domain Layer (aka Model Layer) : Responsible for representing concepts of the business, informationabout the business situation, and business rules. State that reflects the
business situation is controlled and used here, even though the technical
details of storing it are delegated to the infrastructure. This layer is the
heart of business software

==> Usually is model layer ( in MVC )

- Infrastructure Layer : Provide generic technical capabilities that support the higher layers:
message sending for the application, persistence for the domain,
drawing widgets for the UI, etc. The infrastructure layer may also
support the pattern of interactions between the four layers through an
architectural framework.

==> Eg: Helpers, Services like : email, sms, auth

> Some projects don’t make a sharp distinction between User Interface and Application. Others have multiple
Infrastructure layers. But it is the crucial separation of the domain layer that enables MODEL-DRIVEN
DESIGN.

==> Eg: REST APIs

### Express Model With

- Entities
- Value Objects
- Services

#### Entities

- When an object is distinguished by its identity, rather than its attributes, make this primary to its definition in the model. Keep the class definition simple and focused on life cycle continuity and identity.
- Define a means of distinguishing each object regardless of its form or history. Be alert to requirements that call for matching objects by attributes. Define an operation that is guaranteed to produce a unique result for each object, possibly by attaching a symbol that is guaranteed unique. This means of identification may come from the outside, or it may be an arbitrary identifier created by and for the system, but it must correspond to the identity distinctions in the model.

> **The model must define what it means to be the same thing**

Aka Reference Objects

#### Value Objects

> When you care only about the attributes and logic of an element of the model, classify it as a value object. Make it express the meaning of the attributes it conveys and give it related functionality. Treat the value object as immutable. Make all operations Side-effect-free Functions that don’t depend on any mutable state. Don’t give a value object any identity and avoid the design complexities necessary to maintain entities.

>> **if you can’t make a value object immutable, then it is not a value object.**

>> **if you can safely replace an instance of a class with another one which has the same set of attributes, that’s a good sign this concept is a value object.**

How to store value objects in the database?

Let’s say we have two classes in our domain model: Person entity and Address value object:

```c#
// Entity
public class Person
{
    public int Id { get; set; }
    public string Name { get; set; }
    public Address Address { get; set; }
}
 
// Value Object
public class Address
{
    public string City { get; set; }
    public string ZipCode { get; set; }
}`
```

>> **Don’t introduce separate tables for value objects, just inline them into the parent entity’s table.**

##### Refs:

- Domain Driven Design - Eric Evans ( 2003 )
- Domain Driven Design Reference - Eric Evans ( 2015 )

## References

- https://www.w3computing.com/systemsanalysis/
- https://domainlanguage.com/
- https://blog.octo.com/en/hexagonal-architecture-three-principles-and-an-implementation-example/
- https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html
- https://marcduerst.com/2019/09/22/chapter-1-my-journey-in-clean-architecture-and-domain-driven-design/
- https://edwardthienhoang.wordpress.com/2018/08/24/ket-hop-cac-mau-kien-truc-pattern-vao-trong-mot-ddd-hexagonal-onion-clean-cqrs/
- https://edwardthienhoang.wordpress.com/2018/01/26/xay-dung-he-thong-ecommerce-voi-ddd-va-cqrs/
- https://herbertograca.com/2017/11/16/explicit-architecture-01-ddd-hexagonal-onion-clean-cqrs-how-i-put-it-all-together/
- https://www.codeproject.com/Articles/555855/Introduction-to-CQRS
- https://stackoverflow.com/questions/32216408/cqrs-commands-and-queries-do-they-belong-in-the-domain
- https://blog.ndepend.com/hexagonal-architecture/
- https://hackernoon.com/applying-clean-architecture-on-web-application-with-modular-pattern-7b11f1b89011
- https://dzone.com/articles/onion-architecture-is-interesting
- https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/



## Books

- https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164

[system_design_visualization]: ./assets/images/system-design-visualization.png