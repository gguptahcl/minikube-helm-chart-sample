# This Repository has the helm charts for Docker Images  publsihed on DockerHub

### Contents of repo

Helm charts for following Docker Images
	ggupta0109/hello-world-docker
	ggupta0109/weather-service


### Setup on Minikube

-- check if this chart has not been installed previously :

helm list -a 

-- Install charts
helm install hello-world-chart --name=hello-world
helm install weather-chart --name=weather-service


-- To get the service URL 
sudo minikube service hello-world-service --url
sudo minikube service weather-service --url


### Rollbacking setup on Minikube

helm del --purge weather-service
helm del --purge hello-world


### Setup on EKS CLuster

-- check if this chart has not been installed previously :

helm list -a 

-- Install charts
helm install hello-world-chart --name=hello-world
helm install weather-chart --name=weather-service


-- To get the service URL and other details  
kubectl describe service hello-world-service
kubectl describe service weather-service


### Rollbacking setup on EKS CLuster

helm del --purge weather-service
helm del --purge hello-world


### Notes

For testing service on EKS Cluster , service type has to be LoadBalancer. This repo has hello-world service as LoadBalancer and Weather service as NodePort. 

hello-world-chart/values.yaml

service:
  type: LoadBalancer

weather-chart/values.yaml
service:
  type: NodePort

For Minikube deployment - change service type to NodePort
For EKS Cluster deployment - change service type to LoadBalancer

