```	
kubectl get config view

	
kubectl --kubeconfig john.kubeconfig config set-cluster kubernetes  --server https://10.182.0.3:6443 --certificate-authority=ca.crt


kubectl --kubeconfig john.kubeconfig config set-credentials john --client-certificate /root/test/john.crt  --client-key /root/test/john.key

kubectl --kubeconfig john.kubeconfig config set-context john-kubernetes --cluster kubernetes --namespace finance --user john 


kubectl create role  --help | grep kubectl 
kubectl create role john-finance --verb=get,list --resource=pods --namespace finance

kubectl create rolebinding john-fianace-rolebinding --role=john-finance --user=john --namespace finance

kubectl --kubeconfig john.kubeconfig create deploy nginx --image nginx 

```
##the below command a copy from line 2 above runs in the same folder
##kubectl --kubeconfig john.kubeconfig config set-credentials john --client-certificate john.crt  --client-key john.key
