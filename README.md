# 1. Agile: Driven Design and Development
## 1.1 Agile
In software development, agile is a paradigm/philosophy to design and driven development of softwares.
We are going to identify somes key words relevent to our experience:
`DevOps`: Combination of software development and IT operation means continous delivery (CD). For me it not an agile method but a complement since delivery operation is include in the driven of software development as same in the team. 
`Scrum`: Manage Workflow
`Increment`: CI, BDD, DDD, User Story, Epic
`Iteration`: Sprint, Planing, Review, Refinement, Retrospective, Refactory 
`Collaboration`: Team (PO, Scrum Master, Dev, Designer, Tester etc.)

By experience, `Design` and `Development` are notables operations to drive production of software in agile method scrum. Let us explore concepts used to implement these two operations.
## 1.2 Design Patterns
* Object-oriented analysis and design: 
it exploits the concepts as `Entity`, `Aggregate`, `Encapsulation`, `Composition`, `Methode`, `Object`, `Polymorphism` etc. Bref higher architectural level.
* Aspect-oriented design: 
Introduce concept of `cross-cutting concerns` such as security, transaction management, logging to increase modularity and letting them focus purely on the business logic.
* [Model Driven Design](https://www.todaysoftmag.com/article/1529/model-driven-design-theory-to-practice): It describes what a Conceptual Model is and how it is linked with the Problem Model/Domain Model/Business Model/Data Model etc.
* [Domain Driven Design](http://www.infoq.com/minibooks/domain-drivendesign-quickly): It is a pattern which support on 3 principles. 

(1)Focus on the core domain and domain logic. That's means an area of concern from the problem called `Problem Domain`. Eg: Banking, Agriculture, Manifacture etc. 

(2)Design on a model of the domain. That's means create a model which is deeply rooted in the domain. That is done by splitting the problem it into sub-problems, depending on the concerns. This is done by extracting all the key concepts of the sub problems and linking them together.

(3)Collaboration between software specialists and domain experts to iteratively refine a conceptual model that addresses particular domain problems in order to create a good model.

A common architectural solution for domain-driven designs contain four conceptual layers:
1. User Interface(Presentation Layer)

Responsible for presenting information to the user andinterpreting user commands.

2. Application Layer

This is a thin layer which coordinates the applicationactivity. It does not contain business logic. It does not hold the state of the business objects, but it can hold the state of an application task progress.

3. Domain Layer 

This layer contains information about the domain. This is the heart of the business software. The state of business objects is held here. Persistence of the business objects and possibly their state is delegated to the infrastructure layer.

4. Infrastructure Layer

This layer acts as a supporting library for all the other layers. It provides communication between layers, implements persistence for business objects, contains supporting libraries for the user interface layer, etc.

## 1.3 Development Patterns
* Object-oriented programing: It is programming pattern preceded by analysis, design and modeling. All base on object-oriented paradigm.
* Aspect-oriented programming: It is modulary programming pattern which add additional behavior to existing code without modifying the code itself.
* Test Driven Development: Software development process relying on business requirements being converted to test cases before development. It promotes software development by repeatedly testing the software against all test cases.
* [Behavior Driven Development](https://en.wikipedia.org/wiki/Behavior-driven_development): It emerged from TDD and combines the general techniques and principles of OOP and DDD. The particularity for BDD is that business requirements are translated into functional/feature testing case as human-readable text by non-technical team members (QA/Test, Bunsiness Analysis, PO, Domain Experts).

# 2.Behavior Driven Development
