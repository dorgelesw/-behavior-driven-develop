# 1. Agile: Driven Design and Development
## 1.1 Agile
In software development, agile is a paradigm/philosophy to design and driven development of software.
We are going to identify some keywords relevant to our experience:
`DevOps`: Combination of software development and, IT operation means continuous delivery (CD). For me it not an agile method but a complement since delivery operation is include in the driven of software development as same in the team. 
`Scrum`: Manage Workflow
`Increment`: CI, BDD, DDD, User Story, Epic
`Iteration`: Sprint, Planing, Review, Refinement, Retrospective, Refractory 
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

Responsible for presenting information to the user and interpreting user commands.

2. Application Layer

This is a thin layer which coordinates the application activity. It does not contain business logic. It does not hold the state of the business objects, but it can hold the state of an application task progress.

3. Domain Layer 

This layer contains information about the domain. This is the heart of the business software. The state of business objects is held here. Persistence of the business objects and possibly their state is delegated to the infrastructure layer.

4. Infrastructure Layer

This layer acts as a supporting library for all the other layers. It provides communication between layers, implements persistence for business objects, contains supporting libraries for the user interface layer, etc.

## 1.3 Development Patterns
* Object-oriented programing: It is programming pattern preceded by analysis, design and modeling. All base on the object-oriented paradigm.
* Aspect-oriented programming: It is modular programming pattern which add additional behavior to existing code without modifying the code itself.
* Test Driven Development: Software development process relying on business requirements are converted to test cases before development. It promotes software development by repeatedly testing the software against all test cases.
* [Behavior Driven Development](https://en.wikipedia.org/wiki/Behavior-driven_development): It emerged from TDD and combines the general techniques and principles of OOP and DDD. The particularity for BDD is that business requirements are translated into functional/feature testing case as human-readable text by non-technical team members (QA/Test, Business Analysis, PO, Domain Experts).

# 2.Behavior Driven Development
Behavior Driven Development or BDD illustrates the methods of developing a feature or user story based on its behavior.
The behavior is basically explained in a simple language which can be understood by all the collaborators – both technical and non-technical people (Dev, Ops, QA, PO, BA, Expert) to write feature requirements, constraints and, test scenarios.

## 2.1 Standard approach to conduct BDD
![Standard approach to conduct BDD](../bdd-workflow.png)
## 2.1.1 Collaborators
The collaborators explain and provide the feature/business requirements, acceptances criteria of the user stories as test cases for verification of system behavior. 
The key element in this layer is `feature file` which describes the feature requirements in natural human language.
We will use the syntax called [Gherkin](https://cucumber.io/docs/gherkin/) base on the pattern `Given-When-Then` for feature definition.
* `Given` - Sets the scene and initialises what objects needed for test.
* `When` - Think like action or activity you perform.
* `Then` - Think like comparing your expected results with application results.

## 2.1.2 Testing Tools
To develop application with the pattern BDD need to use a test framework tools to write, execute and automate tests. Developers build test logic in program code and map to each statement in the feature files to form automated test cases.
We can use the popular tool [Cucumber](https://cucumber.io/docs/cucumber/) to bind feature files and program code and run the test cases.

## 2.1.3 Target Application
The target application run normally as black box side of user. A testing tool send requests to the application and get responses. Then, build and send test report to collaborators.

## 2.2 How to implement BDD Approach?
They are many tools available for implementing BDD. 
* Cucumber
* Fitnesse
* Concordion
* JBehave
* Spec Flow

We will use `Cucumber` for java and `Spring Framework` in our case. To do this, we must describe a Problem and its potential implement Solution.

## 2.2.1 Problem
Online library:
* A visitor can access the platform and do searches.
* Only subscribers can read a book online or borrow a book.
* A subscriber cannot borrow more than 3 books.
* The search can be simple or advanced.

## 2.2.2 Configuration
We are going to separate unit tests to integration tests and bdd tests.
* Unit Test: we just use Junit 5 to test some method of a bean.
* Integration Test: We use Spring Boot Test with its own configuration to test a component which depends on many beans.
* Acceptance Test: We use Cucumber for java to run acceptance criteria define in feature file as Gherkin syntax.

Let us give a particular attention on Cucumber configuration. As our design is based on DDD, we will have a configuration by a domain.
Let us define XXX as a domain. We will have:
* **CucumberSpringConfig**: Cucumber glue class to load spring context configuration.
* **ContextResetHook**: To reset spring context configuration using `Scenario hooks` (Before, After etc.) at various points in the Cucumber execution cycle.
* **AbstractStepDefinition**: The main cucumber and spring boot test configuration to run steps definitions of features of a domain.
* **XXXCucumberHook**: it used to set up typically a spring context of components of a domain using `Scenario hooks` at various points in the Cucumber execution cycle.
* **XXXCucumberTestRunner**: To configure cucumber runner of features for a domain.
* **XXXTestConfig**: Spring test configuration of components.