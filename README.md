# Déploiement avec Minikube et Kustomize

Ce document fournit des instructions pour démarrer un cluster Kubernetes local à l'aide de Minikube et appliquer des configurations avec Kustomize.

## Prérequis

Avant de commencer, assurez-vous d'avoir installé les éléments suivants :

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Instructions

1. **Lancer Docker Desktop :**

   Assurez-vous que Docker Desktop est en cours d'exécution avant de continuer.

2. **Démarrer Minikube avec Docker comme pilote :**

```bash
minikube start --driver=docker
```  

![Start_Minikube](docs/img/minikube_start.png)

On voit bien que minikube a bien démarré avec l'aide de docker-desktop puisqu'on a bien précisé le driver docker dans la commande.

3. Vérifier l'état de Minikube :

```bash
minikube status
```

![Status_Minikube](docs/img/minikube_status.png)

On voit bien que minikube est bien en marche

Appliquer les configurations avec Kustomize

1. Naviguer vers le répertoire contenant les fichiers Kustomize :


```bash
cd kustomize/
```

![Cd_Kustomize](docs/img/cd_kustomize.png)

2. Appliquer les configurations Kubernetes :

```bash
kubectl apply -k .
```

![Kubectl_Apply](docs/img/kubectl_apply.png)

On voit que tous les services sont bien créés.

Vérifier les ressources Kubernetes

Après avoir appliqué les configurations, vous pouvez vérifier l'état des différentes ressources :

Lister les pods :
```bash
kubectl get pods
```

![Kubectl_Get_Pods](docs/img/kubectl_get_pods.png)

Lister les services :
```bash
kubectl get services
```

![Kubectl_Get_Services](docs/img/kubectl_get_services.png)

Lister les déploiements :
```bash
kubectl get deployments
```

![Kubectl_Get_Deployments](docs/img/kubectl_get_deployments.png)

Tunnel Minikube

Pour accéder aux services exposés, vous pouvez créer un tunnel avec la commande suivante :

```bash
minikube tunnel
```

![Minikube_Tunnel](docs/img/minikube_tunnel.png)

Cela vous permettra d'accéder aux services via leur adresse IP. Une fois le tunnel en cours d'exécution, l'application déployée sera accessible à l'adresse suivante :

Application déployée : http://localhost

![App_Deployed](docs/img/app_deployed.png)

# Déploiement avec ArgoCD

## Installation d'ArgoCD

![Create_Namespace_Argocd](docs/img/create_namespace_argocd.png)
![Install_Argocd](docs/img/install_argocd.png)

## Exposition d'Argocd

![Expose_Argocd](docs/img/kubectl_port_forward.png)

## Récupération du mot de passe initial de l'admin

![Get_Password_Admin](docs/img/get_password_kubectl.png)

## Création de l'application via l'interface web d'ArgoCD

![Create_App](docs/img/create_app.png)

![Create_App_Ui](docs/img/create_app_ui.png)

![Create_App_Ui2](docs/img/create_app_ui2.png)

![Create_App](docs/img/create.png)

## Synchronisation de l'application via l'interface web d'ArgoCD

![Sync_App](docs/img/home_app.png)

![Sync_Button](docs/img/sync_app_ui.png)

![Sync_App2](docs/img/app_synced.png)