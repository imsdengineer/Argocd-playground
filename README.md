# Argocd-playground

Installation options
• Non-High availability setup
• Suitable for evaluation or dev/testing environments. 
• High availability setup.
• Recommended for production.
• You need at least 3 worker nodes.
• Light installation “Core”
• Suitable if ArgoCD is used by administrators only. UI and API 
server is not installed for end users.
• By default, its installed as Non-HA.

Notes: Installation options
You need to create a namespace for argocd.

kubectl create ns argocd

and then choose one of the below options :

1. Non-HA:

a. cluster-admin privileges: https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml 

b. namespace level privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/namespace-install.yaml 



2. HA:

a. cluster-admin privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/ha/install.yaml 

b. namespace level privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/ha/namespace-install.yaml 

3. Light installation "Core"

https://github.com/argoproj/argo-cd/raw/stable/manifests/core-install.yaml 

4. Helm chart: https://github.com/argoproj/argo-helm/tree/main/charts/argo-cds 

*****TO ACCESS THE WEBUI OF ARGOCD, GET THE PASSWORD FROM SECRETS***** 

https://localhost:8080/

<<< kubectl get secrets -n argocd  >>>
$ k get secrets -n argocd
NAME                          TYPE     DATA   AGE
argocd-initial-admin-secret   Opaque   1      57d
argocd-notifications-secret   Opaque   0      57d
argocd-secret                 Opaque   5      57d

k get secret argocd-initial-admin-secret -n argocd -o yaml
apiVersion: v1
data:
  password: R1gtZkI4Tk5Bd1IzOTIyWA==
kind: Secret
metadata:
  creationTimestamp: "2024-03-23T13:53:51Z"
  name: argocd-initial-admin-secret
  namespace: argocd
  resourceVersion: "5786"
  uid: 56c89273-8585-424a-aeca-b51a2ca83c37
type: Opaque

#######Convert into base64 format.

$ echo 'Hello, World!' | base64 
SGVsbG8sIFdvcmxkIQo=

*********DEPLOY THE APPLICATIONS FROM THE MANIFESTS************

kubectl apply -f <file.yaml>

kubectl get applications -n argocd


