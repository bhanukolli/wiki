# K8s 

### K8S Architecture 

[K8S Components](https://kubernetes.io/docs/concepts/overview/components/)
* Master (Control Plane) (Multiple Maters)
  * 4 Process on every master node 
    * API Server (Cluster Gateway)
      * Gatekeeper for authentication 
    * Scheduler
    * Controller Manager 
      * Detect Cluster state changes 
    * etcd 
      * Key value store of cluster state (brain...!)
* Node (Worker Machine)
  * Each node has multiple pods 
  * 3 Process must be installed on all nodes 
    * Kubelet (Intreacts with container and node )
    * Kube Proxy (Forwarding requests)
    * Container Runtime 

### K8S Basic Objects  
 * Node (Physical or Virtual Server)
 * Pod 
   * Smallest unit of K8s 
   * Abstraction over container 
   * Usually 1 application per pod 
   * Each pod gets its own IP address 
   * New IP address on re-creation 
 * Service 
   * Permanent IP address 
   * Lifecycle of pod and service are not connected 
   * Loadbalancer 
 * Ingress 
   * Route traffic into cluster 
 * ConfigMap
   * Configuration of application (Properties)
 * Secret
   * Used to store secret data (base64 encoded) 
 * Volumes 
   * Attach Physical storage 
     * Local 
     * Remote (Cloud / External storage)
 * Deployments 
   * Blueprint for pods (apps)
   * Stateless apps 
 * Statefulset 
   * Stateful apps 

### Minikube and kubectl 

* Minikube - Used for testing K8s locally 
* kubectl - Command line utility to interact with K8s clusters 

Mac install 
`brew install hyperkit` (Virtual machine)
`brew install minikube` 

 Minikube create K8s cluster 
`minikube start --vm-driver=hyperkit` 
`minikube status` 
### Kubectl commands 

```
kubectl get nodes 
kubectl get pod
kubectl get services 
kubectl create deployment <DEPLOYMENT_NAME> --image=nginx
kubectl get replicaset 
kubectl edit deployment <DEPLOYMENT_NAME>
kubectl logs <POD_NAME>
kubectl describe pod <POD_NAME>
kubectl exec -it <POD_NAME> -- bash
kubectl delete deployments <DEPLOYMENT_NAME>
kubectl get events
kubectl apply -f <FILE_NAME>.yaml
kubectl delete -f <FILE_NAME>.yaml
```
    
*Layers of abstraction* 
`Deployments` manages a Replicaset 
`Replicaset` manages a Pod
`Pod` is an abstraction of Container
`Container` 


