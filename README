# Instalação do ArgoCD no K8s

## Criar o namespace
kubectl create ns argocd

## Deploy do ArgoCD no K8s
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## Expor o NodePort para acesso da UI
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'

## Port-forward para acesso da aplicação 
kubectl port-forward svc/argocd-server -n argocd 8080:443

## Acesso a Secret do Admin do ArgoCD
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d