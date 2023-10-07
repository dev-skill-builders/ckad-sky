- kubectl run nginx --image nginx
    - it deploys a docker container by creating a Pod,
    - so it first creates a Pod automatically
    - and deploys an instance of the nginx Docker image.
    - the nginx image is downloaded from the Docker Hub repository.

- kubectl delete deployment nginx


- kubectl create -f pod-def.yml 


- kubectyl apply -f pod-def.yml 


- kubectl get po


- kubectl describe pod myapp-pod

##### To modify the properties of the pod
- kubectl edit pod redis


##### Get detail info on pods like Node details etc.
- kubectl get pods -o wide

##### Create the YAML definition to a file
- kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-pod-def.yaml

##### Extract the YAML definition to a file
- kubectl get pod <pod-name> -o yaml > pod-definition.yaml