# Introduction

* Using consolidated set of libraries makes codebase consistent and knowledge of the team concentrated
* Sometimes it makes sense to use 2 different libraries for the same thing
  - Example: EF could be the default choice for working with SQL database, combined with ADO.NET for specific use cases

# Dependency injection

* [Autofac](https://autofac.org/) - the most popular DI container, suitable when the built-in .NET DI container is not enough

# Logging

* [Serilog](https://serilog.net/) - the most popular
* [NLog](https://github.com/NLog/NLog) - second most popular

# Automated testing

* [NUnit](https://nunit.org/) - has better documentation than xUnit
* [FluentAssertions](https://fluentassertions.com/) - most widely used assertion library

# Observability

* [OpenTelemetry specification](https://github.com/open-telemetry/opentelemetry-specification) - the specification for OpenTelemetry, useful when making custom instrumentation
* [OpenTelemetry .NET](https://github.com/open-telemetry/opentelemetry-dotnet) - the main .NET technologies
* [OpenTelemetry .NET contrib](https://github.com/open-telemetry/opentelemetry-dotnet-contrib) - .NET technologies contributed by the community
* [Health checks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) - a very extensive list of health checks ready to be used

# Other

* [FluentValidation](https://docs.fluentvalidation.net/) - more extensible than DataAnnotations
* [IdGen](https://github.com/RobThree/IdGen) - Snowflake ID generator
* [Fody](https://github.com/Fody/Fody) - weaver for .NET assemblies
