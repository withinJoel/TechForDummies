# Kubectl Commands

* To check the cluster status `kubectl cluster-info`
* To view nodes in the cluster `kubectl get nodes`
* To list all the pods in the default namespace `kubectl get pods`
  * Add `-o wide` along with `kubectl get pods` to get more details.
* To get a detailed info about a specific pod `kubectl describe pod <pod-name>`
* To see all resources running in the current namespace. `kubectl get all`
* To see the version of the kubectl `kubectl version`
* To see the logs for that pod `kubectl logs -f <pod-name>`
