# First Contact with Kubectl

## Getting thet nodes
The below command returns an abtracted information about the list of nodes <br>
- ``` kubectl get no ``` or ``` kubectl get node ``` or ``` kubectl get nodes ```

### Obtaining machine-readeable output
**Note:** ``` Kubectl get ``` can output **JSON**, **YAML**, or be directly formatted <br>
- **Give us more info about the nodes:** <br>
``` kubectl get nodes -o wide  ``` or ``` kubectl get nodes node1 -o wide  ```
- **Let's have some YAML** <br>
``` kubectl get nodes -o yaml ```
### (AB)using ```kubectl``` and ```jq```
- **Show the capcity of all our nodes as a stream of JSON objects:** <br>
``` kubectl get nodes -o json | jq ".items[] | {name:.metadata.name} + .status.capacity"```
### For more comprehensive overview, we can use ``` kubectl describe ``` instead
- ``` kubectl describe node/node1 ``` or ``` kubectl describe node node1 ```

**Note:** Kindly observe that this follows the pattern: <br> ``` kubectl describe resource-type-name/resource-name ``` or ``` kubectl describe resource-type-name resource-name ```