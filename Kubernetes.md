Adding Calico to a cluster
curl https://docs.projectcalico.org/manifests/calico.yaml -O
kubectl apply -f calico.yaml

If NFT is to be enabled 
FELIX_IPTABLESBACKEND - NFT

Remove taints from master
kubectl taint nodes --all node-role.kubernetes.io/master-
