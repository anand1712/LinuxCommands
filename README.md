# Welcome to my Linux Commands Page

# GIT
#### Reset a Branch to another Branch
```
git checkout mybranch
git reset --hard mainbranch
```
#### Cherrypick a commit from a different branch
```
git cherrypick <commitid>
```
#### Delete a branch from remote
```
git push -d <branch name>
```
#### Create a Patch from last commited change
```
git diff HEAD~ > <somefile>.diff
```
#### Apply a Patch from diff
```
git apply < <somefile>.diff
```
# Linux
#### List of open files by a process
```
lsof -p <pid>
```
# Docker
#### Delete all docker images from the system
```
docker rmi -f `docker images -aq`
```

# OpenSSL
#### Creating a CA
```
openssl req -new -x509 -days 9999 -keyout ca-key.pem -out ca-crt.pem -addext basicConstraints=critical,CA:TRUE,pathlen:1 -subj "/C=IN/ST=TN/CN=ca.localhost" -addext "subjectAltName = DNS:ca.localhost"
```

#### Creating a Server Certificate from CA
```
openssl genrsa -out server-key.pem 4096
openssl req -new -key server-key.pem -out server-csr.pem -subj "/C=IN/ST=TN/CN=server.localhost" -addext "subjectAltName = DNS:server.localhost"
openssl x509 -req -days 9999 -in server-csr.pem -CA ca-crt.pem -CAkey ca-key.pem -CAcreateserial -out server-crt.pem -extfile <(printf "subjectAltName=DNS:server.localhost")
openssl verify -CAfile ca-crt.pem server-crt.pem
```

#### Creating a Client Certificate from CA
```
openssl genrsa -out client1-key.pem 4096
openssl req -new -key client1-key.pem -out client1-csr.pem -subj "/C=IN/ST=TN/CN=client1.localhost" -addext "subjectAltName = DNS:client1.localhost"
openssl x509 -req -days 9999 -in client1-csr.pem -CA ca-crt.pem -CAkey ca-key.pem -CAcreateserial -out client1-crt.pem -extfile <(printf "subjectAltName=DNS:client1.localhost")
openssl verify -CAfile ca-crt.pem client1-crt.pem
```

#### Print a Openssl Certificate
```
openssl x509 -noout -text -in server-crt.pem
openssl x509 -noout -text -in client1-crt.pem
openssl x509 -noout -text -in ca-crt.pem
```

# GRPC
#### Generating go stubs from the proto file
```
protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative <filename>.proto
```
# Kubernetes
```
kubeadm reset
ctr -n k8s.io c rm $(ctr -n k8s.io c ls -q)
ctr -n k8s.io i rm $(ctr -n k8s.io i ls -q )
kubeadm init --pod-network-cidr=192.168.0.0/16 
rm -rf $HOME/.kube
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifests/tigera-operator.yaml
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifests/custom-resources.yaml
kubectl taint node master-node node-role.kubernetes.io/control-plane:NoSchedule-
kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/v0.0.24/deploy/local-path-storage.yaml
kubectl patch storageclass local-path -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```
