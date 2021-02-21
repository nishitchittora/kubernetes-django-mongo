## Kubernetes Django Deployment with Mongo DB

Demo deployment of Mongo DB with Django using K8s

### Steps to follow
1. Take a clone of repository
	```shell
	git clone https://github.com/nishitchittora/kubernetes-django-mongo.git
	```
2.  Apply the MongoDB Deployment from the `mongo-deployment.yaml` file:
	```shell
	kubectl apply -f ./mongo-deployment.yaml
	```
3. Query the list of Pods to verify that the MongoDB Pod is running:
	```shell
	kubectl get pods
	```
4. Apply the MongoDB Service from the following  `mongo-service.yaml`  file:
	```shell
	kubectl apply -f
	```
5. Query the list of Services to verify that the MongoDB Service is running:
	```shell
	kubectl get service
	```
