Production Ready Kubernetes
---------------------------
Author: WeaveWorks (gitops model)
Slides: https://docs.google.com/presentation/d/1xuuEm3E0fryak2Yl3ej_DnplrhHi2WjVSHLxBOYBUZ4/edit#slide=id.g6b0556557b_0_0
        http://tinyurl.com/kubecon-2019-workshop
Environment: lukebakerkubecon@gmail.com (used kubernetes default config)

###The Kubernetes production ready checklist
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
