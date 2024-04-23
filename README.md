# Kubernetes
Kubernetes Mastery: Hands-On Lessons From A Docker Captain, Bret Fisher

## Kubernetes Architecture
![architecture1](docs/images/architecture.png)

## Kubernetes Physical Architecture
![architecture1](docs/images/physical-architecture.png)

## Shpod Tips and Tricks

Be sure to come back to this lecture later if you have shpod issues, as I've thrown in common hiccups as you use it throughout the course!

- **Tip 1: Namespaces matter!** <br>
Once you learn about namespaces, you know that running kubectl commands often only affects the current namespace. Shpod runs in the shpod namespace, so if you mean to do something with the default namesapce, you need to either ensure that shpod config is set to use the default namespace (which it is by default) or ``` add -n defaul ``` to your commands. So ``` kubectl get pods ``` would turn into ``` kubectl get -n default pods ``` . We've setup the shpod pod to set it's namespace to default though, so this shouldn't be a big issue.

- **Tip 2: DNS matters with Namespaces!** <br>
The above shpod namespace affects DNS as well. If you need to curl or ping a Service name (which you'll learn later), remember that Kubernetes Service DNS names are namespace-sensitive from inside the cluster. Doing a ``` ping myservice ``` from a pod in one namespace only works if that Service is in the same namespace. In the Shpod, you would need to ``` ping mypod.default ``` if that Service was in the default namespace.

- **Tip 3: Attach shows you the console (tty) output**, even from multiple terminals. You can use exec for additional terminal shells <br>
An ``` attach ``` command will show the virtual console of a pod (like a tty), so multiple ``` attach ``` commands in multiple terminal windows will show the same thing because they are both looking at the console output. For your 2nd terminal, you can use an ``` exec ``` command that will start a new shell process in the existing container. This works **exactly** the same way as Docker attach and exec commands: <br><br>
1st window, attach: <br> ``` kubectl attach --namespace=shpod -ti shpod ``` <br><br>
2nd window, create a new bash shell: <br> ``` kubectl exec --namespace=shpod -ti shpod -- bash -l ```