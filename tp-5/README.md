# Etape 1
Créer les namespaces: 
```
kubectl create ns app-dev
kubectl create ns app-staging
kubectl create ns app-prod
```
Et ajouter les labels:
```
kubectl label namespaces app-dev app.kubernetes.io/part-of=demo-app
kubectl label namespaces app-dev environment=dev
kubectl label namespaces app-dev owner=platform-team
kubectl label namespaces app-staging owner=platform-team
kubectl label namespaces app-staging app.kubernetes.io/part-of=demo-app
kubectl label namespaces app-staging environment=staging
kubectl label namespaces app-prod app.kubernetes.io/part-of=demo-app
kubectl label namespaces app-prod environment=prod
kubectl label namespaces app-prod owner=platform-team
```
La commande `kubectl get ns --show-labels` devrait afficher : 
```
NAME              STATUS   AGE     LABELS
app-dev           Active   5m42s   app.kubernetes.io/part-of=demo-app,environment=dev,kubernetes.io/metadata.name=app-dev,owner=platform-team
app-prod          Active   5m35s   app.kubernetes.io/part-of=demo-app,environment=prod,kubernetes.io/metadata.name=app-prod,owner=platform-team
app-staging       Active   5m38s   app.kubernetes.io/part-of=demo-app,environment=staging,kubernetes.io/metadata.name=app-staging,owner=platform-team
```

# Etape 3

```
kubectl config set-context dev-user@app-cluster --cluster='minikube' --user='dev-user'
kubectl config set-credentials dev-user --username=dev-user --password=dev-password

kubectl config set-context qa-user@app-cluster --cluster='minikube' --user='qa-user'
kubectl config set-credentials qa-user --username=qa-user --password=qa-password
```
Note : il faut configurer les users avec une authentification valide (par exemple avec des token)

# Etape 4
```
kubectl apply -f role-dev.yaml
kubectl apply -f rolebinding-dev.yaml
kubectl apply -f role-staging.yaml
kubectl apply -f rolebinding-staging.yaml
```

# Etape 5
```
kubectl apply -f role-prod.yml
kubectl apply -f deployer-prod.yml
kubectl apply -f rolebind-prod.yml

kubectl create token prod-deployer -n app-prod
```
Copier le token donné, puis : 
```
kubectl config set-credentials prod-deployer --token=<TOKEN>
kubectl config set-context prod-deployer@app-cluster --cluster=minikube --user=prod-deployer --namespace=app-prod
```

# Etape 6