# homelab

## Flux Bootstrap Setup

1. Install Flux CLI on system with `curl -s https://fluxcd.io/install.sh | sudo FLUX_VERSION=2.0.0 bash`
1. I ended up having to install Flux CLI on my Linux Destop to run the flux bootstrap with k3s. Did this with `yay -Syy flux-bin`.
1. Logged into GitHub > Settings > Developer Settings > Personal access tokens > Fine-grained tokens > made `homelab-flux-read-token-#` to only allow access to single homelab repo. Then, in permissions for Repository, allow Contents. I chose only `Read` this time around. Expires October of 2026.
1. `export GITHUB_TOKEN="{Token Here}"`
1. `flux bootstrap github --token-auth --owner=archlord333 --repository=homelab --branch=main --path=k3s/prod-cluster --personal --components="source-controller,kustomize-controller,notification-controller" --interval=5m0s`

# Flux Update Token

1. Regenerate Token in GitHub > Settings > Developer Settings > Personal access tokens > Fine-grained tokens > click `homelab-flux-read-token-#` that was recently expired, and then, regenerate a token that lasts for a chosen amount of time.
1. Update the k8s secret in flux-system.

# Accessing Homelab K3s Cluster

Use k9s or kubectl noob. :)
