# in local
- install kubectl
- install and run minikube to run k8 test cluster

# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

# you can change and delete init password

# for the first time:
you need to apply the application.yml with kubectl
kubectl apply -f application.yml

application.yml = argocd configuration
For different environments, create new folders. In this case we only have dev