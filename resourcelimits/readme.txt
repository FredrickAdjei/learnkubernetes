Resource Types:

Resource Quotas: Resource Quotas control CPU, memory, storage, and object count (e.g., pods, services).

Limit Ranges: Limit Ranges primarily control CPU and memory limits and requests. They are used for fine-grained control over the resources allocated to containers within pods.

Enforcement:

Resource Quotas: Resource Quotas strictly enforce resource limits at the namespace level. If the quota is exceeded, new pods and objects may be rejected or fail to create.

Limit Ranges: Limit Ranges influence the resource allocation for pods but do not strictly enforce limits. Pods that exceed the defined limits are not rejected, but they may be subject to eviction by resource management mechanisms like the Kubernetes Horizontal Pod Autoscaler (HPA).


A resource quota, defined by a ResourceQuota object, provides constraints that limit aggregate resource consumption per namespace.
 It can limit the quantity of objects that can be created in a namespace by type, 
 as well as the total amount of compute resources that may be consumed by resources in that namespace.
 