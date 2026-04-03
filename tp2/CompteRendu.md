Dans ce TP Minikube, j’ai déployé une application nginx à l’aide d’un Deployment puis exposé celle-ci via un Service.
Pour vérifier le bon fonctionnement du cluster et des ressources, j’ai utilisé les commandes `kubectl get nodes`, `kubectl get pods` et `kubectl get svc`.
J’ai également utilisé `kubectl describe pod` pour diagnostiquer plus finement l’état des conteneurs.

Le service a été exposé en utilisant un Service de type `ClusterIP`, permettant une communication interne dans le cluster.
Pour tester l’accès, j’ai utilisé `kubectl port-forward svc/web-nginx-svc 8080:80`, ce qui m’a permis d’accéder à nginx depuis mon navigateur.

Une première difficulté a été un problème de labels entre le Deployment et le Service, empêchant la liaison correcte.
Je l’ai résolu en vérifiant que le label `app: web-nginx` était identique dans le selector et les pods.

Une deuxième difficulté concernait l’accès au service depuis l’extérieur.
J’ai compris que `ClusterIP` n’est pas accessible directement, et j’ai donc utilisé le port-forward pour contourner cette limitation.
