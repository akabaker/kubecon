Freddie Mac's Service Mesh Journey
----------------------------------

Tetrate is service mesh partner.
    * tetrate mgmt plane
Lift and shift to vmware cloud on aws (brownfield)
Greenfield, deploy to managed k8 on public cloud

Sidecar become new demarcation between app and network.

### To software defined instrastructure
The mesh abstracts common app support features into  the service platform.
SRE (sidecar reliability team lol)

### Security use cases
* Istio is critical for zero trust and micro-segmentation
* DNS aware policy
* Mutual TLS
* Security as code
* Centralized policy mgmt

(see pic)

### Availability use cases
* Moved central traffic/route rules to Istio Ingress GW/Sidecar.
    * Layer 7 policies closer to application
* Locality aware load balancing
    * K8 doesn't provide this by default
        * isitio's locality prioritized and fail-over LB feature offered options
* Autoscaling
    * Scale on telemetry of Istio sidecar (scale based on response time or number of requests)
        * by default k8 does this based on cpu/mem usage

### Brownfield Integration - goals
Mesh first, containerize next.
They did mesh first with all kinds of traffic flows.
VM -> K8
VM -> VM
LB -> VM or k8 service

#### Brownfield challeneges
Some VMs have sidecars, those that don't have app specific certs.
Service registry scatter across load balancers and vmware
(see pic)

### Lessons Learned
* Incremental adoption
    * Don't boil the ocean
    * let people opt in over time
    * Focus on things that require mimimal code change at start
        * start with observability, then mutal TLS, follwowed by routing and policy enforcement
* Don't use Root CA for the mesh
    * Intermediate CA issued per citadel
* Mesh first, containerize next
    * Use the mesh to migrate from borwnfield to greenfield
        * get the sidecar into the vm to get started
    * Enables seamless fallback to VMs during migration
    * Provides observability over all traffic in the system
* Formed a TIGER team
    * arch, dev, network, sec to create team
    * "Coach" to help devs migrate
* Plan for CI/CD integration from the start
* Abstract Istio APIs from devs
* Figure out daily support strategy
    * this is hard