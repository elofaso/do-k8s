# DigitalOcean Kubernetes Set Up
1. Install and configure doctl https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/
2. Create Kubernetes cluster.
>doctl kubernetes cluster create \<cluster-name\> --node-pool "auto-scale=true;min-nodes=1;max-nodes=5"
3. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
4. Create Docker repository.
>doctl registry create \<globally-unique-registry-name\>
5. Add container registry support to the docker cluster.
>doctl kubernetes cluster registry add \<cluster-name\> 
6. Log in docker to registry.
>doctl registry login
7. Install Kubernetes metrics server.
>kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
8. Install Kubernetes Redis failover operator.
>kubectl create -f https://raw.githubusercontent.com/spotahome/redis-operator/master/example/operator/all-redis-operator-resources.yaml
9. Edit k8s/node-deployment.yaml to replace 'hello' with your app name, 'elofaso/node-hello' with your repository-name/image-name. Replace Load Balancer size 'lb-small with 'lb-medium' or 'lb-large', if desired; Load Balancer cannot be resized.
10. Deploy Node app and Redis to Kubernetes cluster.
>cd k8s
>kubectl apply -f .
