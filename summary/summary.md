---
marp: true
---

# Kubecon - Highlights

https://github.com/akabaker/kubecon.git

---

# Weaveworks workshop
_Slides: http://tinyurl.com/kubecon-2019-workshop_
* Deployed an application using GKE, GitHub, and Flux.
    * Configured using weaveworks cloud.
* Configured monitoring and alerting using Prometheus queries and weaveworks cloud.
* Application and cluster checklists.

---

![clusterimg](C:/Users/luke.baker/kubecon/summary/images/weave_1.png)

---

![clusterimg2](C:/Users/luke.baker/kubecon/summary/images/weave_2.png)

---

![clusterimg3](C:/Users/luke.baker/kubecon/summary/images/weave_3.png)


---

# GitOps
_https://github.com/fluxcd/flux_
* Use Git as the single source of truth
    * Changes observable/verifiable 
        * Lots of talk around 'signing' commits by verifying pgp keys
* Most primarily using Flux to pull configuration from git.
* Selling point, devs just push code.
    * Lots to unpack here.

---

![flux cd image](C:/Users/luke.baker/kubecon/summary/images/flux_1.jpg)


---

# Open Policy Agent
_https://www.openpolicyagent.org/_

* Declarative general purpose policy engine
    * Uses Rego (language), declarative
    * Evaluation engine
    * Can user X operation Y on resource Z?
* Library OR sidecar (http)
--- 

# Vitess
_https://vitess.io/_

Database clustering system for MySQL
>Vitess is a database solution for deploying, scaling and managing large clusters of MySQL instances. It’s architected to run as effectively in a public or private cloud architecture as it does on dedicated hardware. It combines and extends many important MySQL features with the scalability of a NoSQL database. Vitess can help you with the following problems:
>
>* Scaling a MySQL database by allowing you to shard it, while keeping application changes to a minimum.
>* Migrating from baremetal to a private or public cloud.
>* Deploying and managing a large number of MySQL instances.
---

# Freddie Mac - Migration
_https://static.sched.com/hosted_files/kccncna19/63/Tetrate%20-%20Freddie%20Mac%20-%20Istio%20Service%20Mesh.pdf_

Freddie Mac migrated to a service mesh before moving everything to k8

---

![freddie diagram](C:/Users/luke.baker/kubecon/summary/images/freddiemac_1.png)

---

![freddie diagram](C:/Users/luke.baker/kubecon/summary/images/freddie_2.png)

---

# High level items
* Service mesh all over the place
* Using certificates with a real tld
* Secret stores
* We have to use github or gitlab
* Prometheous
    * All over the place but not HA!!
    * Thanos is available, but takes some work
* Go through k8 the hard way

---

# Pragmatic Thoughts
_"Way back in March.."_

* Tools are changing rapidly.
* Expertise on moving targets.
* We will need team(s) to support migration and evolution of platform.
* Microsoft does not appear to be first class citizen in this realm.