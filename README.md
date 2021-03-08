# DigitalOcean Kubernetes Set Up
1. Install doctl https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/
2. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
3. Create Kubernetes cluster
>doctl k8s cluster create <cluster-name> --node-pool "auto-scale=true;min-nodes=1;max-nodes=5"
4. Create Docker repository
>doctl registry create <globally-unique-registry-name>
5. Add container registry support to the docker cluster
>doctl kubernetes cluster registry add <cluster-name> <cluster-name> 
6. Generate DigitalOcean API token https://cloud.digitalocean.com/account/api/token
7.Login Docker to registry
>doctl registry login
Install Kubernetes metrics server
>kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
Install Kubernetes Redis failover operator
>kubectl create -f https://raw.githubusercontent.com/spotahome/redis-operator/master/example/operator/all-redis-operator-resources.yaml
Deploy Node and Redis to Kubernetes cluster
>cd k8s
>kubectl apply -f .

