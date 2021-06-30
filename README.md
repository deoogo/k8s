# k8s sem o docker

<h1> Dicas k8s </h1>

<h2> Setup inicial Kubernetes </h2> 

* cat "net.bridge.bridge-nf-call-iptables = 1" > /etc/sysctl.conf
* echo '1' > /proc/sys/net/ipv4/ip_forward
* sysctl --system

* modprobe overlay && modprobe br_netfilter


# Configurar hostname em kd nó

* hostnamectl set-hostname HOSTNAME

# Instalação conteinerd 
* apt update && apt-get install containerd -y

* mkdir -p /etc/containerd
* containerd config default  /etc/containerd/config.toml

# Instalação k8s

* curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
* apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main" && apt update

* apt-get install kubeadm kubelet kubectl -y

# Setar o ip em cada maquina do cluster no default do kubelet

* echo "KUBELET_EXTRA_ARGS=--node-ip=192.168.33.11" > /etc/default/kubelet

* kubeadm init --apiserver-advertise-address="192.168.33.10" --apiserver-cert-extra-sans="192.168.33.10"  --node-name master --pod-network-cidr=192.168.0.0/16
 
 
# Instalar um addions de redes
* kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
 
 
# Criar um app de test
* kubectl create deployment nginx --image nginx
* kubectl expose deployment nginx --type NodePort --port 80


# Pegar o token de adição de nós 

* kubeadm  token create print-join-command
 
* kubeadm reset 

# Comandos utéis 

* kubectl top pods -n namespace

* kubectl top nodes -n namespace

* kubectl get pods -n namespace

* kubectl get hpa -n namespace

* kubectl edit hpa  NOMEDOHPA -n namespace -->  Alterar as variaveis target / max e min / current e desired


* kubectl get deployments -n namespace

* kubectl edit deployments NOMEDODEPLOYMENTS -n namespace



