Production Ready Kubernetes
---------------------------
Author: WeaveWorks (gitops model)
Slides: https://docs.google.com/presentation/d/1xuuEm3E0fryak2Yl3ej_DnplrhHi2WjVSHLxBOYBUZ4/edit#slide=id.g6b0556557b_0_0
        http://tinyurl.com/kubecon-2019-workshop
Environment: lukebakerkubecon@gmail.com (used kubernetes default config)

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

### something else
 
    