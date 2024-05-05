# Task 
(VPC peering and Kubernetes Installation with kubeadm and containers creation and publishing apps and accessing them from the other Windows server. )
2. Install 2 linux servers in a private subnet in a different VPC , create a Kubernetes cluster with them . One worker the other is a master. Then write a basic web app which will get the index.html from S3 bucket and will present the html to the windows server from the previous excersice. The containers will be stored in dockerhub to save cost.


Using the AWS machine linux has some weird issues because of missing etables and other stuff. 
Do the following steps to download kubectl and kubeadm: 
```bash

#!/bin/bash

cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.30/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.30/rpm/repodata/repomd.xml.key
EOF

sudo dnf update

sudo dnf install -y kubectl kubeadm 


# efs 
sudo dnf install -y amazon-efs-utils
mount -t efs -o tls,iam,accesspoint=fsap-0fc7d4656ac187a10 fs-07079a1e7a0ef7e75: /mnt/efs-test-2

```

To see the weird errors of kubeadm run the following command: 
```bash

kubeadm init
```
