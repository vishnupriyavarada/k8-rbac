** Commands to get aws-auth object 

```
kubectl get configmap aws-auth -n kube-system
```
```
kubectk get configmap aws-auth -n kube-system -o yaml
```
*** Copy the output  to a file aws-auth.yaml

** Edit aws-auth.yaml file (google search : edit aws auth configmap -> open the article  "Grant IAM users access to Kubernetes with a ConfigMap" )


** Command to access eks cluster using kubectl

```
aws eks update-kubeconfig --region region-code --name my-cluster

aws eks update-kubeconfig --region us-east-1 --name expense
```


# RBAC

REGION_CODE=us-east-1
CLUSTER_NAME=expense
ACCOUNT_ID=529088271493

### Permissions

* 1. OIDC Provider

```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```  