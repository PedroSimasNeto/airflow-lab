# Instalação do ArgoCD no K8s

## Criar o namespace
```shell
kubectl create ns argocd
```

## Deploy do ArgoCD no K8s
```shell
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Expor o NodePort para acesso da UI
```shell
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
```

## Port-forward para acesso da aplicação 
```shell
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Acesso a Secret do Admin do ArgoCD
```shell
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d
```

# Configuração do Airflow no ArgoCD

## Adicionando o repositório do GitHub
```shell
kubectl apply -f repository.yaml
```

## Deploy do Airflow no ArgoCD
```shell
kubectl apply -f airflow.yaml
```