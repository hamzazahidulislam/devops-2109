<!-- @format -->

# Server Stup

### Gives the user read permission, and removes all other permission.

    sudo chmod 400 keypair.cer

### access the server with the keypair.cer

    ssh -i ./keypair.cer ubuntu@13.232.51.123

### update server

    sudo apt update

### install docker

    sudo apt install docker.io -y

### run nginx container on docker on port 8080

    sudo docker run -p 8080:80 nginx

### install Net Tools

    sudo apt install net-tools
    ifconfig

### install TCPDUMP

    sudo apt install tcpdump

### check network traffic on interface eth0

    sudo tcpdump -i eth0

### check network traffic on interface eth0 and port 8080

    sudo tcpdump -i eth0 dst port 8080
    sudo tcpdump -i lo dst port 8080

### check network route table

    sudo netstat -tunlp

### flexible tool for interrogating DNS name servers

    dig localhost

### IP packet filter rules

    sudo iptables -t nat -L

### Route Table

    sudo route

### check ip address added in interface

    sudo ip addr

### display the status of TCP and UDP endpoints in table format

    netstat -nltp

### allows for port scanning and port listening

    netcat -l -p 8000

### Telnet utility allows users to test connectivity to remote machines

    telnet localhost 8000

### K8s replicaController watch mode

    kubectl get rc -w

### K8s get services

    kubectl get svc

### K8s delete pod

    kubectl delete pod name1 name2

### get k8s running pod environment variable

    kubectl exec -it <pod_name> -- env

### get k8s running pod show labels

    kubectl get pods --show-labels
    kubectl get pods --show-labels -o wide
    kubectl get all | grep <selector_name>

### get k8s services description and replicaController

    kubectl describe svc <service_name>
    kubectl get rc

### delete k8s replicaController

    kubectl delete rc <replicaController_name>

### access running k8s pod inside a container

    kubectl exec -i -t my-pod --container main-app -- /bin/bash

### remove k8s running pod labels

    kubectl label pod <pod_name> <label_key>-

### k8s get namespace

    kubectl get ns
    kubectl get pods -n kube-system

### get k8s volumes

    kubectl get pv
    kubectl get pvc
    kubectl get storageclass
    kubectl describe storageclass

### encoded base64 base

    echo -n "hello" | base64

### check kubernetes cluster configuration

    kubectl config current-context

### change kubernetes namespaces

    kubectl config use-context microk8s

## Reference

- Overview of kubectl

  - https://kubernetes.io/docs/reference/kubectl/overview/

- Get environment variable from kubernetes pod?

  - https://stackoverflow.com/questions/59198188/get-environment-variable-from-kubernetes-pod

- Get a Shell to a Running Container
  - https://kubernetes.io/docs/tasks/debug-application-cluster/get-shell-running-container/
