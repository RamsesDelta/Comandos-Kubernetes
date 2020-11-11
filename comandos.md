# Comandos Kubernetes

**Kubectl get nodes** : obteniendo los nodos, es decir todos los clusters creados

**kubectl get nodes -o wide** : ver más a detalle el nodo o cluster

**minikube start -p desarrollo** : indicamos que vamos a hacer un nuevo cluster llamado desarrollo

**minikube profile** : indica en que perfil o cluster estamos 

**minikube profile list**  : se muestran todos los clusters

**minikube profile desarrollo** : indicamos que nos cambiamos al cluster de desarrollo

**minikube delete** : eliminamos un cluster, pero hay que asegurarse cual cluster se desea eliminar, se puede saber por medio del minikube profile, una vez revisado la información procedemos a ejecutar el comando

**kubectl run nginx1 –image=nginx** : con este comando indicamos que se va crear un POD con su nombre y a su vez la imagen en la que está basada

**kubectl get pods** : para ver los pods que hay

**kubectl get pods -o wide** : para ver los pods a grandes rasgos

**kubectl describe pod/nginx1** : para ver un POD con todas sus características con más detalle

**kubectl logs apache** : para ver los logs del POD

**kubectl logs -f apache** : para seguir los logs de un POD pero sé que siguiendo cada mensaje nuevo 

**kubectl logs apache --tail=30** : se indica que queremos ver los últimos logs pero en líneas, en este caso se mostraran los 30 últimas líneas 

**kubectl delete pods apache** : para eliminar un POD ya se que agregar la s o sin la s del pods

**kubectl create -f nginx.yaml** : para construir un POD a partir de un archivo manifest 

**kubectl get pod nginx1 -o yaml** : para obtener el yml de un pod

**kubectl get pod nginx1 -o json > fi.json** : para convertir la información del pod ya sea en yml o json y guardarlo 

**kubectl delete pod apache --grace-period=5** : para borrar un POD pero va esperar 5 segundos pasando eso se borra el POD

**kubectl delete pod apache --now** : para borrar el POD indemdiatamente, este se utiliza cuando el POD al borrar se queda trabado

**kubectl delete pods -- all** : borra todos los pods y no avisa cuando se eliminan todos  

**kubectl logs apache -c redis-django** : este sirve para ver los logs de un contenedor en específico, ya que podemos tener mas de un contenedor en un solo POD

**kubectl apply -f nginx.yaml** : sirve para crear y modificar aun POD, ya que si no ponemos el apply nos arroja un error diciendo que ya existe el POD, si no existe el POD lo crea y si existe pues modifica algo que tu le indiques 

**kubectl get pod tomcat --show-labels** : para ver las etiquetas de un POD

**kubectl get pod tomcat --show-labels -L estado** : mostrar o escoger la etiqueta con la que estamos llamando en este caso estado es el nombre de la etiqueta que nombramos 

**Kubectl label pod tomcat responsable=ramses** : para agregar otra etiqueta 

**kubectl get pod tomcat --show-labels -L estado,responsable** : para ver mas de una etiqueta en especifico 

**kubectl label --overwrite pod tomcat estado=test** : para modificar el valor de una etiqueta

**kubectl label pod tomcat responable-** : para eliminar un etiqueta

**kubectl get pods --show-labels -l estado==desarrollo** : este sirve para hacer un filtrado de etiquetas que tenga la etiqueta de estado y su valor de desarrollo, por lo que saldrán todos los PODS que tengan dichas etiquetas

**kubectl get pods --show-labels -l 'estado in(desarrollo)' : se supone que con esta comando se obtiene los PODS que incluyan esta etiqueta

**kubectl get pods --show-labels -l 'estado in(desarrollo,testing)'** : al igual que el comando de arriba sirve igual pero con la diferencia que se le agrega otra otro valor a lo que debería de tener la etiqueta

**kubectl delete pods -l estado=desarrollo** : eliminara todos los PODS que tengan esa etiqueta con su respectivo valor

**kubectl create deployment apache --image=httpd** : para crear un deployment con una imagen

**kubectl get deploy** : obtener los deploys

**kubectl get rs** : para ver la replicas

**kubectl describe deploy apache** : para ver la información de un deploy

**kubectl get deploy apache -o yaml** : para ver la información del deploy pero en formato yaml, además se puede también en formato json, este comando se vio también para los PODS

**kubectl get pods -l app=nginx** : obteniendo todos los pods que tengan la etiqueta de app cuyo valor es de nginx

**kubectl scale deploy nginx-d --replicas=5** : para agregar otras replicas para que den un total de cinco 

**kubectl scale deploy -l deploy estado=1 --replicas=10** : este comando sirve para poder editar un deploy en específico por medio de una etiqueta llamada estado cuyo calor sea o es de 1, se va a editar la escala de las replicas

**kubectl expose deployment web-d --name=web-svc --target-port=80 --type=NodePort** : este comando sirve para exponer un servicio, se le indica el nombre del servicio, el puerto y por ultimo el tipo de nodo 

**kubectl get svc** : para ver los service port que hay 

**kubectl describe svc web-svc** : muestra información de un servicio en especifico 
Para poder acceder al nodo exterior, tenemos que revisar la ip del node, ejemplo minikube ip, dicha ip la tenemos que colocar en el navegador, seguido de el puerto que buscamos el NodePort que tenga el servicio que creamos para establecer la comunicación con los PODS
