# Currency App

## Required projects
https://github.com/gaganichake/currency-conversion-service

https://github.com/gaganichake/currency-exchange-service

https://github.com/gaganichake/limit-service

https://github.com/gaganichake/naming-server

https://github.com/gaganichake/spring-cloud-config-server

https://github.com/gaganichake/api-gateway

https://github.com/gaganichake/git-localconfig-repo

# Docker commands

Run a docker image
Docker run -p 5000:500 project/app-name:1.0.0.RELEASE

-p : port number. {Host Posr}:{Container Port}
-d : Run the container in the background
--restart=always : Automatically Start the application container when starting docker
-m 512m : How much maximum memory you want to allocate to this container
--cpu-quota: How much CPU Quota you want to allocate tooth’s specific container. Max is 100%

View docker logs
Docker log

Show only running containers
Docker container ls

Show running containers as well as stopped containers
Docker container ls -a

Show all docker images
Docker images

Stop a running container gracefully
Docker container stop

Create tag for existing docker repository
Docker tag project/app-name:1.0.0.RELEASE project/app-name:latest

Only download the image with “latest” tag. “latest” is default tag, if not specified
Docker pull project/app-name

Search an image on Docker Hub
Docker search mysql

Show difference layers of a docker image when created
Docker image history <image ID or repository name>

Detailed in-depth information of an image
Docker image inspect <image ID or repository name>

Remove a docker image from local machine - not from registry.
Docker image remove <image ID or repository name>

Pause a running container
Docker container pause <image ID or repository name>
Docker container unpause <image ID or repository name>

Detailed in-depth information of a container
Docker container inspect <image ID or repository name>

Remove all stopped containers from local machine.
Docker container prune

Show container logs
Docker container log -f <image ID or repository name>

Stop a running container forcefully
Docker container kill <image ID or repository name>

See all events happening behind the scene in a Docker environment
Docker events

Display the running top processes of a running container - PID, Use, Time, Command
Docker top <image ID or repository name>

Show all the stats of all running container - Container ID/Name, CPU, Memory Usage/Limit, I/O, PIDS
Docker stats

See all resource being manager by docker system
Docker system df

# Kubernetes Commands

kubectl version

kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=80
kubectl get deployments (or just deployment)
kubectl scale deployment hello-world-rest-api --replicas=3
kubectl autoscale deployment hello-world-rest-api --max=10 --cpu-percent=70
kubectl edit deployment hello-world-rest-api #minReadySeconds: 15
kubectl delete deployment hello-world-rest-api 

curl http://localhost:8080/
curl http://localhost:8080/hello-world
curl http://localhost:8080/hello-world-bean

kubectl get events (or just event)
kubectl get events --sort.by=.metadata.creationTimestamp

kubectl get pods (or just pod or just po)
kubectl get pods -o wide
kubectl explain pods
kubectl describe pod hello-world-rest-api-58ff5dd898-9trh2
kubectl delete pod hello-world-rest-api-58ff5dd898-62l9d

kubectl get services (or just service or just svc)
kubectl get service --all-namespaces
kubectl delete service hello-world-rest-api

kubectl get replicasets (or just replicaset) (or just rs)
kubectl get explain replicaset
kubectl get rs -o wide

kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE

kubectl get componentstatuses

# gcloud shell and kubectl

gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105

kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080

kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get events --sort-by=.metadata.creationTimestamp

kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp

kubectl get componentstatuses
kubectl get pods --all-namespaces

kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp

kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-n6c7l

kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-8bhdt

# Working with Currency Exchange and Currency Conversion microservices

gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-c --project solid-course-258105

docker login
docker push in28min/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
docker push in28min/mmv2-currency-conversion-service:0.0.11-SNAPSHOT

kubectl create deployment currency-exchange --image=in28min/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-exchange --type=LoadBalancer --port=8000
kubectl get svc
kubectl get services
kubectl get pods
kubectl get po
kubectl get replicaset
kubectl get rs
kubectl get all

kubectl create deployment currency-conversion --image=in28min/mmv2-currency-conversion-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-conversion --type=LoadBalancer --port=8100

kubectl get svc --watch

# Using YAML for configuraton for deployment and service

kubectl get deployments

kubectl get deployment currency-exchange -o yaml >> deployment.yaml 
kubectl get service currency-exchange -o yaml >> service.yaml

(You may move all content of service.yaml at the end of deployment.yaml and delete service.yaml)
(In deployment.xml update replicas: 1 to   replicas: 2)

(You may move all content of service.yaml at the end of deployment.yaml and delete service.yaml)
(In deployment.xml update replicas: 1 to   replicas: 2)

kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml

(After executing 'apply', if you see a warnin or error, simple delete the old deployments using label)
(Labels helps you delete pods, deployments, services, replicasets all at once)

kubectl delete all -l app=currency-exchange
kubectl delete all -l app=currency-conversion

kubectl apply -f deployment.yaml

kubectl logs currency-exchange-9fc6f979b-2gmn8
kubectl logs -f currency-exchange-9fc6f979b-2gmn8 

# Using ConfigMap YAML for environment variables

kubectl create configmap currency-conversion --from-literal=CURRENCY_EXCHANGE_URI=http://currency-exchange
kubectl get configmap
kubectl get configmap currency-conversion -o yaml >> configmap.yaml

(You may move all content of configmap.yaml at the end of deployment.yaml and delete configmap.yaml)

watch -n 0.1 curl http://34.66.241.150:8100/currency-conversion-feign/from/USD/to/INR/quantity/10

# Rollout history

docker push in28min/mmv2-currency-conversion-service:0.0.12-SNAPSHOT
docker push in28min/mmv2-currency-exchange-service:0.0.12-SNAPSHOT
<<<<<<< HEAD
=======

kubectl rollout history deployment currency-conversion
kubectl rollout history deployment currency-exchange
kubectl rollout undo deployment currency-exchange --to-revision=1

# Auto Scaling

kubectl autoscale deployment currency-exchange --min=1 --max=3 --cpu-percent=5 
kubectl get hpa (Horizontal Pod Autoscaler)
kubectl top pod
kubectl top nodes
kubectl delete hpa currency-exchange
kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml
>>>>>>> origin/master

kubectl rollout history deployment currency-conversion
kubectl rollout history deployment currency-exchange
kubectl rollout undo deployment currency-exchange --to-revision=1

# Auto Scaling

kubectl autoscale deployment currency-exchange --min=1 --max=3 --cpu-percent=5 
kubectl get hpa (Horizontal Pod Autoscaler)
kubectl top pod
kubectl top nodes
kubectl delete hpa currency-exchange
kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml
