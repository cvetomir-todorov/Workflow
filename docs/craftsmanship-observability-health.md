# Introduction

* Meaning
  - When the health checks are implemented properly
  - When k8s probes are configured properly
  - Then components would be more resilient
* Benefits
  - Components would be given the time to initialize properly
  - Components which aren't alive would be restarted
  - Components which can't handle traffic will not receive it
* Important for high-availability components

# `/healthz`

* Mandatory
* Executed manually
* Provides detailed data
  - Service data
  - Dependencies data

# `/startupz`

* Optional
* Executed by k8s when the component is started via a `startupProbe`
* Indicates whether container has initialized
  - Used when the container is starting slowly for some good reason
  - Example: component needs to load a lot of data into memory from a slow data source in order to properly function

# `/livez`

* Mandatory
* Executed by k8s regularly via a `livenessProbe`
  - Started after the `startupProbe` has succeeded, if there was any
  - Independent from the `readinessProbe` success/failure
* Indicates whether the container is alive
* If probe fails container is restarted
* Implementation
  - Should be successful if component main thread is running
  - Should not check for dependencies
* Cascading failures
  - After 1 pod fails, the others start to get overloaded and fail too
  - Timeout period should be comparable to client timeouts
  - Should have forgiving `failureThreshold` count

# `/readyz`

* Mandatory
* Executed by k8s regularly via `readinessProbe`
  - Started after the `startupProbe` has succeeded, if there was any
  - Independent from the `livenessProbe` success/failure
* Indicates whether container is ready to accept traffic
* If probe fails container is removed from the load balancer
* Implementation - should include checking dependencies availability
    - All dependencies should be checked simultaneously
    - For a URL - send HTTP `HEAD` request
    - For a DB - query `SELECT 1`
    - Internal service - call `/readyz`
* Shared dependency
    - One that is used by all pods in the deployment
    - Could break all pods in the deployment
    - Requires timeout > max response timeout for the dependency
    - May need to increase `failureThreshold` count
* Dependency not available
    - The component could return data from cache for `GET` requests
    - The component fails for `PUT`/`POST` requests
    - Response indicating degradation could be better than failure in some cases

# Resources

* https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/health-checks?view=aspnetcore-6.0
* https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks
* https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startupprobes/
* https://www.innoq.com/en/blog/kubernetes-probes/
* https://medium.com/metrosystemsro/kubernetes-readiness-liveliness-probes-bestpractices-86c3cd9f0b4a
* https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-how-to-avoid-shooting-yourself-in-the-foot/
