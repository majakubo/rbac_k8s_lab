Task 0
Prepare environment with minikube and callico
Task 1 (usage of Role RBAC)
You have specific deployment in you company, your CTO put pressure on moving towards least privilage model. You have two environments, production and development, you've heard that some developer messed with containers running on production. Your task is to separate production and development infrastructure into two namespaces, then create 3 roles, prod, dev and auditor, where prod has full access to prod and dev, dev have read only on prod and full access on dev, auditor has read only. 
Task 2
One of your data sciencist has created ticket that he can't do sth, look into data_sciencist role and adjust his permission so that he/she will be able to do his job. Don't give him full persmissions!.
Task 3
Your network engineer reported that there is visible suspected network traffic on ports xyzs to images xyzs, by digging the configuration you've noticed that to much ports is open, limit ports only to required for proper functioning.
Task 4
App from specific diagram is not working, check network policies and be the hero of your company by fixing app.
