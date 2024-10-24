This guide outlines the steps to install and set up the necessary components for deploying a application using Docker Desktop with Kubernetes, 
along with monitoring tools Prometheus and Grafana, and a CI/CD pipeline using GitHub Actions.

step:1 
	Install and setup up docker desktop on machine.
	Enable Kubernetes in the Docker Desktop settings.

step:2 
	Created self-hosted CI/CD pipeline on Github action.
	This project utilizes a pipeline to automate builds and deployments the application.
	self-hosted runner run on windows

step:3
	Building docker images for backend and frontend 
 
step:4 
	deploy the frontend 
	kubectl apply -f frontent-deploy.yml
	kubectl apply -f frontend-svc.yml

step:5 
	deploy the backend
	kubectl apply -f backent-deploy.yml
	kubectl apply -f backent-svc.yml

step:6 
	deploy MongoDB 
	kubectl apply -f secrets.yml
	kubectl apply -f mongo-deploy.yml
	kubectl apply -f mongo-svc.yml 

step:7 
 	setting up Monitoring tool Prometheus and Grafana
	kubectl create namespace monitoringL

step:8	deploy -f promethues-deploy.yml
	deploy -f promethues-config.yml

step:9
	deploy -f grafana-deploy.yml
	kubectl create secret generic grafana-secret --from-literal=admin-password=${{ secrets.PASS }} -n monitoring

step:10
	Apply RBAC configurations
	kubectl apply -f rbac-role.yml
	kubectl apply -f rbac-rolebinding.yml

step:11 
	Set up Ingress
	kubectl apply -f ingress.yml
