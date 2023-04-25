# Introduction

Describes the typical stages of a CICD pipeline

# Preparation stage

* Version
* Verify layout

# Code stage

* Lint code
* Build code
* Testing
  - Run the automated tests
  - Create code coverage

# Quality stage

* Analyze code
* Push
  - Code analysis
  - Code coverage

# Package

* Create packages
  - NuGet
  - .NET publish
  - Docker image

# Deploy

* Push packages
  - NuGet to repository
  - .NET publish to servers
  - Docker image to repository
