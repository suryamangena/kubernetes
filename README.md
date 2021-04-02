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

## [Architecture](images/k8-architecture.png)

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