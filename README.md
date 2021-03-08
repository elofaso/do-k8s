# DigitalOcean Kubernetes Set Up
1. Install doctl https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/
2. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
3. Create Kubernetes cluster
>doctl k8s cluster create <cluster name> --node-pool "auto-scale=true;min-nodes=1;max-nodes=3"

