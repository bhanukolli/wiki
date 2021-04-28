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
```
minikube start --vm-driver=hyperkit
minikube status
minikube service serviceName # To expose service externally 
```
### Kubectl commands 

```
kubectl get nodes 
kubectl get pod
kubectl get pod -o wide 
kubectl get all 
kubectl get services 
kubectl create deployment <DEPLOYMENT_NAME> --image=nginx
kubectl get deployment <DEPLOYMENT_NAME> -o yaml 
kubectl get replicaset 
kubectl edit deployment <DEPLOYMENT_NAME>
kubectl logs <POD_NAME>
kubectl describe pod <POD_NAME>
kubectl exec -it <POD_NAME> -- bash
kubectl delete deployments <DEPLOYMENT_NAME>
kubectl get events
kubectl apply -f <FILE_NAME>.yaml
kubectl delete -f <FILE_NAME>.yaml
kubectl get namespace/ns
```
    
*Layers of abstraction* 
`Deployments` manages a Replicaset 
`Replicaset` manages a Pod
`Pod` is an abstraction of Container
`Container` 

### K8S Configuration File 
* Metadata 
* Specification 
* Status (Desired State Vs Actual State) - Automatically added by K8s 
  
### K8s Namespace 
Virtual cluster inside of Main cluster   
* kube-system
  * System process 
  * DO-NOT Create / Modify anything in system 
* kube-public
  * Publicly accessible data
  * a configmap, which contains cluster information 
* kube-node-lease
  * heartbeats of nodes 
  * each node has associated lease object in namespace 
  * determines the availability of a node. 
* default 
  * resources we create are located here

```
kubectl create namespace <NAME>
kubectl get namespace/ns 
kubens <NAMESPACE> # External utility to set default namespace (Need to install)
```

Why ?

Dont's
1. Everything in one namespace 
2. Conflicts : Many teams using same application name 

Do's 
1. Resources grouped in namespace 
   1. Database / Monitoring / Logging / Teams 
2. Resource sharing btwn environments (Staging / dev)
3. Resource sharing : Blue/Green deployments 
4. Access and Resource Limits on namespaces 

You can't access most of the resources from another namespace. 
  Ex: configmap / secrets 
Services can be shared between namespaces 
Global components `kubectl api-resources --namespaced=false `
  * Volumes
  * Node 

Components created are by default in default namespace, 
### Misc
Basic encryption of text using base64 
`echo -n 'text' | base64` 
