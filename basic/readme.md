#start with memory size
minikube start --memory=7000


#create pod
kubectl apply -f pod.yaml


#get all pods
kubectl get pod

#describe
kubectl describe pod nginx

#get os name
kubectl get nodes -o wide

#run nginx pod
kubectl run nginx-pod --image=nginx

#What is the image used to create the new pods?
kubectl descirbe pod <pod_name> #check image name

#delete pod
kubectl delete pod <pod_name>

#get replica set
kubectl get replicaset

#why we need labels and selectors?
- 

#how to scale?
kubectl replace -f replicaset-defi.yaml

kubectl scale --replicas=6 -f replica.yaml
kubectl scale rs new-replica-set --replicas=5 

#update replicaset on running
kubectl edit replicaset <repicaset name>
 --update sepec replica

 #delete all pod
 kubectl delete --all pod  

#get all
kubectl get all
 
 #get deployment
 kubectl get deployment

#get pod deployment  details
kubectl describe deployment <myapp>

# rollout cmd
kubectl rollout status deployment/myapp-deployment

kubectl rollout history deplyment/myapp-deployment

### Deployment strategy
    - There are 5 instance running and now either
     --- can deploy by destory all and deploy all (recrate strategy)
     -- or destory and deploy one by one with zero time(rolling strategy)

    - update application by updating file and run
        kubectl apply -f deploy.yml
    or
    - update running image only
        kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1   #updating only nginz

## rolling back
kubectl rollout undo deployment/myapp-deployment

# rollout status
kubectl rollout status deployment/myapp-deployment

#delete replicaset
kubectl delete replicaset replcaset_name
#delete replicacontroller
kubectl delete rc rc_name


#scale down to zero
kubectl scale deployment replica_name --replicas=0

#getting namespace
kubectl get namespaces
kubectl get pods --all-namespaces
kubectl get replicaset --all-namespaces
kubectl get deployments --all-namespaces

#checking which namespace has pod
kubectl get pods --namespace= name_space

#get node 
kubectl get nodes.

#edit deployment file
kubectl edit deployment frontend

#What is the type of the default kubernetes service?
kubectl get service

# Networking
 - different Ip address is assigned to different POD 
 - kuberenets doesn't do networking by own while clustring
 - all containers/POds can communicate to one another without NAT
 - all nodes can commmunicate with all containers and vice-versa without NAT
 - tools can be used
    - cisco , flannel, nsx, cillium

# Services
    - unable communication
    - to access pod from laptop /outer world
    - types:
        1. NodePort
        2. ClusterIP
        3. LoadBalancer


# Microservices Architecure
