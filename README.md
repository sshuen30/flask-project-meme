## The docker-compose.yaml creates two containers:
- An "app" container serving the flask application on gunicorn server @ port 5001
- A "nginx" container serving the nginx service @ port 8081
- A nginx configuration (proxy pass directive) is used to route incoming requests to Nginx (port:8081) to the flask app named "app" running on port:5001. 

## How to run flask project using docker-compose:
- Git clone repository
``` bash
gitclone https://github.com/sshuen30/flask-project.git
```
``` bash
cd into flask-project
```
- Start docker compose
``` bash
docker-compose up -d or 
```
- Start docker compose and scale 3 containers for app
``` bash
docker-compose up -d --build --scale app=3 (To create 3 containers for app)
```
- Stop docker compose
``` bash
docker-compose down
```
- Browser: xxx.xxx.x.xx:8081

## How to run flask project on Kubernetes:
- Copy flask-development.yaml and flask-service into a kubernetes cluster (eg, Google Cloud)
- Start a deployment
``` bash
kubectl apply -f flask-development.yaml
```
- Start a load balancer service to route traffic to deployment - no need for nginx
``` bash
kubectl apply -f flask-service.yaml 
```
- Get IP and port no. of service
``` bash
kubectl get svc meme-flask-service 
```
- Scale deployment to 2 pods
``` bash
kubectl scale deployment meme-flask-deployment --replicas=2 
```
- Change deployment image
``` bash
kubectl set image deployment/meme-flask-deployment meme-flask=sshuen30/flask-app:v1 
```
