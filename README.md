The docker-compose.yaml creates two containers:
- An "app" container running the flask application on gunicorn server on port 5001
- A "nginx" container running the nginx service
- A nginx configuration (proxy pass directive) is used to route incoming requests to Nginx on port 8081 to the flask app named "app" running on port 5001. 

How to run flask project using docker-compose:
- gitclone https://github.com/sshuen30/flask-project.git
- cd into flask-project
- docker-compose up -d or 
- docker-compose up -d --build --scale app=3 (To create 3 containers for app)
- Browser: xxx.xxx.x.xx:8081
- docker-compose down

How to run flask project on Kubernetes:
- Copy flask-development.yaml and flask-service into a kubernetes cluster (eg, Google Cloud)
- kubectl -f flask-development.yaml
- kubectl -f flask-service.yaml (Create a load balancer service to route traffic to deployment - no need for nginx)
- kubectl get svc meme-flask-service (Get IP and port no. of service)
- kubectl scale deployment meme-flask-deployment --replicas=2 (scale deployment to 2 pods)
- kubectl set image deployment/meme-flask-deployment meme-flask=sshuen30/flask-app:v1 (Change image)
