### Create a client certificate

Create a directory (cert) where to save the certificates for data scientist:
```
mkdir cert && cd cert
```
Generate a key:
```
openssl genrsa -out datascientist.key 2048
```
Generate a Client Sign Request:
```
openssl req -new -key datascientist.key -out datascientist.csr -subj "/CN=datascientist/O=group1"
```

Find PATH to .minikube on your PC (C:\Users\user\.minikube)
Generate the certificate:
```
openssl x509 -req -in datascientist.csr -CA PATH\ca.crt -CAkey PATH\ca.key -CAcreateserial -out datascientist.crt -days 500
```

### Create a user
Set a user entry: 
```
kubectl config set-credentials datascientist --client-certificate=datascientist.crt --client-key=datascientist.key
```
Set a context entry:
```
kubectl config set-context datascientist-context --cluster=minikube --user=datascientist
```
Check:
```
kubectl config view
```
![image](https://user-images.githubusercontent.com/47759484/148402205-035bf298-32d0-4536-a1cb-0887a5e55460.png)
Switch to the created user:
```
kubectl config use-context datascientist-context
kubectl config current-context
```
![image](https://user-images.githubusercontent.com/47759484/148402478-5a0cf91a-349b-45ae-aad0-7036028214b1.png)
Check your lack of access:
```
kubectl create namespace ns-test
```
![image](https://user-images.githubusercontent.com/47759484/148408869-f4aca3ce-eae2-4932-ac09-5368b3f68ccf.png)


###Grant access to the user
