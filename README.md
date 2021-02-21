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
	kubectl apply -f ./mongo-service.yaml
	```
5. Query the list of Services to verify that the MongoDB Service is running:
	```shell
	kubectl get service
	```
6. Apply the backend Deployment from the  `backend-deployment.yaml`  file:
	```shell
	kubectl apply -f ./backend-deployment.yaml
	```
7. Query the list of Pods to verify that the three backend replicas are running:
	```shell
	kubectl get pods -l app.kubernetes.io/name=djangoBook -l app.kubernetes.io/component=backend
	```
8.  Apply the backend service from the `backend-service.yaml` file:
	```shell
	kubectl apply -f ./backend-service.yaml
	```
9. Query the list of services to verify that the backend service is running:
	```shell
	kubectl get services
	```
10. Then finally, Run the following command to forward port  `8080`  on your local machine to port  `80`  on the service.
	```shell
	kubectl port-forward svc/backend 8080:80
	```
### Cleaning up
Deleting the Deployments and Services also deletes any running Pods. Use labels to delete multiple resources with one command.

1. Run the following commands to delete all Pods, Deployments, and Services.
	```shell
	kubectl delete deployment -l app.kubernetes.io/name=mongo
	kubectl delete service -l app.kubernetes.io/name=mongo
	kubectl delete deployment -l app.kubernetes.io/name=guestbook
	kubectl delete service -l app.kubernetes.io/name=guestbook
	```
2. Query the list of Pods to verify that no Pods are running:
	```shell
	kubectl get pods
	```
