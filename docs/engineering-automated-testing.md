# Introduction

Describes the automated testing process and guidelines

## Tests should be runnable

* Locally against the project
* From the CLI of the CICD pipeline

## Team members primary responsibilities

* [Write code] -> [Run tests] development loop should be as fast as possible
* Software engineers should not wait test engineers to run the tests
* Software engineers should not wait for the CI pipeline to run the tests (with some exceptions maybe)
* Software engineers should be able to run tests locally **while writing new code**
* Test-first approach is critical when striving to achieve regression-capable tests

Therefore:

* Software engineers should write and support the test automation infra
* Software engineers should make the infra as data driven as possible
* Test engineers should aid in test design, main scenarios, specific test cases
  - Take full advantage of the data-driven nature of the infra
  - Write test input (e.g. a file, database)
  - Write expected output (e.g. a file, database)

## What to test

* **Behavior** is the main thing which should be tested
* Additionally:
  - Performance
  - Security
  - TODO add other

# On what level to test

* There are different approaches in terms of the level
* Depending on the definition of unit - every test could be a unit test
  - **E2E** test means the unit is the whole solution with all components, or maybe limited to the components which the current team is responsible for
  - **Component** test means the unit is a whole component (service/command line app/library/etc.), accessible via its API (RESTful API/CLI/object-oriented API/etc.)
  - **Module** test means the unit is one part of the component (of few/several/many), e.g. 10-20-30 types working together for some domain logic (e.g. complex financial calculation), authentication, data access etc.
  - **Class** test means the unit is a single class with (some of) its methods

## Comparison between different units

|                                   | Component tests                                                      | Module tests                                                                | Class tests                                                             |
|-----------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Amount of code to write initially | About 1x or 1.5x the production code                                 | About 1x the production code                                                | About 2.5x or 3x the production code at 90% code coverage               |
| Amount of support needed          | Much less since it focuses on a very stable API                      | Less since it focuses on a relatively stable API                            | Much more since each change in class interaction means fixing the tests |
| Test doubles                      | Very small need, manually written, don't require a mocking framework | Small need, manually written, don't necessarily require a mocking framework | Very big need, often requires on a mocking framework                    |
| Achieve 90% code coverage         | May be challenging                                                   | May have some challenges                                                    | Easy, could achieve close to 100%                                       |
| Cover specific use cases          | May be challenging                                                   | May have some challenges                                                    | Easy                                                                    |
| Test feedback when code breaks    | Not very precise                                                     | Relatively precise                                                          | Very precise                                                            |
| Test infrastructure needed        | Heavier and more elaborate, but can be reused for same dependencies  | Relatively light, but rarely reused                                         | Relatively right, revolving around mocking                              |
| Set up external dependencies      | Challenge to setup and isolate - file system/API/broker/DB/etc.      | Not so challenging, depends on the external dependency                      | Easy via a mocking framework                                            |

E2E unit is very similar to Component unit but requires more components to be brought up. 

## Guidance what unit to choose

* In practice for a lot of projects **class** tests aren't created or don't cover anywhere near 90%+ of the production code
  - That's partly because of the initial amount of time needed
  - Even if they are created, they often end up being commented out, ignored or deleted because it's **extremely** time consuming to support them
* The preferred way of testing should be **component** tests and/or **module** tests.
  - If the component doesn't have too deep paths starting from its entry points and if it isn't too challenging to set up external dependencies then **component** tests are more time efficient
  - On the other hand if better feedback is required and if there are challenges achieving the desired code coverage **module** tests can be used
  - As exceptions and challenges arise **class** tests may be the last resort only for **isolated units** depending on how critical the code is, or some other good reason

# Resources

* My own experience using TDD since 2007 and training other people to do it
* [Ian Cooper](https://mvp.microsoft.com/en-us/PublicProfile/8975?fullName=Ian%20Cooper) talk about [doing TDD the right way](https://www.youtube.com/watch?v=EZ05e7EMOLM)
