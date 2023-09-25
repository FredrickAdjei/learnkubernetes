Manual Scheduling
So if there is no scheduler to monitor and schedule nodes,
what happens? The pods continue to be in a pending state.
Well, without a scheduler, the easiest way to schedule a pod
is to simply set the 'NodeName:' field to the name of the node
in your pod specification file while creating the pod.
The pod then gets assigned to the specified node.
You can only specify the node name at creation time.

-What if the pod is already created

and you want to assign the pod to a node?
Kubernetes won't allow you to modify
the node name property of a pod,so another way to assign a node to an existing pod
is to create a binding object and send a POST request
to the pod's binding API,
thus mimicking what the actual scheduler does.
In the binding object, you specify a target node
with the name of the node,
then send a POST request to the pod's binding API
with the data set to the binding object in a JSON format.
So you must convert the YAML file
into its equivalent JSON form.

Po-bind-definition.YAML
apiVersion: v1
kind: binding
metadata: 
   name; NGINX
target:
   apiversion: v1
   kind: Node
   name: node02

   Convert the YAML or JSON representation of the Binding object to its equivalent JSON form. For example, you can use the kubectl command to do this:
   'kubectl convert -f my-pod-binding.yaml --output=json > my-pod-binding.json'
Send a POST request to the Pod's binding API using curl or another HTTP client, providing the JSON representation of the Binding object as the request data:
'curl -k -H "Content-Type: application/json" -X POST --data @my-pod-binding.json http://<kubelet-node>:10255/pods/<namespace>/<pod-name>/binding/'
Replace <kubelet-node> with the address of the node where the Pod is currently running, <namespace> with the Pod's namespace, and <pod-name> with the name of the Pod you want to move.