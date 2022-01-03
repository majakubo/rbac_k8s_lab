### Chocolatey Package Manager instalation:
In cmd opened with administrative rights:

```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

### Docker instalation:
Download and start Docker desktop from [Docker docs](https://docs.docker.com/desktop/windows/install/), make sure the **Enable Hyper-V Windows Features** option is selected.

### Minikube instalation:
Type:
```
choco install minikube
minikube version
```
![image](https://user-images.githubusercontent.com/47759484/147950326-b5779a85-421c-425e-88e7-ed62f0221989.png)


### Kubectl instalation:
Type:
```
choco install kubernetes-cli
kubectl version
```
![image](https://user-images.githubusercontent.com/47759484/147950390-b45db8a8-5019-4f9f-a1f0-0a138b57e5e4.png)

