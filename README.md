How to run flask project using docker-compose:
- gitclone https://github.com/sshuen30/flask-project.git
- cd into flask-project
- docker-compose up -d
- docker-compose up -d --build --scale app=3
- Browser: xxx.xxx.x.xx:8081
- docker-compose down

How to run flask project on Kubernetes:
- Copy flask-development.yaml and flask-service into a kubernetes cluster (eg, Google Cloud)
- kubectl -f flask-development.yaml
- kubectl -f flask-service.yaml

