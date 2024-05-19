# Argocd-playground

Installation options
• Non High availability setup
• Suitable for evaluation or dev/testing environments. 
• High availability setup.
• Recommended for production.
• You need at least 3 worker nodes.
• Light installation “Core”
• Suitable if ArgoCD is used by administrators only. UI and API 
server is not installed for end users.
• By default its installed as Non-HA.

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
