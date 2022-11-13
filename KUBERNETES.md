## **KUBERNETES**
____

1. **WHAT IS KUBERNETES**
    
    This is container Orchestration tool used when our appliction is distributed in multiple containers. its job is to monitor, scale, restart containers automatically even if they are spread across multiple nodes. No manual intervention required.

1. **KUBERNETES FEATURES**
    
    - Managing Multiple containers as one entity
	- Resource usage Monitoring
	- Networking
	- Rolling update
	- Load Balancing
	- Health checks

1. **COMPONENTS OF MASTER NODE**
    
    - **Kube-ApiServer**; the main component, exposing APIs for the other master components. It validates and configures data for the api objects which include pods, services, replicationcontrollers, and others. 
	- **ETCD;** an open source distributed key-value store used to hold and manage the critical information that distributed systems need to keep running.
	- **Scheduler**; a control plane process which assigns Pods to Nodes, determines which Nodes are valid placements for each Pod in the scheduling queue according to constraints and available resources.
	- **Control Manager**; responsible for node management (detecting if a node fails), pod replication, and endpoint creation.

1. **COMPONENTS OF WORKER NODE**
	- **Kubelet**; the primary "node agent" that runs on each node responsible for facilitating communication between the control plane and the node.
	- **Kube proxy**; watches the API server for pods/services changes in order to maintain the network up to date
	- **Container runtime**; responsible for managing container images and running containers on that node

1. **HOW KUBERNETES WORK**

	Its master node relationship where the msater controls the nodes hosting containers. The master schedules containers on the nodes, monitors the node as well as the containers and also keeps a track of the logs of events that happens in the container. The workers/nodes process whatever is required in the application eg api calls.

1. **KUBERNETES ARCHITECTURE**

	The first thing to deploy in a kubernetes architecture is a pod. 
	- Pod is a container that can hold multiple containers. e.g. when you have containers 
	  that are dependent of each other; a php container that have files in another container are zipped up/coexist in a pod.
	- Deployment takes care of the number of PODs running inside kunernetes. when 
	  creating a deployment specify which image in the container you want to run and how many instances/replicas of the container you want to run. In surmmary a Deployment deploys the number of pods that you want to run and the type of image you want in the pod.
	- Service: This is an internal load balancer for all the pods that are running. It 
	  relays user requests randomly to the cluster, chanelling requests to nodes that have less traffic. The types are Cluster IP, NodePort, LoadBalancer.   
	- Ingress: this is used when you have multiple exposed services. It relays user 
	  request to the appropriate service. e.g When you have www.abc.com and www.abc.com/blog and a user is trying to access www.abc.com/blog, the job of ingress is to direct the request to the right service pointing to www.abc.com/blog.