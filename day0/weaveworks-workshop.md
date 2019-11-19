Production Ready Kubernetes
---------------------------
Author: WeaveWorks (gitops model)
Slides: https://docs.google.com/presentation/d/1xuuEm3E0fryak2Yl3ej_DnplrhHi2WjVSHLxBOYBUZ4/edit#slide=id.g6b0556557b_0_0
        http://tinyurl.com/kubecon-2019-workshop
Environment: lukebakerkubecon@gmail.com (used kubernetes default config)
https://cloud.weave.works/

### The Kubernetes production ready checklist
* Liveness and readyness
    * allows k8 to restart or stop traffic to pod
* Metrics
    * app level stuff 
* Dashboards
    * grafana
* App runbook
    * 04:00 WTF guide
* Limits and requests
    * resouce allocation for pods
    * limits are eval at runtime
    * requests at scheduling
    * priority classes are available
* Labels and annotations
    * metadata, can be used as filter in kubectl (for humans)
* Alerts
    * _Alerts should link to dashboard and playbook_
* Structured Logging
    * Avoid logging to files
    * log to stdout is easiest probably
* Tracing
    * Opentelemetry?
    * opentelemetry.io
    * Tracer, appdash, jaeger
    * Don't trace everything
* Graceful shutdowns
    * respond to SIGTERM
    * this is how k8 will tell application to end
* Graceful deps
    * Readyness probe (keeps crash loop from happening)
    * _Exponential backoff with jitters_
* ConfigMaps
    * Prefer file based configuration over ENV vars
        * allows config to be versioned
    * Configmap as a volume is easiest option (when configmap file changes, update config by listening for file change)
        * For reconfig without rebuild
* Labeled images using commit sha
    * Label docker images with code commit sha
    * tracing image to code
    * ${branch}-${hash}
* Lockdown runtime context
    * Init contanier to configure (has more privs), then app containers have less privs

### Cluster checklist
* Deployment pipeline (inf automation)
    * seperate from build pipeline
    * flux?
* Build pipeline
    * build artifact
* Image registry
    * security scanning here
    * creds for push and pull
* Monitoring inf
    * prometheus has service discovery with k8
        * hard to run two prometheus boxes
        * _use Cortex and Thanos (open source). Cortex is CNCF and supports multi-tenancy_
    * routing alert and triggers
* Shared storage
    * size and performance before choosing
* Secrets management
    * hashicorp vault
    * bitnami sealed secrets (is fav)
* Routing traffic
    * Ingress controller
        * can do logging and authentication, but that may be better on api gateway
    * API Gateway
        * can replace ingress controller (higher layer ingress controller)
        * _Ambassador (envoy) is k8 native_
    * Ingress Security (WAF)
        * AWS waf, nginx mod-security, cloudflare
        * This would be better as someone else's problem
    * Service Mesh
        * may not be needed,
        * tracing without instrumentation
        * service to service tls
        * fine grained traffic policies, but lots of complexity
    * Network policies
        * in massive flux
        * rules on allowed connections
        * service mesh alone isn't sufficient
        * Need a CNI plugin
            * Weave Net, Calico, Cillium
* Identity and Permission (Authx) integration
    * Use Role, clusterole, rolebinding
    * integration with auth providers
* Image scanning
    * Scan container images
    * Define security policy, then automate it.
    * Docker, Sync, Twistlock. Most container registries do this out of the box
        * hard part is the outcome of the results
    * distroless (reduce size of images)
* Network security (IPS/IDS)
    * For on-prem
    * Try and make someone else's problem
    * Falco, Caylent, Capsule8
* Log Aggregation
    * _What would you do with a 'right to be forgotten request'?_
* ETCD Backup
    * Some stuff is only in etcd and not in config registry
    * Velero
* Pod Security Policies
* Cluster runbooks
    * Same as app runbook but for cluster
    * lifecycle doc
* Secure ETCD
    * hosted platform is win
* HA masters
    * multi-master setup so we can keep controlling cluster
    * _Azure doesn't have multi-master node_
* Service catelogue/broker
    * For app team, preconfigured modules (chart repo)

### Installing thing on cluster (weave cloud?)

### Monitoring with Prometheus
Slides: https://docs.google.com/presentation/d/1mjnPkuWRd0EJ6WMb8KXGvfXdt8mNg-8iBuuEDifYAMA/edit#slide=id.g65bd4f844c_0_486
Metrics pyramid

Struggles with ephemerial workloads
    * Push gateway
    * Prom is pull based

Prom typicall performs service discovery

RED metrics
    * Request, errors, delays

http://apdex.org (code SLO to metric)

prom doesn't impose schema

### GitOps
Slides: https://docs.google.com/presentation/d/1Yin8AfWCvk-vuaPUNORlBI5Q4Zr2FouzHeDQMGoR8V0/edit#slide=id.g62f6d660e6_0_31
Git|imagerepo -> agent -> k8

blue/green + dark deploy (traffic mirror?)


### arch
Independent control and tenant clusters
(ops owns control cluster) -> tenant clusters spun up

rebuilding k8 clusters often is an emerging pattern


### security
TLS On control plane
Etcd is where secrets and state live.
Firewall etc so it's only accessed by master nodes
Go through "Kubernetes the hard way"

RBAC role gets bound to user, group or service account (roleBinding)

Auth users with external provider

check perms
`kubectl auth can-i create pod`

PodSecurity Polices
    * works with selinux