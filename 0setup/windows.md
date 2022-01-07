### Chocolatey Package Manager instalation:
In cmd opened with administrative rights:

```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```
### Virtual Machine instalation:
Download VM from [its side](https://www.virtualbox.org/).

### Docker instalation:
Download and start Docker desktop from [Docker docs](https://docs.docker.com/desktop/windows/install/), make sure the **Enable Hyper-V Windows Features** option is selected.

### Minikube instalation:
In cmd type:
```
choco install minikube
minikube version
```
![image](https://user-images.githubusercontent.com/47759484/147950326-b5779a85-421c-425e-88e7-ed62f0221989.png)


### Kubectl instalation:
In cmd type:
```
choco install kubernetes-cli
kubectl version
```
![image](https://user-images.githubusercontent.com/47759484/147950390-b45db8a8-5019-4f9f-a1f0-0a138b57e5e4.png)

### Starting a local Kubernetes cluster
On Windows it is best to start minikube using either Hyper-V or Virtualbox - Docker networking does not work properly on Windows and you will run into issues.
```
minikube start --network-plugin=cni --cni=calico --driver=hyperv
OR
minikube start --network-plugin=cni --cni=calico --driver=virtualbox
```
These commands may take a moment. 
If you're getting error about not enough memory, but it seems like you have enough (Memory=2200MB, Disk=20000MB) try restarting your computer and running starting command as the first thing.  

Check if done succcesfully:
```
kubectl get no
```
![image](https://user-images.githubusercontent.com/47759484/148371407-d86f9131-38c6-4616-a25d-410e49aa9ce3.png)


To stop minikube:
```
minikube stop
```
To delete minikube completely:
```
minikube delete
```
