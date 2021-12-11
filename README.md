Tasks are divided into two groups: Creating and Debugging.
Creating tasks are designed to teach how to translate requirements into kubernets configs.
Debuggin are designed to teach how to view, analyze and modify existing ones.

Task 0
Prepare environment with minikube to create k8s with callico network plugin.
- install virtualbox
- install minikube
- create cluster
- run callico network
- run example app deployment to veryfi that setup is working

Task 1 (Creating, usage of Role RBAC)
You have specific infrastructure (created with example yaml) in you company, your CTO put pressure on moving towards least privilage RBAC model. You have two type of pods production pods and development pods. It was recently reported that some developer messed pods running production application, so that production database was affected. Your task is to separate production and development infrastructure into two namespaces, then create 3 roles, ops, dev and auditor, where prod has full access to prod and dev, dev have read only on prod and full access on dev, auditor has read only. 

1. Start example infrastructure from given yaml. Application shouldn't be complicated, it can be for example 4 running pods (managed by two deployments): 2 pods with name example_prod, and 2 pods with name example_dev.
2. Create two namespaces
3. Move existing deployments to namespaces
4. Create required roles and rolebindings
5. Run given commands to prove that rolebinding works as expected.
6. Save yaml for this task.

Task 2 (Debugging, usage of Role and hopefully Cluster Role)
One of your data sciencist has created ticket that he can't do sth, look into data_sciencist role and adjust his permission so that he/she will be able to do his job, give him only absolutely necessary permissions.
1. Start example infrastructure with role datasciencist
2. Fix rolebinding for user datasciencist
3. Test
4. Save yaml

Task 3 (Creating, usage of network policies to limit network traffic ingress/egress traffic)
Your network engineer reported that there is visible suspected network traffic xyz pods are accessed with ssh port and large data transfer is done with xyz ports, by digging the configuration you've noticed that to much ports is open, limit ports only to required for proper functioning and for only group of ip addresses (data about reqiured ports in table).
1. Start example infrastructure with no network policies.
2. Create network policy to meet requirements from network enginner.
3. Run commands to verify results
4. Save yaml for this task.

Task 4 (Debugging, network policies with targeting pods)
App from specific diagram is not working, check network policies and be the hero of your company by fixing app.
1. Start example infrastructure with existing network policies
2. Adjust policies to meet requirements from diagram
3. Run commands to verify results
4. Save yaml for this task.
