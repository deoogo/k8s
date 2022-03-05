<h1> Conteiners </h1>


### Build Dockerfile
* docker image build -t userDockerHub/nome:TAG.
* docker images ls
* docker container run -d userDockerHub/nome:TAG
* docker container ls


### Registry docker
* docker images tag IDconteiner userDockerHub/nome:TAG
* docker login registry.com
* docker push userDockerHub/nome:TAG
* docker pul userDockerHub/nome:TAG

### Comandos docker 

* docker container run -it IMAGE
* docker run -d -p 0:0
* docker exec -it conteiner /bash ou sh

### Volume


* docker run -ti --mount type=bind.src=caminhoHost.dist=/caminhoConteiner IMAGEM

* docker volume ls

* docker volume create **nome**

* docker volume inspect **nome**


* docker run -ti --mount type=**volume**.src=**nome**.dist=/caminhoConteiner IMAGEM


 


* docker volume prune
 
### Instalar um addions de redes

* kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
 
 
### Criar um Deployment de teste
* kubectl create deployment nginx --image nginx
* kubectl expose deployment nginx --type NodePort --port 80


### Pegar o token de adição de nós 

* kubeadm  token create print-join-command
 
* kubeadm reset 

### Comandos utéis
* kubectl (pods|services|) --all-namespaces -> Listar pods ou services

* kubectl logs nomeDoPod -n namespace -> Logs do pods


* kubectl exec -ti my_pod-79d7766cb8-2shml -- bash -> logar no conteiner


* kubectl top pods -n namespace -> Mem/Cpu/disco dos Pods

* kubectl top nodes -n namespace -> Mem/Cpu/disco dos nós


* kubectl get pods -n name 

* kubectl describe pod NomedoPod -n namespace


* kubectl get hpa -n namespace

* kubectl edit hpa  NOMEDOHPA -n namespace -->  Alterar as variaveis target / max e min / current e desired


* kubectl get deployments -n namespace

* kubectl edit deployments NOMEDODEPLOYMENTS -n namespace

### HELM

* helm repo list --> Lista seu repo local do HELM

* helm install prometheus prometheus-community/prometheus --> Exemplo pratico de uma instalação 

* helm upgrade nome_realese projeto/helm --set key=value --> Alterar um paramentro do manifesto do k8s

* helm show values projeto/helm > values.yaml --> lista os valores do helm chart

* helm upgrade nome_realese projeto/helm -f values.yaml  --> Aplicando as alterações do values.yaml

* helm uninstall  prometheus --> Desistalar 



 

