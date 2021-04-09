# k8s
Dicas k8s

Setup inicial 

cat "net.bridge.bridge-nf-call-iptables = 1" > /etc/sysctl.conf
echo '1' > /proc/sys/net/ipv4/ip_forward
sysctl --system

modprobe overlay
modprobe br_netfilter

Configurar hostname em kd nó
hostnamectl set-hostname HOSTNAME

Instalação conteinerd 
apt update
apt-get install containerd -y
mkdir -p /etc/containerd
containerd config default  /etc/containerd/config.toml

Instalação k8s

curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"


apt-get install kubeadm kubelet kubectl -y

kubeadm init --apiserver-advertise-address 192.168.33.88
kubeadm init --apiserver-cert-extras-sans IP-PUBLIC
 
 
Instalar um addions de redes
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
 
 
Criar um app de test
kubectl create deployment nginx --image nginx
kubectl expose deployment nginx --type NodePort --port 80


Pegar o token de adição de nós 

kubeadm  token create print-join-command
 
kubeadm reset 
