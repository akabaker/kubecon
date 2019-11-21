Moving Data with Vitess
-----------------------
Moving from AKS to GKE (using vitess)
 
### How cloud lock-in happens
* Provisioning
* autoscaling
* queues
* network egress

usually paying 2x cost per hour/day with hosted dbs

microsoft lol
AKS experience was bad
    * 100 node limit
    * single node type
    * disks take 30 min to mount
    * support was bad

Vitess enabled them to migrate.
    * use k8's native stuff for autoscaling, use vitess for queues and databases.

Vitess Architecture
    * (see slide)
    global topology server
    |[region]            |[region]
    topology server      topology server

Vitess used as a queue as well