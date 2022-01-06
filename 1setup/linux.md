### Docker instalation:
Follow [Docker docs](https://docs.docker.com/engine/install/ubuntu/) instructions.

### Minikube instalation:
In cmd type:
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### Kubectl instalation:
In cmd type:
```
sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2 curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

### Starting a local Kubernetes cluster
```
minikube start --network-plugin=cni --cni=calico
```
These commands may take a moment. 
Check if done succcesfully,  your single-node minikube cluster should me listed as ready:
```
kubectl get no
```
Similar to this:
![image](https://user-images.githubusercontent.com/47759484/148371869-33e302ac-2320-4521-890c-814d6cf2898f.png)


To stop minikube:
```
minikube stop
```
To delete minikube completely:
```
minikube delete
```
