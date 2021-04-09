## KubeCtl
1) Kubectl has config file in hidden folder  vi ~/.kube/config
2) This config consists of clusters, users, contexts(groups clusters and users)

## [App Deployment Workflow](./../images/app-deployment-workflow.png)

1) Source Code
2) Build into Container Image
3) Publish it to repo (Container Registry)
4) Kubernetes Manifest 
5) Post to apiserver in master