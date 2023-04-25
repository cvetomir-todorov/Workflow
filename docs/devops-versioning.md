# Introduction

Describes the versioning schemes and workflow

# Scheme

* Semantic versioning
  - `MAJOR.MINOR.PATCH`
    - `MAJOR` version when you make incompatible API changes
    - `MINOR` version when you add functionality in a backwards compatible manner
    - `PATCH` version when you make backwards compatible bug fixes
  - Suitability:
    - Making easy for clients to ensure backwards compatibility
    - Releases are not related to a regular schedule
    - Libraries
    - Software having an API
    - Components in a microservice architecture
* Calendar versioning
  - Various schemes - `2022.05.28`, `2022.010.0528`
  - Suitability:
    - It is more important to know **when** a release is created rather than **how big** the changes are since the previous release
    - Releases are done on a regular schedule

# CHANGELOG

Various formats exist, more or less complex, automated or not

<details><summary>Example using semver in Markdown format and manual input</summary>

```markdown
# Unreleased

* Add feature Delta
* Fix bug 6

# 1.0.0 - 2023.11.25

* Fix bug 5
* Fix bug 4
* Add complex feature Gamma
  - Add sub-feature Gamma 1
  - Add sub-feature Gamma 2
  - Add sub-feature Gamma 3

# 0.1.1 - 2023.04.05

* Fix bug 3
* Fix bug 2
* Change feature Alpha
* Fix bug 1

# 0.1.0 - 2023.03.10

* Add feature Beta
* Add feature Alpha
```

</details>

# Version File

## .NET

* Projects resulting in assemblies deployed to production should be versioned
* Projects should import a `version.props` file in MSBuild format 
* The `version.props` file is located in `source` dir
* The `version.props` file contains the version number in `semver`

<details><summary>Example for MSBuild</summary>

`version.props` file:
```msbuild
<Project>

<PropertyGroup>
  <VersionPrefix>1.2.3</VersionPrefix>
  <AssemblyVersion>$(VersionPrefix)</AssemblyVersion>
  <FileVersion>$(VersionPrefix)</FileVersion>
</PropertyGroup>

</Project>
```

Project file for a versioned component:
```msbuild
<Project Sdk="Microsoft.NET.Sdk">

  <Import Project="../version.props" />

  <PropertyGroup>
    <TargetFramework>net7.0</TargetFramework>
  </PropertyGroup>

</Project>
```

</details>

# Resources

* https://softwareengineering.stackexchange.com/a/255201
* https://semver.org/
* https://calver.org/
* https://keepachangelog.com/
