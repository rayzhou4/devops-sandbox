# Hello Kubernetes
Made a simple Kubernetes cluster with WebApp and MongoDB pods which can be deployed locally through Minikube

### Learning Objectives
- Kubernetes (+ Kubectl)
- Minikube

### How to use
**NOTE**: Do **not** delete or stop minikube as a docker container. \
**NOTE:** The Kubectl CLI is for configuring the Minikube cluster AND Minikube CLI is for starting up and deleting the cluster.

Install Docker, Minikube and clone repo locally. Then, run the following commands to first start Minikube (with Docker as its driver) and check its status (I ran the following commands in an individual PowerShell terminal at my root folder, "C:/Users/my_username", because I would always run into problems running it in VSCode):

<blockquote>
  minikube start --driver docker 
  
  minikube status
</blockquote>

Afterwards, you want to run all these commands in this order in the path of where you installed the repo to start the WebApp deployment and MongoDB service: 

<blockquote>
  kubectl apply -f mongo-config.yaml <br>
  kubectl apply -f mongo-secret.yaml <br>
  kubectl apply -f mongo.yaml <br>
  kubectl apply -f webapp.yaml <br>
</blockquote> <br>

Then, you use the get and describe keywords from kubectl to see the detailed info about each specific component (or all of them too!):

<blockquote>
  kubectl get node -o wide<br>
  kubectl get pod -o wide<br>
  kubectl get svc -o wide<br>
  kubectl get all -o wide<br>
</blockquote> <br>

<blockquote>
  kubectl describe svc {svc-name} <br>
  kubectl describe pod {pod-name} <br>
</blockquote> <br>

Then, to actually view your WebApp that is connected to the MongoDB, you would need to execute the following command:

<blockquote>
  minikube ip
</blockquote> <br>

Then in your browser you need to enter "MINIKUBE_IP:30100".

If that fails (like it did for me), execute the follwing command to host the application:

<blockquote>
  minikube service webapp-service
</blockquote> <br>

To stop and remove minikube cluster and all resources:

<blockquote>
  minikube stop

  minikube delete
</blockquote> <br>