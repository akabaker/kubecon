How to Backup and Recover Your Kubernetes Cluster
-------------------------------------------------
Velero, restric, rook, noobaa

### What is Valero
velero.io
* backup and restore tool for k8
    * DR
    * data migration
    * Data protection

* extends k8 API
* `kubectl get pod mypod -o yaml`, then storing together ina 'backup'
* It uses PVs
    * uses their snapshot API
    * if filesystem, uses 'restric'.
* Requires object storage (s3 compatable)
    * noobaa, minio are OSS

### What is Rook?
CNCD incubation project, a storage operator
Extends k8 with operators and custom types
* Implements Operator Pattern
* Defines desired state for storage resource
* Operator runs reconciliation loops to watch and apply changes

### What is Noobaa?
multicloud gateway for object storage
mirror across multiple clouds or on-prem via bucket class definition

### demo
Backup workflow is wordpress app with db and PV
Backup is dumped to s3 endpoint via noobaa
