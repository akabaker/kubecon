Open Policy Agent (CNCF project)
--------------------------------

Provide unified policy enforcement layer.
Started at Styra.
Incubating in CNCF.

### What is OPA
* Declartive general purpose policy engine
    * Uses Rego (language), declarative
    * Evaluation engine
    * Can user X operation Y on resource Z?
* Library OR sidecar (http)
* Has tooling to build, test, and debug
    * VS Code plugin
* Input is json, output is json
    * Service -> OPA -> query <- policy decision

### Integrations
* All of them?

### Use cases
* Admission control 
    * restrict ingress hostnames for payments team
    * ensure container images com from corportate repo
* API Authorization
    * deny test scripts access to prod services
* Data protection
    * trades exceeding 10M must be between 9am and 5pm

### Trending use cases
* Spinnaker, boomerang, terraform

### OPA Use-Case: K8 admission controller, Gatekeeper (beta stage)
(see pic)

* A customizable k8 admission webhook that helps enforce policies and stengthen governance.
* Control what end-users can do on the cluster.
* Preview effect of policy changes in prod clusters (dry-run).
* Audit capability to identify resources that are out of compliance.
* Microsoft, Google, Styra collab.
* Re-useable policies.
    * ConstraintTemplates.
    * Testable.
* Metrics -> prometheous

_DEMO_
* Example was someone spinning up a kub project, getting abandoned.
    * Admin discoverability to see if its actually used?
* Example, all namespaces must have an owner property.
* Example, find all resources in cluster that don't have resource limits.
    * Use audit results to find them.
* Prometheous data