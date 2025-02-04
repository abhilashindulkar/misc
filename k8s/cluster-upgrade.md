## Cluster Upgrade process

3 Strategies
- All at once -- will have downtime
- one at a time -- workload would get shifted to other nodes
- introducing new nodes with latest version of required components & deleting redundant nodes.
  
#### With kubeadm

apt-get upgrade -y kubeadm=1.18.0-00

#### kubelet upgrade
on node

kubectl drain node01

apt-get upgrade -y kubeadm=1.18.0-00
apt-get upgrade -y kubelet=1.18.0-00

kubeadm upgrade node config --kubelet-version v1.18.0
systemctl restart kubelet

kubectl uncordon node01
