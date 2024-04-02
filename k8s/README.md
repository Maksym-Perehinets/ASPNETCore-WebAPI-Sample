---
To start this cluster localy pleas follow next instruction

First install kubectl (Follow next instruction only if you don't have kubectl and kubeadm iinstalled v1.29) 

Linux instaletion guide (Debian)

Install apt-transport-https, ca-certificates and curl
```console
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
```

Install public sign key for k8s
```console
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```

Add k8s repo to your sources.list.d
```console
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```

Then you can install kubectl kubeadm
```console
sudo apt-get update
sudo apt-get install -y kubectl kubeadm
```

After that you are ready to install minikube 

Download minikube binary for Debian
```console
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
```

Then install it 
```console
sudo dpkg -i minikube_latest_amd64.deb
```

To start up your local k8s cluster 
```console
minikube start
```
After that add node 
```console
minikube node add
```

Now you can start testing it in local env
```console
minikube image load <your name or what ever you want>/api-asp:latest
```

To expouse your service use 
```console
kubectl port-forward -n bestrong service/bestrong-api-svc <8080 or any port ypu want>:8080
#or for port 8080 use 
kubectl port-forward -n bestrong service/bestrong-api-svc 8080:8080
```