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