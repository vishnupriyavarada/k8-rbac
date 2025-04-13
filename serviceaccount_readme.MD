# Pod should access secret manager
### Steps

REGION_CODE=us-east-1
CLUSTER_NAME=expense
ACCOUNT_ID=529088271493

** 1. Make sure OIDC provider exists
```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```  
** 2. Create IAM policy for secret manager. Give only read permissions(under Read --> GetSecretValue)

** 3. we need to map sa (service account) to a created IAM policy in above step

```
eksctl create iamserviceaccount \
--cluster=$CLUSTER_NAME \
--namespace=expense \
--name=expense-mysql-secret \
--attach-policy-arn=arn:aws:iam::$ACCOUNT_ID:policy/ExpenseMysqlSecretRead \
--override-existing-serviceaccounts \
--region $REGION_CODE \
--approve
```