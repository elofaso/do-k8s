# DigitalOcean Kubernetes Set Up
1. Install doctl https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/
2. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
3. Create Kubernetes cluster.
>doctl k8s cluster create <cluster-name> --node-pool "auto-scale=true;min-nodes=1;max-nodes=5"
4. Create Docker repository.
>doctl registry create \<globally-unique-registry-name\>
5. Add container registry support to the docker cluster
>doctl kubernetes cluster registry add \<cluster-name\> 
6. Generate DigitalOcean API token https://cloud.digitalocean.com/account/api/token
7.Login Docker to registry. Paste API token.
>doctl registry login
8. Install Kubernetes metrics server.
>kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
9. Install Kubernetes Redis failover operator.
>kubectl create -f https://raw.githubusercontent.com/spotahome/redis-operator/master/example/operator/all-redis-operator-resources.yaml
10. Edit k8s/node-deployment.yaml to replace 'hello' with your app name, 'elofaso/node-hello' with your repository-name/image-name. Set Load Balancer size as lb-small, lb-medium, or lb-large; Load Balancer cannot be resized.
11. Deploy Node app and Redis to Kubernetes cluster.
>cd k8s
>kubectl apply -f .
