# Comandos Kubernetes

**Kubectl get nodes**  obteniendo los nodos, es decir todos los clusters creados

**kubectl get nodes -o wide** ver más a detalle el nodo o cluster

**minikube start -p desarrollo** indicamos que vamos a hacer un nuevo cluster llamado desarrollo

**minikube profile** indica en que perfil o cluster estamos

**minikube profile list** se muestran todos los clusters

**minikube profile desarrollo** indicamos que nos cambiamos al cluster de desarrollo

**minikube delete** eliminamos un cluster, pero hay que asegurarse cual cluster se desea eliminar, se puede saber por medio del minikube profile, una vez revisado la información procedemos a ejecutar el comando
