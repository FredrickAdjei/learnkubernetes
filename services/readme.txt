e's a brief description of each:

NodePort Service:

A NodePort service exposes a service on a specific port of each node in the cluster.
It allocates a static port on each node, and any traffic sent to this port is forwarded to the corresponding service.
NodePort services are typically used when you need to expose a service to the external world.
They are often used in combination with Ingress controllers to route traffic to the appropriate services within the cluster.
ClusterIP Service:

A ClusterIP service exposes a service on an internal cluster IP address.
It is accessible only within the cluster, making it suitable for inter-service communication.
ClusterIP services are often used when services need to communicate with each other within the cluster.
LoadBalancer Service:

A LoadBalancer service exposes a service using a cloud provider's load balancer.
It automatically provisions a load balancer, such as an AWS Elastic Load Balancer or an Azure Load Balancer, and directs traffic to the Pods of the service.
LoadBalancer services are used when you need to expose a service to the internet or an external network, and you want to distribute traffic across multiple nodes in a cloud-native way.



The port on the Pod where the actual web server

is running is 80, and it is referred to as the target port

because that is where the service

forwards their request to.

The second port is the port on the service itself.

It is simply referred to as the port.

Remember, these terms are from the viewpoint of the service.

The service is, in fact, like a virtual server

inside the node.

Inside the cluster it has its own IP address,

and that IP address is called the ClusterIP of the service.

And finally, we have the port on the node itself

which we use to access the web server externally,

and that is as the node port.

As you can see, it is set to 30,008.

That is because node ports can only be in a valid range

which by default is from 30,000 to 32,767.

