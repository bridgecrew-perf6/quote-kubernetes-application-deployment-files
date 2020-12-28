
![alt text](https://cdn-images-1.medium.com/max/1200/1*1BF_eIkV6wkuqsziZ_hf7Q.png)

# Stateful Kubernetes CRUD Application Deployment Files

This repository is a part of a Medium Post named  **### How to Deploy a Stateful CRUD Web Application to Minikube(Local Cluster) and Google Cloud Kubernetes Engine(GKE)**. It is about creating a Stateful application and deploying it both Minikube(Local Cluster) and Google Cloud Kubernetes Engine(GKE).

There are multiple deployment files in this repository. You can find what they are in the description below;

***kubernetes-deployment.yaml*** --> This is the main file which we need to deploy the following repositories to Kubernetes
1. [quote-kubernetes-application-web](https://github.com/emreozcan3320/quote-kubernetes-application-web)
2. [quote-kubernetes-application-api](https://github.com/emreozcan3320/quote-kubernetes-application-api)

*docker-compose-deployment.yaml* --> docker-compose deployment.yaml file which is used at a [CRUD web application repository](https://github.com/emreozcan3320/star-wars-quote-web-application).  I put it here so we can easily compare Kubernetes and docker-compose deployment files.

*kompose-convert-files* --> Output files of the Kompose tool which converts docker-compose deployment.yaml file to Kubernetes deployment.yaml files.

*dump.sql* --> In case you need initial data. Docker-compose deployment needs that but Kubernetes deployment starts without initial data.

### How to run it?
***!!IMPORTANT***
This deployment file uses Google Cloud's private container registry. So you **CAN NOT**  access the docker images. But you can build your own images by using the repositories that I gave you.  There are configuration differences related to local MySql usage or  Google Cloud SQL usage. To make these changes, you should only switch branches at the **backend**. Therefore please check the [quote-kubernetes-application-api](https://github.com/emreozcan3320/quote-kubernetes-application-api) repository. After that, you have to update image sources on kubernetes-deployment.yaml according to your image address.

If all configuration is done you just need to run;
`kubectl apply -f kubernetes-deployment.yaml`
you can check deployment status by getting information about all objects like
`kubectl get all`

If you are using Minikube, you have to type `minikube tunnel`. With that LoadBalancer service can take an IP and the application can be exposed to an IP and PORT. Also you can use **Minikube Dashboard** to exam cluster. You can reach it by runing `minikube dashborad` command.

If you want to run this application with Docker-compose please check [this repository](https://github.com/emreozcan3320/star-wars-quote-web-application).

