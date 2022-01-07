Tasks are divided into two groups: Creating and Debugging.
Creating tasks are designed to teach how to translate requirements into kubernets configs.
Debuggin are designed to teach how to view, analyze and modify existing ones.

Task 0
Prepare environment with minikube to create k8s with callico network plugin.

Task 1 (Creating, usage of Role RBAC)
Your company have specific infrastructure described with 1task/infrastructure1.yaml. Your CTO put pressure on moving towards least privilage RBAC model. You have two type of objects: production objects named *-dev and development objects named *-dev. It was recently reported that some developer messed with pods running the production application, so that production nginx was affected. Your task is to separate production and development infrastructure into two namespaces, then create 3 roles: ops, dev and auditor. Ops role should have full access to whole infrastructure, dev should have read only on prod namespace and full access on dev namespace, auditor should read only to dev and prod. 

Prework:
Run kubectl apply -f 1task/infrastructure1.yaml

Sugested workflow:
1. Create two namespaces
2. Update infrastructure1 so that prod and dev are in separate namespaces.
3. Create required roles and rolebindings

Verification:
1. Upload yaml file of infrastructure3 and yaml files with newly created roles and rolebindings.

Task 2 (Debugging, usage of Role and hopefully Cluster Role)
One of your data sciencist - Bob, has created ticket that he can't scale his development spark cluster, look into data_sciencist role and adjust his permission so that he/she will be able to do what he wanted, give him only absolutely necessary permissions.

Prework:
Run kubectl apply -f 2task/infrastructure2.yaml


Verification:
1. Scale number of podxyz in spark deployment using datasciencist context.
2. Upload yaml files with changed objects.

Task 3 (Creating, usage of network policies to limit network traffic ingress/egress traffic)
Your network engineer reported that there is suspected network traffic in your company network. Wordpress pod is accessed with ssh port and large data transfer is done through it. By digging the configuration you've noticed that to much ports are open. Change infrastructure3.yaml to limit ports only to required for proper functioning (table) and only for ip addresses from your company internal subnet (data about reqiured ports in table). 
Prework
Run kubectl apply -k 3task/

Veryficaiton:
1. Upload infrastructure3.yaml after changes.

