# Introduction

* Consistent code style
  - Reduces ambiguity, complexity
  - Increases readability, productivity 
  - Is important to team work
* Code style needs to be verified
  - During development via IDE tools
  - During the CICD pipelines via CLI tools

# Choice

* The rule format chosen is **editorconfig**
  - There should preferably be a single editorconfig file
  - It could be stored in a dedicated repo and reused across multiple repos
* IDE tools are up to the engineer's **personal preference** as long as they are compliant
* CLI tool chosen is **dotnet format**
  - Doesn't support ReSharper rules
  - Rules are sufficient enough and allow *some* freedom of expression
  - Free and doesn't need tools requiring licensing

# Options

## Rules

* StyleCop .ruleset file
* ReSharper .DotSettings file
* editorconfig .editorconfig file (C# and .NET standard rules)

## IDE tools

* Visual Studio
  - Supports editorconfig rules
  - Good performance
  - Requires licensing even for Community edition in certain cases
* StyleCop
  - Supports only StyleCop rules
  - Integrates well with Visual Studio
  - Open source and free
* ReSharper
  - Supports ReSharper and editorconfig rules
  - Integrates well with Visual Studio
  - Undeserved bad reputation for performance which applies only to large projects
  - Requires licensing, but works with the cheaper personal licenses
* Rider
  - Supports ReSharper and editorconfig rules
  - Good performance, better than Visual Studio with ReSharper
  - Multi-platform
  - Additional learning curve
  - Requires licensing, but works with the cheaper personal licenses

## CLI tools

* StyleCop
  - Supports only StyleCop rules
  - Open source and free
* dotnet format
  - Supports editorconfig rules: core, .NET, C# without more advanced ones
  - Installed via `dotnet tool update --global dotnet-format`
  - Ran via `dotnet format path-to.sln --no-restore --verify-no-changes --verbosity detailed`
  - Command only reports the inconsistencies and returns an exit code > 0 if there are any issues
  - Open source and free
* JetBrains InspectCode which is part of ReSharper CLI tools
  - Supports editorconfig rules: core, .NET, C#, ReSharper
  - Installed via `dotnet tool update --global JetBrains.ReSharper.GlobalTools`
  - Ran via `jb inspectcode path-to.sln --no-build --output=output.file`
  - Requires an additional check of the output file
  - Free but requires ReSharper/Rider to create the editorconfig file

# Resources

* https://dev.to/srmagura/c-linting-and-formatting-tools-in-2021-bna
* https://editorconfig.org/
* https://github.com/DotNetAnalyzers/StyleCopAnalyzers
* https://github.com/dotnet/format
* https://docs.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/
* https://www.jetbrains.com/resharper/
* https://www.jetbrains.com/rider/
* https://www.jetbrains.com/help/resharper/ReSharper_Command_Line_Tools.html
* https://www.jetbrains.com/help/resharper/InspectCode.html
