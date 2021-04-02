# kubernetes
Kubernetes addresses the management challenges of containers. It is orchestrator of microservices apps.

## Cluster
Cluster is made up of one or more masters and bunch of nodes. 

## Master
    -Software runs in master called as Control plane
    -Never deploy application without having multi-master H/A control plane 
    -3 Masters are suggested to have in cluster
    -If has any trouble, 5 masters are suggested
    -For example, 3 masters, in this 1 will be leader and other will be followers, if leader goes down other followers come together to elect new leader among them
    -[Run business apps in nodes and leave masters for control plane operations](images/master-business-app.png)

## Nodes
Nodes do the work 

## Pods
K8 needs cotainer to be wrapped in pods. Scaling and self healing needs pods wraped inside the deployment.

## [Architecture](images/K8-architecture.png)

## Kube-apiserver
    - Frontend to the control panel 
    - Exposes the API(REST)
    - Consumes JSON/YAML

## Cluser Store
    -Persists cluster state and config
    -Based on etcd no sql database
    -Performance is critical

## Kube controller manager
    -Controller of Controllers
        a) Node Controller
        b) Deployment Controller
        c) Endpoints/EndpointSlice controller
    -Watch loops
    - Reconciles(match) observed state with desired state

## Kube-scheduler
    -Watches API server for new work tasks
    -Assign work to cluser nodes
Note: [Refer to sanpshot](images/scheduler-controller.png)

## [Kubelet](images/kubelet.png)
    - Main kubernetes agent that run on every node 
    - Registers node with cluster, watches api server on the master for the new work assignments
    - Report back to master and maintain state of clusters and running apps
    - kubelet don't how to run containers

## [Container runtime](images/container-runtime.png)
    -Can be Docker
    -Pluggable: Container Runtime Interface (CRI)
        - Docker, containerd, CRI-O, Kata

## [Kube-proxy](images/kube-proxy.png)
    -Networking Component
    -Pod IP Address-> it assign unique ip address to the pod 
    -If pod has multicontainers all the containers will get single ip and if we want to reach each individual containers. Proxy use light weight load balancer to manage

## Virtual Kubelet
    -No nodes
    -Pods run on cloud's hosted container backend

## [Declarative Model & Desired State](images/state.png)
    -Describe the end/desire state in a manifest file. Manifest file is a description what it has to look like and it is not a long list of commands to achieve desire state.
     Long list of commands is called as imperative method
    -Post that manifest file to the apiserver in master and its upto kubernetes to do whatever it is necessary to get end state

## Pods
Kubernetes can only runs containers within pods, containers without pods are not eligible to run in kubernetes
[Pod is a shared execution envrionment (network, memory, volume )](images/pods-loosely-tightly.png)
[Never scale by adding more containers to a single mod, instead add more pods for scaling](images/pods-scaling.png)