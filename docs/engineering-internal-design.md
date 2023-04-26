# Introduction

Describes principles about how a component should be designed internally in the language being written

# Simplicity

* Prefer clarity and readability achieved via a simpler design
* Avoid providing extensibility hooks which aren't needed in the near future
* Avoid using predefined project structure which is over-engineered and/or contextually inappropriate
* As long as design doesn't become overcomplicated follow the [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) principles
  - Avoid the **O**pen-closed principle
* Use complex Design patterns only when necessary

# Project organization

* Each dir should be treated as a package
  - When at least one type from package A uses a type from package B, then there is a dependency A -> B
  - There shouldn't be circular dependencies between packages
  - Exceptions:
    - Entity Framework `DbContext` which requires circular dependencies in certain project organization
* Merge packages A and B when
  - Types in package B are only used in package A
  - All clients of packages A and B use always both packages
  - There is no other package that uses only package A or only package B

# Refactoring

* A major practice used in order to have code as simple as possible
* Allows moving from the simplest design possible to a bit more complex design, but only when immediately needed, not before

# Dependency injection

* Stimulates loose coupling
* Allows concurrent development
* Enables and makes it easy to use component, module, class tests

# DDD

* Aggregates
