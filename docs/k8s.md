## Basics

Kubernetes workloads aren’t network-visible by default. You make containers available to the outside world by creating a service. Service resources route traffic into the containers within pods.

A service is an abstract mechanism for exposing pods on a network. Each service is assigned a type—either ClusterIP, NodePort, or LoadBalancer. These define how external traffic reaches the service.


### Cluster IP:

* This is the default service type that exposes the service on a cluster-internal IP by making the service only reachable within the cluster.
* A Cluster service is the default Kubernetes service. It gives you a service inside your cluster that other apps inside your cluster can access.
* There is no external process.

![image](https://user-images.githubusercontent.com/1982362/206649571-ac8e59b1-6f70-49cf-bbee-a364e62dcf6a.png)

#### When to use Cluster IP?
* There are a few scenarios where you would use the Kubernetes proxy to access your services.
* debugging your services, or connecting to them directly from your laptop for some reason
* Allowing internal traffic, displaying internal dashboards, etc.


### Node Port:

* This exposes the service on each Node’s IP at a static port. Since a ClusterIP service, to which the NodePort service will route, is automatically created. We can contact the NodePort service outside the cluster.
* A Nodeport service is the most primitive way to get external traffic directly to your service.
* NodePort, as the same implies, opens a specific port on all the Nodes (the VMs), and any traffic that is sent to this port is forwarded to the service.

![image](https://user-images.githubusercontent.com/1982362/206649598-b968bb43-75bc-42f7-a793-aebe6ad91df4.png)

#### When to use Node Port?
* There are many downsides to this method
* You can only have one service per port
* You can only use ports 30,000-32,767
* If your Node/VM IP address change, you need to deal with that
* For these reasons, I don’t recommend using this method in production to directly expose your service. If you are running a service that doesn’t have to be always available, or you are very cost-sensitive, this method will work for you. A good example of such an application is a demo app or something temporary.



![image](https://user-images.githubusercontent.com/1982362/206658333-60676ca8-4734-46a5-ad83-396082169da8.png)

