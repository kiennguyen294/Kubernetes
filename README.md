# Kubernetes
## Enabling shell autocompletion
```
sudo apt-get install bash-completion
echo "source <(kubectl completion bash)" >> ~/.bashrc
source .bashrc
```
## Install helm
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh
```
## Install kube dashboard 
### Deploy kube dashboard using kubectl
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta6/aio/deploy/recommended.yaml
```
### Authen
#### Create service account
```
kubectl create serviceaccount dashboard-admin-sa
kubectl create clusterrolebinding dashboard-admin-sa --clusterrole=cluster-admin --serviceaccount=default:dashboard-admin-sa
```

## Intall Rook Ceph
```
git clone https://github.com/rook/rook.git
cd rook/cluster/examples/kubernetes/ceph/
kubectl apply -f common.yaml
kubectl apply -f operator.yaml 
kubectl apply -f cluster-test.yaml
```
### Check rook ceph
```
kubectl apply -f toolbox.yaml
kubectl exec -it rook-ceph-tools-76c7d559b6-td9gd -n rook-ceph sh
# ceph -s
```

## Set default storage class
```
kubectl patch storageclass <storage-class-name> -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```

## Fix bug delete namespace stuck
```
NAMESPACE=your-rogue-namespace
kubectl proxy &
kubectl get namespace $NAMESPACE -o json |jq '.spec = {"finalizers":[]}' >temp.json
curl -k -H "Content-Type: application/json" -X PUT --data-binary @temp.json 127.0.0.1:8001/api/v1/namespaces/$NAMESPACE/finalize
```
