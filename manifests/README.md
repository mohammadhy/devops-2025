> [!TIP]
> setup insecure registry for containerd (DEPRECATED)
```
       [plugins."io.containerd.grpc.v1.cri".registry]
      [plugins."io.containerd.grpc.v1.cri".registry.mirrors]
        [plugins."io.containerd.grpc.v1.cri".registry.mirrors."IP:PORT"]
          endpoint = ["http://IP:PORT"]
        [plugins."io.containerd.grpc.v1.cri".registry.configs."IP:PORT".tls]
          insecure_skip_verify = true
        [plugins."io.containerd.grpc.v1.cri".registry.configs."IP:PORT".auth]
           password = "admin"
           username = "admin"
```
> [!TIP]
> setup insecure registry for containerd (NEW Version)
```
    vim /etc/containerd/certs.d/docker.io/hosts.toml
    server = "http://192.168.1.105:5000"
    [host."http://192.168.1.105:5000"]
      capabilities = ["pull","resolve", "push"]
      skip_verify = true
     override_path = false
      username = "admin"
      password = "123"
```
## To Install Ceph As StorageClass:
    kubectl apply -f manifest/ceph
    kubectl apply -f https://raw.githubusercontent.com/ceph/ceph-csi/master/deploy/rbd/kubernetes/csi-provisioner-rbac.yaml
    kubectl apply -f https://raw.githubusercontent.com/ceph/ceph-csi/master/deploy/rbd/kubernetes/csi-nodeplugin-rbac.yaml
    wget https://raw.githubusercontent.com/ceph/ceph-csi/master/deploy/rbd/kubernetes/csi-rbdplugin-provisioner.yaml
    kubectl apply -f csi-rbdplugin-provisioner.yaml
## To Install Nfs Server:
    apt install nfs-server
    vi /etc/export
    <Path> <CLIENT-IP>(rw, sync, no_root_squash)
## Create StorageClass Nfs
    helm repo add nfs-subdir-external-provisioner https://kubernetes-sigs.github.io/nfs-subdir-external-provisioner
    helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner --create-namespace --namespace nfs-provisioner --set nfs.server=<ip> --set nfs.path=/data
## To Install prometheus Operator:
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    kubectl apply -f manifest/prometheus/rbac
    helm install prometheus prometheus-community/kube-prometheus-stack -f values.yaml --create-namespace --namespace monitoring
## To Install Metallb:
    kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.7/config/manifests/metallb-native.yaml
    kubectl apply -f metallb-ip-pool.yaml
## To Install Nginx-Ingress
       kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
## To Install Argocd And Argocd Rollout:
    helm upgrade --install argocd argo/argo-cd --namespace argocd -f argocd-values.yaml --create-namespace
    kubectl create namespace argo-rollouts
    kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
    curl -LO https://github.com/argoproj/argo-rollouts/releases/latest/download/kubectl-argo-rollouts-amd64
    chmod +x ./kubectl-argo-rollouts-darwin-amd64
    sudo mv ./kubectl-argo-rollouts-darwin-amd64 /usr/local/bin/kubectl-argo 
    kubectl-argo rollouts version --kubeconfig 
## SonarQube
   Create Key On Sonarqube
   Install Plugins On Jenkins
   1) go to managejenkins
   2) Section SonarQube servers
   3) Put Ip Address Sonar
   4) Put Key On Credentials
   5) EX For Python : /var/lib/jenkins/sonar-cli/bin/sonar-scanner -Dsonar.projectKey=<Project-Name> -Dsonar.sources=.  -Dsonar.exclusions=<file/folder not scan>
## Move Image Docker To Containerd:
    docker save -o image.tar <image-name>
    sudo scp IP:<PATH> image.tar
    sudo ctr -n=k8s.io images import image.tar
## Use Trivy Offline Scanner
    snap install oras --classic
    oras cp ghcr.io/aquasecurity/trivy-db:2 --to-plain-http 192.168.1.104:5000/trivy/trivy-db:2
    TRIVY_USERNAME=YOUR_USERNAME TRIVY_PASSWORD=YOUR_PASSWORD trivy image --db-repository 192.168.1.104:5000/trivy/trivy-db:2 -f json -o trivy.json 192.168.1.104:5000/python-web-app:v1 
    ### use Trivy Local DB
    docker run --rm -v $PWD:/app -v /var/run/docker.sock:/var/run/docker.sock 192.168.1.5:5000/aquasec/trivy:0.58.0 image --db-repository $REGISTERY/aquasecurity/trivy-db:2 --java-db-repository $REGISTERY/aquasecurity/trivy-java-db:1 -f json -o /app/trivy.json  $REGISTERY/$IMAGE:$CI_COMMIT_SHORT_SHA'''
    
## Use Metrics-server 
    kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/high-availability-1.21+.yaml
        kubectl -n kube-system edit deployment metrics-server
    - --kubelet-insecure-tls
## Use Gvisor As Runtime 
    change config.toml And Add 
            [plugins."io.containerd.grpc.v1.cri".containerd.runtimes.runsc]
          runtime_type = "io.containerd.runsc.v1"
          [plugins."io.containerd.grpc.v1.cri".containerd.runtimes.runsc.options]
            binaryName = "/usr/local/bin/runsc"
## To Have App In App Argocd 
   
   argocd app create app-of-app-voting --dest-namespace argocd --dest-server https://kubernetes.default.svc --repo http://192.168.1.109/root/voting-app-requirment.git --path ./argo_app_in_app/ --sync-policy auto
