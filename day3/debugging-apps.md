Debugging
---------

k8 not golden hammer (of course)
The more you know of k8, the less you know  : )

### Section 1, Cluster Design
(controller -> etcd -> workers) live in multiple AZ
Design condsiderations
What is your core compentency?
    * can you do it right?

EKS gives you control plane and data plane.

K8 master node components
    * api server, controller manager, scheduler, etc

ETCD 
    * 3 minimum servers
    * uses raft protocol

Worker node components
    * kubelet
    * kube-proxy (pods -> nodes)
    * container runtime

ekscutl is amazon's kubectl

### Section 2, Networking
Number 1 source of failures

Eks uses amazon-vpc-cni
    * runs on top of ENI (elastic network interface)
Worker nodes and pods get IP address from VPC

Be aware of max IPs per node.

_No more than 100 pods per node._

#### Section 2.2, CoreDNS
Uses Corefile for configuration
    * can be edited by editing coredns configmap

_Recommend two replicas of coredns running_
_add logging to coredns configmap_
_memory recommended in MB: (pods + services)/1000 + 54_

Autopath plugin
    * Do not recommend enabling by default unless having problem with external name resolution

### Section 3, Kubectl
Uses conf file in ~/.kube/config
    * potentially multiple clusters in each section
