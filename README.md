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
    kubectl describe ns myns

### delete k8s replicaController

    kubectl delete rc <replicaController_name>

### access running k8s pod inside a container

    kubectl exec -i -t my-pod --container main-app -- /bin/bash

### remove k8s running pod labels

    kubectl label pod <pod_name> <label_key>-

### k8s get namespace

    kubectl get ns
    kubectl get pods --all-namespaces
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
    kubectl cluster-info

### change kubernetes namespaces

    kubectl config use-context microk8s

### create namespace in k8s cluster

```
kubectl config set-context testing \
 --namespace testing \
 --cluster docker-desktop \
 --user docker-desktop

```

     kubectl config set-context --current --namespace=test

### create namespace

    kubectl create ns test

### run pod with specified namespace

    kubectl apply -f firstpod.yml --namespace test
    kubectl get pods -n test

### check the yaml configuration

    kubectl apply -f replica.yml --dry-run=client

### when you forgot the yaml configuration

    kubectl explain rc --recursive | less
    kubectl explain pod --recursive | less

### how to delete bulk resources

    kubectl delete pods --all
    kubectl delete rc --all

### track your k8s deployement rollout status

    kubectl rollout status deployment nginx-deployment
    kubectl rollout history deployments nginx-deployment
    kubectl apply -f nginx-deployment.yaml ;watch "kubectl get rs -o wide"
    kubectl apply -f nginx-deployment.yaml ;watch "kubectl get all -o wide"

### k8s roll back and pasue deployment

    kubectl rollout undo --help
    kubectl rollout undo deploy nginx-deployment
    kubectl rollout undo --to-revision=3 deploy nginx-deployment
    kubectl rollout pause deploy nginx-deployment
    kubectl rollout status deploy nginx-deployment
    kubectl rollout resume deploy nginx-deployment

### get k8s deployment

    kubectl get deployments
    kubectl get deploy -o wide
    kubectl get deployments nginx-deployment -o yaml

### check docker container use resources

    docker container stats d638e2778ea0

### k8s resources list

     kubectl api-resources | less
     kubectl api-resources | grep -i pod

### delete pod with specified namespace

    kubectl delete -f firstpod.yml -n test

### get k8s kube-public value

    curl -k https://192.168.214.130:6443/api/v1/namespaces/kube-public/configmaps/cluster-info

### get resources access to namespace

    curl myfirstservice.mynamespace.svc.cluster.local:8080
    curl myfirstservice.mynamespace.svc.cluster.local

### how to define ResourceQuota in namespace

    kubectl create quota my-quota --hard=pods=10
    kubectl delete quota my-quota
    kubetcl apply -f resourcequota.yml --namespace=myns
    kubectl delete quota resourcequota --namespace=myns

## Reference

- Overview of kubectl

  - https://kubernetes.io/docs/reference/kubectl/overview/

- Get environment variable from kubernetes pod?

  - https://stackoverflow.com/questions/59198188/get-environment-variable-from-kubernetes-pod

- Get a Shell to a Running Container
  - https://kubernetes.io/docs/tasks/debug-application-cluster/get-shell-running-container/
