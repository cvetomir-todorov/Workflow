# Introduction

* Good code quality is foundational for
  - Engineering productivity
  - More accurate estimation
  - Team morale
* Code quality should be verified
  - During development via IDE tools
  - During the CICD pipelines via CLI tools
* Analysis should be available so that code quality is tracked

# Choice

* IDE tools are up to the engineer's **personal preference** as long as they are compliant
* CLI tool is **sonnarscanner** which integrates with SonarCloud/SonarQube
* `main` should be the default branch in SonarCloud/SonarQube
* Code coverage should also be exported and tracked

# Options

## IDE tools

* ReSharper
  - Supports ReSharper rules
  - Integrates well with Visual Studio
  - Undeserved bad reputation for perfomance which applies only to large projects
  - Requires licensing, but works with the cheaper personal licenses
* Rider
  - Supports ReSharper rules
  - Better performance than Visual Studio + ReSharper
  - Multi-platform
  - Additional learning curve
  - Requires licensing, but works with the cheaper personal licenses
* SonarLint
  - Supports Sonar rules
  - Works well with SonarCloud/SonarQube
  - Free but requires the open-source requiring SonarCloud or SonarQube license

## CI tools

* sonnarscanner
  - Supports Sonar rules
  - Works well with SonarCloud/SonarQube

# Resources

* https://www.jetbrains.com/resharper/
* https://www.jetbrains.com/rider/
* https://www.sonarlint.org/
* https://rules.sonarsource.com/csharp
* https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
* https://www.sonarsource.com/plans-and-pricing/
