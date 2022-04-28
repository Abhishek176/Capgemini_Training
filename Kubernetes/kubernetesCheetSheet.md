```
kubectl get pod : To list all the pods
kubectl run <pod_name> --image=<image_name> : To create the pod
kubectl describe <resource_type> <resource_name> :  To describe any resourse
kubectl get <resource_type> -o wide : To check the wide output
kubectl get <resource_type> <resource_name> -o yaml : To check the details about the resource in yaml format
kubectl get <resource_type> <resource_name> -o json : To check the details about the resource in json format
kubectl delete <resource_type> <resource_name> : To delete the specific resource
kubectl apply -f pod.yml : To create kubernetes resource in declarative way
kubectl delete -f pod.yml : To create kubernetes resource in declarative way
kubectl exec <pod_name> -- <command> : To run any command inside the pod
kubectl exec <pod_name> -c <container_name> -- <command> : To run any command inside the pod if it is a multi container pod
kubectl logs <pod_name> -f : TO check the logs of container if it is a single contianer pod
kubectl logs <pod_name> -c <container_name> -f : TO check the logs of container if it is a multi contianer pod
kubectl delete <resource_type> --all : TO delete all resource of specific type
kubectl delete all --all : To delete all resource
kubectl run myapp --image=nginx --dry-run=client : To dry run
kubectl run myapp --image=nginx --dry-run=client -o yaml > <file_name>.yml : To create resource from command line
kubectl exec -it <pod_name> -- bash/sh/ash : To go inside the container
kubectl exec -it <pod_name> -c <container_name> -- bash/sh/ash : To go inside the container if it is a multi container pod
kubectl get pod -w : To run kubectl get pod command in watch mode
kubectl get <resource_type> --show-labels : TO check the labels
kubectl edit <resource_type> <resource_name> : To modify the resource

# Label
kubectl label <resource_type> <resource_name> key=value : To attach label to any resource
kubectl label --overwrite <resource_type> <resource_name> key=value : To overwrite the label
kubectl label <resource_type> <resource_name> key- : To remove the label
kubectl get pod -l app=myapp : list all the pod who has app==myapp label
kubectl delete pod -l app=myapp : TO delete pod who has app==myapp label

#Replication Controller
kubectl get rc : To list the replication controller
kubectl describe rc <rc_name> : To check the details of replication controller
kubectl delete rc <rc_name> : To delete the replication controller
kubectl delete rc <rc_name> --cascade=orphan : To delete replication controller without deleteing the pods
kubectl edit rc <rc_name> : To modify the replication controller
kubectl scale rc <rc_name> --replicas=<no_of replicas> : To scale the replication controller

# ReplicaSet
kubectl get rs : To list the replicaset
kubectl describe rs <rs_name> : To check the details of replicaset
kubectl delete rs <rs_name> : To delete the replicaset
kubectl delete rs <rs_name> --cascade=orphan : To delete replicaset without deleteing the pods
kubectl edit rs <rs_name> : To modify the replicaset
kubectl scale rs <rs_name> --replicas=<no_of replicas> : To scale the replicaset

# Deployment
kubectl create deploy myapp --image=nginx : To create deployment
kubectl get deploy :  To list the deployment
Kubectl describe deploy <deployment_name> : To describe the deployment
kubectl scale deploy <deployment_name> --replicas=<no_of replicas> : TO scale the replicas
kubectl rollout history deploy <deployment_name> : To check the revision details of the deployment 
kubectl rollout status deployment <deployment_name> : To check the rollout status
kubectl rollout undo deploy myapp-deploy : To rollback to previous revesion
kubectl rollout undo deploy myapp-deploy --to-revision=<revision_no> : To rollback to specific revesion
kubectl rollout history deploy myapp-deploy --revision=<revision_no> :  To check the change made in the specific revesion

# service
kubectl expose <deployment/rs/rc/pod> <deployment/rs/rc/pod_name> --type=ClusterIP/NodePort/LoadBalancer --port=<service_port> --target-port=<backend_pod_port> --name=<service_name> : To cerate service in imperative way

# Ingress
kubectl get ing : To list the ingress 
kubectl describe ing <ingress_name> : To describe the ingress
kubectl delete ing <ingress_name> : To delete the ingress

# namespace
kubectl create ns <namespace_name> : To create the namespace
kubectl get ns : To list the namespaces
kubectl config set-context --current --namespace <namespace_name> : To mark some namespace as default

# configmap
kubectl create cm cm1 --from-literal=key1=value1 --from-literal=key2=value2 : To create configmap
kubectl create cm cm2 --from-file=<filename> : To create configmap from file

# Taints and toleration
kubectl taint node <node_name> key=value:Effect<NoSchedule/PrefferNoSchedule/NoExecute> : To apply taint to node
kubectl taint node <node_name> key- : To remove taint from node

Kubectl top node : To monitor the cpu and memory usages of the node
Kubectl top pod -n <namespace_name> : To monitor the cpu and memory usages of the pod in specific namespace

# Volume
kubectl get pv : To list the persistent volumes
kubectl describe pv <pv_name> :  To describe the persistent volume
kubectl delete pv <pv_name> : To delete the persistent volume
kubectl get pvc : To list the persistent volume claim
Kubectl describe pvc <pvc_name> : To describe the pvc
kubectl delete pvc <pvc_name> : To delete the persistent volume claim
kubectl get sc : To list the storage class
kubectl describe sc <storageclass_name> : To describe storage class

kubectl cordon <node_name> : To make node as unschedulable
kubectl uncordon <node_name> : To make node as schedulable
kubectl drain <node_name> : To drain the node

# Helm
helm repo add stable https://charts.helm.sh/stable" : To add the repository
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo list : To list the repository
helm list : To check what charts you have instaled using helm
helm history <installation_name> : To check the history of chart installation
helm uninstall <installation_name> : To uninstall the chart
```
