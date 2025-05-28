GitOps with ArgoCD and Kubernetes (K3s)

This is a basic project to show how GitOps works using ArgoCD and Kubernetes.

What This Project Does

Deploys a simple app to Kubernetes using K3s.

Uses ArgoCD to sync Kubernetes resources from a GitHub repo.

Automatically updates the app when you push changes to Git.

Tools Used:

ArgoCD

K3s (Kubernetes)

GitHub

EC2 Ubuntu Server

Docker

Files Included:

deployment.yaml – Deployment for a sample HTTP app

service.yaml – Service to expose the app

kustomization.yaml – Lists files for ArgoCD to apply

Steps:

Install K3s and ArgoCD on an EC2 Ubuntu server.

Clone this repository:

git clone https://github.com/arjumandshafi/Devopintership-project1

then change the directory:

cd Devopintership-project1

add deployment.yaml, service.yaml, kustomization.yaml files

then push the files to github 

git init

git remote add origin https://github.com/arjumandshafi/Devopintership-project1

git add .

git commit -m "Initial"

git push -f https://github.com/arjumandshafi/Devopintership-project1

In ArgoCD, create an app.

Go to ArgoCD UI http://<EC2-Public-IP>:30080

Click "NEW APP"

Fill in:

App Name: hello-app

Project: default

Sync Policy:  Auto 

Repository URL: https://github.com/arjumandshafi/Devopintership-project1

Path: . 

Cluster URL: https://kubernetes.default.svc

Namespace: default

then create app.

Update any file → push to Git → ArgoCD updates the app.

Access the App:

Run:

kubectl get svc hello-app

Use the NodePort to open the app in your browser:

http://<EC2-IP>:<NodePort>

Output should be something like:

Hello from GitOps!
