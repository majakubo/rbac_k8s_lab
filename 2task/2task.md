openssl genrsa -out datascientist.key 2048

openssl req -new -key datascientist.key -out datascientist.csr -subj "/CN=datascientist/O=group1"

openssl x509 -req -in datascientist.csr -CA C:\Users\a.szlendak\.minikube\ca.crt -CAkey C:\Users\a.szlendak\.minikube\ca.key -CAcreateserial -out datascientist.crt -days 500

kubectl config set-credentials datascientist --client-certificate=datascientist.crt --client-key=datascientist.key

kubectl config set-context datascientist-context --cluster=minikube --user=datascientist

kubectl config view

![image](https://user-images.githubusercontent.com/47759484/148402205-035bf298-32d0-4536-a1cb-0887a5e55460.png)


kubectl config use-context datascientist-context
kubectl config current-context

![image](https://user-images.githubusercontent.com/47759484/148402478-5a0cf91a-349b-45ae-aad0-7036028214b1.png)

