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
