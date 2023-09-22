Imperative and declarative are two different approaches for interacting with Kubernetes 
and managing resources within a Kubernetes cluster:

1. Imperative Commands:

Imperative commands are action-based commands that specify how to perform an operation.
They involve specifying step-by-step instructions for making changes to resources.
Imperative commands are typically more human-readable and resemble natural language instructions.
Examples of imperative commands include kubectl create, kubectl apply, kubectl edit, and kubectl delete.
eg. kubectl create deployment nginx-deployment --image=nginx

2. Declarative Configuration:

Declarative configuration involves defining the desired state of resources in a configuration file (usually YAML or JSON) and then applying that configuration to the cluster.
It focuses on specifying what the desired end state should look like, rather than the specific steps to get there.
Declarative configurations are typically stored in version control systems (e.g., Git) and are more infrastructure-as-code oriented.
Examples of declarative commands include creating or updating resources using YAML manifests with kubectl apply.
A declarative configuration might look like this:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest


Key Differences:

Imperative commands focus on specifying the actions to be taken, which can be useful for quick one-off operations or debugging.
Declarative configurations specify the desired end state, making them more suitable for managing infrastructure as code and for ensuring consistency and reproducibility.
Imperative commands are often used for quick tasks and experimentation, while declarative configurations are used for defining the desired state of resources and ensuring that state is maintained.
In practice, many Kubernetes users use a combination of both imperative and declarative approaches based on their specific needs. Declarative configuration is often favored for managing applications
and infrastructure in production environments due to its ability to capture and maintain the desired state of the cluster's resources.

Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
(This will automatically use the pod's labels as selectors)
Or
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml (This will not use the pods labels as selectors, instead it will assume selectors as app=redis. You cannot pass in selectors as an option. So it does not work very well if your pod has a different label set. So generate the file and modify the selectors before creating the service)


Create a Service named nginx of type NodePort to expose pod nginx's port 80 on port 30080 on the nodes:

kubectl expose pod nginx --type=NodePort --port=80 --name=nginx-service --dry-run=client -o yaml

(This will automatically use the pod's labels as selectors, but you cannot specify the node port. You have to generate a definition file and then add the node port in manually before creating the service with the pod.)