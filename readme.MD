** Commands to get aws-auth object 

```
kubectl get configmap aws-auth -n kube-system
```
```
kubectk get configmap aws-auth -n kube-system -o yaml
```
*** Copy the output  to a file aws-auth.yaml

** Edit aws-auth.yaml file (google search : edit aws auth configmap -> open the article  "Grant IAM users access to Kubernetes with a ConfigMap" )