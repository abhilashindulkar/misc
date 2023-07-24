#### Kubernetes Objects & their API version.

<details>
<summary>Refer the below table for each object's kind, apiVersion details.</summary>
<p>Source Ref: https://kubernetes.io/docs/reference</p>
</details>


kind  | apiVersion
:-------------: | :-------------:
Pod  | v1
Service  | v1
Replication Controller  | v1
ConfigMap | v1
Secret | v1
ServiceAccount | v1
Role | rbac.authorization.k8s.io/v1
ClusterRole | rbac.authorization.k8s.io/v1
RoleBinding | rbac.authorization.k8s.io/v1
ClusterRoleBinding | rbac.authorization.k8s.io/v1
ReplicaSet  | apps/v1
Deployment  | apps/v1
StatefulSet  | apps/v1
Daemonset  | apps/v1
Job  | batch/v1
CronJob  | batch/v1
PersistentVolume | v1
PersistentVolumeClaim | v1
VolumeSnapshotClass | snapshot.storage.k8s.io/v1
StorageClass | storage.k8s.io/v1
EndpointSlice  | discovery.k8s.io/v1
NetworkPolicy | networking.k8s.io/v1
Ingress  | networking.k8s.io/v1
IngressController | networking.k8s.io/v1
