# Kubernetes course
This repository contains a personal fork of the course files from 
 [Edward Viaene](https://www.udemy.com/user/ward-viaene/) Kubernetes course on 
 Udemy: https://www.udemy.com/learn-devops-the-complete-kubernetes-course/?couponCode=KUBERNETES_GITHUB



## install minikube to test kubernetes on your local machine 

[minikube](https://minikube.sigs.k8s.io/docs/start/) 
 is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: minikube start

    >    minikube start
    >    k get po -A
    NAMESPACE     NAME                               READY   STATUS    RESTARTS   AGE
    kube-system   coredns-74ff55c5b-67q4t            1/1     Running   0          39s
    kube-system   etcd-minikube                      0/1     Running   0          47s
    kube-system   kube-apiserver-minikube            1/1     Running   0          47s
    kube-system   kube-controller-manager-minikube   0/1     Running   0          47s
    kube-system   kube-proxy-d4cpc                   1/1     Running   0          39s
    kube-system   kube-scheduler-minikube            0/1     Running   0          47s
    kube-system   storage-provisioner                1/1     Running   0          52s

you can use the Kubernetes Dashboard like this :
    
    minikube dashboard
    
## test a deployment on minikube

To create a sample deployment and expose it on port 8080:

    kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
    kubectl expose deployment hello-minikube --type=NodePort --port=8080

It may take a moment, but your deployment will soon show up when you run:

    kubectl get services hello-minikube

The easiest way to access this service is to let minikube launch a web browser for you:

    minikube service hello-minikube

Alternatively, use kubectl to forward the port:

    kubectl port-forward service/hello-minikube 7080:8080

Tada! Your application is now available at http://localhost:7080/

