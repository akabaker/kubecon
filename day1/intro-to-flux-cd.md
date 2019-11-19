Intro to Flux CD
-----------------
Flux CD and Argo CD merged.
flux-get-started repo on github

### What is GitOps
(see pic)
JuSt uSe GiT PuSh

Advantages:
* collab with pull reqs
* audit log on all changes (SOC 2 compliance)
* signed commits to prove authorship and origin
    * flux looks at approved committers and their keys

### Flux
Multi-tenancy is supported.

Flux watches for changes in repo and applies to cluster.
(see pic)

Update policies are used to define how flux should update workloads.

Flux supports Bitnami sealed secrets (encrypted files in git).

Helm Operator
* Subproject
* makes helm releses declarative 