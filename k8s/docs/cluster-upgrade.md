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

---

### Official Documentation - kubeadm upgrade - controlplane

1. repository has been changed to pkg.k8s.io

   Use below command to repository definition

   echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list

2. Download signing key GPG

   curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

3. Update the latest patch release

   sudo apt update
   sudo apt-cache madison kubeadm

3. Upgrade kubeadm

   sudo apt-mark unhold kubeadm && \
   sudo apt-get update && sudo apt-get install -y kubeadm='1.30.x-*' && \
   sudo apt-mark hold kubeadm

4. Verify kubeadm version

   kubeadm version

5. Check target version we can upgrade to

   kubeadm upgrade plan

6. Upgrade the kubernetes components version - except kubelet.

   kubeadm upgrade apply v1.30.x

- other controlplanes -

  kubeadm upgrade node

7. Upgrade node (kubelet and kubectl)

   Prepare the node - drain all the workloads, mark it unshedulable

   kubectl drain node01 --ignore-daemonsets

8. Upgrade kubectl and kubelet

   sudo apt-mark unhold kubelet kubectl && \
   sudo apt-get update && sudo apt-get install -y kubelet='1.30.x-*' kubectl='1.30.x-*' && \
   sudo apt-mark hold kubelet kubectl

9. Restart the kubelet

    sudo systemctl daemon-reload
    sudo systemctl restart kubelet

10. Mark the node schedulable again

    kubectl uncordon node01

   


