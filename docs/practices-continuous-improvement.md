# Introduction

Describes practices to continuously improve quality of the end result, the project and codebase, the team

# Knowledge sharing

* Tech-talks on general and on specific technical topics
* Mentoring focused on improvements
* Pair-programming to share practices and productivity tips
* Code reviews to spread domain and technical knowledge

# PR

* Each PR should leave the codebase in a state no worse than before
* Achieved via code reviews (subjective) and measured via code quality tools (objective)
  - Example: SonarCloud/SonarQube quality gate, code duplication %, code coverage %, number of issues, tech debt time etc.
* Code quality metrics thresholds
  - Positive (e.g. code coverage) should be gradually increased
  - Negative (e.g. tech debt time) should be gradually decreased

# Technology

* On a predefined period of time (6 months) or on a number of sprints (e.g. each 10) there should be time reserved for checking changes and opportunities for improvement regarding:
  - Main technologies -. NET runtime, Base Class Library, C# etc.
  - 3rd party libs - NUnit, FluentAssertions, FluentValidation etc.
  - Tooling - OS, IDE, code quality tools etc.
  - Data storage and integration systems - databases, caching, message brokers
  - Operations - Docker, Kubernetes
  - TODO add other
* Checking and suitability assessment should lead to stories for implementing the necessary changes
  - Caring for the codebase, tooling, principles, technologies is caring for the end result
  - Stakeholders should be aware of that
  - Software engineers should be empowered to make the decisions about software engineering!
* Upgrading to the next version of .NET should be considered and realistically achieved each 12 months
  - Security patches are increasingly important in the current security-sensitive context
  - .NET LTS versions have shorter cycles: ~3 years for .NET 6
  - Making small upgrades regularly is more efficient than big upgrades less frequently
  - Improves engineer productivity, happiness, hire-ability
