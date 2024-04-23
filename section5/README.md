## First Contact with Kubectl

### getting thet nodes in the system
The below command returns an abtracted information about the list of nodes <br>
```
kubectl get node
```

### Obtaining machine-readeable output
**Note:** ``` Kubectl get ``` can output **JSON**, **YAML**, or be directly formatted <br>
- **Give us more info about the nodes:** <br>
``` kubectl get nodes -o wide  ```
- **Let's have some YAML** <br>
``` kubectl get nodes -o yaml ```
### (AB)using ```kubectl``` and ```jq```
- **Show the capcity of all our nodes as a stream of JSON objects:** <br>
``` kubectl get nodes -o json | jq ".items[] | {name:.metadata.name} + .status.capacity"```