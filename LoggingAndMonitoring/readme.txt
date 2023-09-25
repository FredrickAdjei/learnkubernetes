Kubernetes does not come with a full-featured built-in monitoring solution.
However, there are a number of open-source solutions available today such as Metrics Server, Prometheus, the Elastic Stack,
and proprietary solutionslike Datadog and Dynatrace.

-Metrics Server.
You can have one Metrics Server per Kubernetes cluster.
The Metrics Server retrieves metrics
from each of the Kubernetes nodes and pods,
aggregates them, and stores them in memory.
Note that the Metrics Server
is only an in-memory monitoring solution
and does not store the metrics on the disk.
And as a result, you cannot see historical performance data.

Kubernetes runs an agent on each node
known as the kubelet, which is responsible
for receiving instructions
from the Kubernetes API master server
and running pods on the nodes.
The kubelet also contains a sub component
known as the cAdvisor or Container Advisor.cAdvisor is responsible
for retrieving performance metrics from pods
and exposing them through the kubelet API
to make the metrics available for the Metrics Server.

- kubectl top node - view pperformance
- kubectl top pods 


kubectl logs <podname> - logs of a pod
kubectl logs -f <podname> - -f to sream thr logs live
if there are multiple containers in a pod youll have to specifiy name of the container