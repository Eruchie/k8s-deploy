## **KUBERNETES JOTs** ##
___

- If storageClass has allowVolumeExpansion set to false, extending the persistent volume will not be possible
 - If PVC is deleted is the corresponding PV also deleted? It depends on the reclaim policy. If the reclaim policy is set to retain then it wont be deleted if PVC is gone. if reclaim police is set to delete, PV will be deleted.
 - If my ETCD is down will it impact on existing application? It wont impact on existing application. If we restart/delete a pod then it will impact application pods. Pods will not be recreated automatically after restart or reboot because etcd is down.
 - If Scheduler is down will it impact on existing application? No it wont. If scheduler is down then no new pods will be created. 
 - I have done some changes on config Map but still it is not reflecting in application pods? It will reflect after we restart the pod.
 - Images are present on container Registry but still I am getting image pull Off error on Application Logs 
 - What is Cordon and Drain? Cordon i will mark a node as unschedulable while Drain makes it unschedulable and evicts the pods. 
 - I am trying to create a pod but its stuck in pending state, how do I fix the issue?
 - A pod keeps having crash loop back OFF Error? What are the reasons and how do we fix this issue?
 - What is the diff btw Kubernetes and docker swarm? DS is a default container orchestration tool that comes with Docker. DS is used to ochestrate simple docker containers While K8s is used to manage more complex app containers. Kubernetes offer support for larger/complex demand pdtn enviroment and also have integrated tools for monitoring. DS cannot auto scale, has no GUI, requires 3rd party tools for logging and monitoring and cannot rollback deployed rolling updates
 - What is Heapster? helps us do container cluster monitoring.
 - What is kubelet? A service agent that controls and maintains a set of pod specs throgh kubernetes API server. it also maintains the POD lifecycle ensuring a given set of containers are all running. The kublet runs on each node and ensures communication between the master and slave nodes. Pod specs; infomation/ all about a pod
 - kubectl is k8s cmd line tool used for deploying managing creating updating and inspecting resources in k8s.... its a cmd line tool for interacting in k8s.
 - What are the different services within k8s? Cluster Ip service; a load balanced IP address in which one/more pods matching the same label selector can foward traffic to. This is an internal service only. Node Port Service; exposes the services of each node on a static port, Load Balancer Service; exposes the services externally using the LB of the cloud provider. External Name; a special type of service without selectors but uses DNS names instead. 
 - How to set a static IP for K8s LB? Whenever K8s master assigns a new IP address, it can be assigned on the LB by changing the DNS record
 - What is ETCD? this is a distribution key-value store for k8s data which includes metada and config data and allows nodes in k8s clusters to read write data. it reps the state of a cluster at a specific time. 
 - Can you use many claims out of a persistent volume? No; The mapping between persistent volume to persistent volume claim is 1:1
 - How do you deploy a feature with zero downtime in K8s? You can apply a rolling update to ensure no downtime
 -  What is the diff btw replication controllers and replica sets? Replication controllers are obsolete and do not have selectors. replication sets have selectors in their spec, the selectors help you select different types of services 
 - What is a kube-proxy: runs on all the node and it is responsible for directing traffic to the right container based on the IP and port number of incoming requests 
 - What is a headless service? This service enables you directly reach a pod without accessing it through a proxy.
 - What is PVC? Persistent Volume Claim, It is a requested storage used by k8s for pods. the claim should be created in the same namespace where the POD resides. name space is used to segregate the cluster into different parts so that there wont be conflict betwween teams.
 - What are the different components of a Kubernetes architecture? two main components are the master and the worker node. 
 Master node has API server; used in managing and controlling the cluster. Controller manager; responsible for regulating the cluster in k8s. Scheduler; responsible in scheduling tasks in the worker node. ETCD; stores all the information of what the current cluster looks like.  
 Worker node has kublet, kube-proxy, pods
 - If you have to pass a sensitive information in your cluster how would you do it? We can pass sensitive information in k8s using secrets. Secrets can be created through a yaml file. Most orgs use secrets to pass sensitive info like username and password. 
 - What is sematext docker agent? it is a log collection agent with events and matrics, it runs as a small container in each docker host. These agents gather metrics events & logs for all cluster nodes and containers.
 - if you delete a pod (created as part of deployment) what happens to the information inside of it? Deployment will make sure that the new pod is created to maintain the number of replicas. But it all depends on the volume mount used if you want info retained then use a persistent volume.
 - Is there any pattern to pods being assigned to nodes? can you make sure a pod gets scheduled to a particular node? When a pod is created it spawns automatically to any node, scheduled by k8s to manage work load and resources, but if you want to spawn a pod on a particular node, it can be done through taints.
 - If a K8s job should finish in 20secs and it takes 5mins, how can you make sure to stop the application if it exceeds 40secs? When we create a job spec, we can assign  --activeDeadlineSeconds flag to the command, this flag relates to the duration of the job, once the job reaches the treshold specified, it will terminate. 
 
 Performing a rollback
 List all revisions of a DaemonSet; kubectl rollout history daemonset <daemonset-name>
 Roll back to a specific revision
 
 Namespaces are a way to organize clusters into virtual sub-clusters — they can be helpful when different teams or projects share a Kubernetes cluster.