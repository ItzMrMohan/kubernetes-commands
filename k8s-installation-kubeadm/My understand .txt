#-------------------Ubuntu-----------------#
#-------------------Both Master and worker-----------------#

*   sudo su
*   apt update
*   apt upgrade
*   apt-get update
*   apt install net-tools
*   apt install nano
*   apt install vim
*   hostname
*   apt-get install docker.io -y
*   service docker restart
*   service docker status
*   docker version
*   curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
*   echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" >/etc/apt/sources.list.d/kubernetes.list
*   apt-get update
*   apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
*   service kubelet status
*   kubeadm version
*   kubelet version


#------------------------Only Master---------------------#
*   kubeadm init

*   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
*   sudo chown $(id -u):$(id -g) $HOME/.kube/config

*   kubectl apply -f https://docs.projectcalico.org/v3.8/manifests/calico.yaml

#-------------------------Run on worker-----------------------#
kubeadm join 10.128.0.30:6443 --token tk9w52.29sd3hh5afqmnbgz \
    --discovery-token-ca-cert-hash sha256:0123e7c42d8d1a82508d6a36d0d027653a3d319a6e054abe69340f2ff18d2926


*   sudo systemctl restart kubelet
*   sudo systemctl status kubelet

