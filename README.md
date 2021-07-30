<h1> Conteiners </h1>

Build Dockerfile
docker image build -t nome:1.0 .

docker images ls
docker container run -d nome:1.0
docker container ls

Volume

docker run -ti --mount type=bind.src=caminhoHost.dist=/caminhoConteiner IMAGEM
docker volume ls
docker volume create **nome**
docker volume inspect **nome**

docker run -ti --mount type=**volume**.src=**nome**.dist=/caminhoConteiner IMAGEM

docker run -d -p 0:0 

docker volume prune
 
# Instalar um addions de redes
* kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
 
 
# Criar um app de test
* kubectl create deployment nginx --image nginx
* kubectl expose deployment nginx --type NodePort --port 80


# Pegar o token de adição de nós 

* kubeadm  token create print-join-command
 
* kubeadm reset 

# Comandos utéis 
* kubectl logs nomeDoPod -n namespace


* kubectl top pods -n namespace

* kubectl top nodes -n namespace

* kubectl get pods -n name 
* kubectl describe pod NomedoPod -n namespace


* kubectl get hpa -n namespace

* kubectl edit hpa  NOMEDOHPA -n namespace -->  Alterar as variaveis target / max e min / current e desired


* kubectl get deployments -n namespace

* kubectl edit deployments NOMEDODEPLOYMENTS -n namespace



