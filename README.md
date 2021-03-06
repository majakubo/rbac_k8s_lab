Tasks are divided into two groups: *Creating* and *Debugging*.
*Creating* tasks are designed to teach how to translate requirements into kubernets configs. *Debugging* are designed to teach how to view, analyze and modify existing ones.

## Task 0

Prepare environment with minikube to create k8s with callico network plugin.

---

## Task 1: [Creating] Usage of Role RBAC

Your company have specific infrastructure described with *1task/infrastructure1.yaml*. Your CTO puts pressure on moving towards the least privilage RBAC model. You have two type of objects: production objects named *-prod and development objects named *-dev. It has been recently reported that some developers messed pods running the production application, so that production nginx was affected. Your task is to separate production and development infrastructure into two namespaces, then create 3 types of users: ops, dev and auditor. 

* **ops** user type should have full access to whole infrastructure
* **dev** user type should have read only on prod namespace and full access on dev namespace
* **auditor** user type should have read only to dev and prod

After you create required roles, assign them to existing service accounts: 

* *eve-auditor* should be **auditor**
* *alice-ops* should be **ops**
* *bob-developer* should be **developer**

### Prework:
run
> kubectl apply -f 1task/infrastructure1.yaml

### Hints:
For verifications of permisions it's convinient to use *can-i*, for example:
> kubectl auth can-i get secrets --as=serviceaccount:default:datasciencist

### Sugested workflow:
1. Create two namespaces.
2. Update infrastructure1 so that prod and dev objects are in separate namespaces.
3. Create required roles and rolebindings with RBAC on namespaces.

### Verification:
1. Upload changed yaml file of infrastructure1 and yaml files with newly created roles and rolebindings.

### Cleanup:
1. Run to delete created roles and rolebindings
> kubectl delete -f 1task/infrasturcture1.yaml
2. Delete created roles and rolebindings

#### Help:
Create two namespaces:
https://kubernetes.io/docs/tasks/administer-cluster/namespaces-walkthrough/#create-new-namespaces

Create ClusterRole (across namespaces):
https://kubernetes.io/docs/reference/access-authn-authz/rbac/#clusterrole-example

Create RoleBinding:
https://kubernetes.io/docs/reference/access-authn-authz/rbac/#rolebinding-example

---

## Task 2: [Debugging] Usage of Role and hopefully Cluster Role

One of your data sciencist - Bob (bob-smart service account), has created ticket that he can't scale his development of a spark cluster. By scaling he means runing more spark-workers, look into datasciencist role and adjust his permission so that he will be able to do what he wants to, give him only absolutely necessary permissions.

### Prework:
Run
> kubectl apply -f 2task/infrastructure2.yaml

### Hint:
As with task1, use *can-i*

### Verification:
1. Upload changed infrastructure2.yaml

### Cleanup:
1. Run
> kubectl delete -f 2task/infrastructure2.yaml
2. Delete additional objects that you created.

---

## Task 3 [Creating] Usage of network policies to limit network traffic ingress/egress traffic

Your network engineer reported that there is a suspected network traffic in your company network. Wordpress pod is accessed through ssh port and large data transfer is done through it. It was discovered that source ip addresses that started this suspected trafic are from Malaysia! By digging the configuration you've noticed that there is no network policy created to limit the access to wordpress. Create network policy so that wordpress will acceppt ingress and egress trafic only from you local network.

### Prework:
Run
> kubectl apply -k 3task/

### Verificaiton:
1. Upload infrastructure3.yaml after changes.

### Cleanup:
1. Run
> kubectl apply -f 3task/

#### Help:
Create NetworkPolicy:
https://kubernetes.io/docs/concepts/services-networking/network-policies/#networkpolicy-resource

Ingress from:
https://kubernetes.io/docs/concepts/services-networking/network-policies/#behavior-of-to-and-from-selectors
