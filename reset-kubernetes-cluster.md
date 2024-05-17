Source: https://www.aii-3.com/wp-content/uploads/2023/01/DevOps-How-to-Reset-Kubernetes-Cluster.pdf

Solution
#Reset kubernetes cluster using kubeadm
kubeadm reset -f
#Remove all the data from all below locations
rm -rf /etc/cni /etc/kubernetes /var/lib/dockershim /var/lib/etcd /var/lib/kubelet /var/run/kubernetes ~/.kube/*
#Flush all the firewall (iptables) rules
iptables -F && iptables -X
iptables -t nat -F && iptables -t nat -X
iptables -t raw -F && iptables -t raw -X
iptables -t mangle -F && iptables -t mangle -X
#Restart the Docker service
systemctl restart docker