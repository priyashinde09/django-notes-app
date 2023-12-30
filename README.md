# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/priyashinde09/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest

##EKS cluster
1. deploy deployment file.
Create deployment.yaml file
vi deployment
container port-8000
apply " kubectl apply -f deployment.yaml" command
2. deploy service file.
create service.yaml file
vi service.yaml
apply "kubectl apply -f service.yaml" command
Expose node port as 31000
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
