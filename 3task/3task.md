## Task 3 (Role Debugging)
Your network engineer reported that there is visible suspected network traffic, xyz pods are accessed with ssh port and large data transfer is done with xyz ports, by digging the 
configuration you've noticed that to much ports is open, limit ports only to required for proper functioning and for only group of ip addresses (data about reqiured ports in table).

Start example infrastructure with no network policies.
Create network policy to meet requirements from network enginner.
Run commands to verify results
Save yaml for this task.

As a result all Pods will be able to connect to the Internet only via selected ports.

### Deploy the resources and verify network traffic between Pods and host machine
In cmd go to the directory with files for this exercise and:

Create the nginx and hello pods in the default namespace using the provided manifests. The nginx Pod will be exposed outside the cluster using a Service of type NodePort and the hello Pod will be exposed internally using a Service of type ClusterIP. Run this command:
