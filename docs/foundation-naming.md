# Introduction

Linux-based OSes, open source projects, file system, tooling (Git, Docker, Kubernetes etc.) follow to a large extent the Linux conventions, ensuring consistency and convenience (e.g. because of case sensitivity). It makes sense naming to be aligned with Linux.

The main point is that both `camelCasing` and `PascalCasing` aren't good enough for splitting words because they are case sensitive. Which leaves two popular choices. The `underscore_separation` is a good one but there are some [regex considerations](https://blog.codinghorror.com/of-spaces-underscores-and-dashes/). Which favor the `dash-separation` over it.

# Git repos

* Repo labels should be free text
  - Example: `History Consumer`, `Messenger`
  - Note: GitLab allows labels in addition to the official repo URL
* Repo URLs should be `lowercase-with-dash-separation`
  - Example: `history-consumer`, `messenger`
* Branches should be `lowercase-with-dash-separation`
  - Example: `main`, `fix-connection-timeout`, `feat-add-history-cache`
* Version tags should be exactly 3 numbers separated by dots
  - Example: `1.2.3`, `2.0.0`

# SonarCloud/SonarQube

* Since projects in SonarCloud/SonarQube are on a root level we would need a prefix - usually the name of the project
* Project display name should be free text
  - Example: `CecoChat History Consumer`, `CecoChat Messaging`
  - The name of the project here is `CecoChat`
* Project key should be `lowercase-with-dash-separation`
  - Example: `ceco-chat-history-consumer`, `ceco-chat-messaging`
  - The name of the project here is `ceco-chat`

# File system

* Directories should be named `lowercase-with-dash-separation`
  - Example: `/source/code-examples/`
* Files should be named `lowercase-with-dash-separation`
  - Example: `/docs/intro-architecture.md`
* Exceptions to these rules:
  - Directories and files specific to .NET projects (excluding solution files)
  - The standard `.gitignore`, `CHANGELOG`, `README.md`, `LICENSE` files

# CLI tools

* If we package the executable into a single file - it should be `lowercase-with-dash-separation`
  - Example: `history-consumer`
* If we use dotnet CLI in order to run it - its casing should match the standard .NET `PascalCasing`
  - Example: `dotnet HistoryConsumer.dll`
* Parameter longer version
  - Should be `lowercase-with-dash-separation`
  - Should be applied with `--`
  - Example: `history-consumer --verbose-output --debug`
  - Example: `dotnet HistoryConsumer.dll --verbose-output --debug`
* Parameter shorter version
  - Should be lowercase and 1 letter
  - Should be applied with `-`
  - Example: `history-consumer -v -d`
  - Example: `dotnet HistoryConsumer.dll -v -d`

# .NET files and directories

* Files and directories should be named after the projects and types they contain
* C# conventions document contains detailed naming conventions

# YML/YAML

* This is related to files related to Git, Docker, Kubernetes etc.
* All elements should be `lowercase-with-dash-separation`
* Exceptions:
    - TODO

```yaml
customer:
  name:
    first-name: John
    second-name: Smith
    full-name:
      - John
      - Smith
  address:
    street: 22 Harbor st.
  phone: 123456789
```
