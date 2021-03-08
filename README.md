# DigitalOcean Kubernetes Set Up
* Install doctl https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/
* Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
* Create Kubernetes cluster
doctl k8s cluster create <cluster name> --node-pool "auto-scale=true;min-nodes=1;max-nodes=3"

