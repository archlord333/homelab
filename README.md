# homelab

## Flux Bootstrap Setup

1. Install Flux CLI on system with `curl -s https://fluxcd.io/install.sh | sudo FLUX_VERSION=2.0.0 bash`
1. I ended up having to install Flux CLI on my Linux Destop to run the flux bootstrap with k3s. Did this with `yay -Syy flux-bin`.
1. Logged into GitHub > Settings > Developer Settings > Personal access tokens > Fine-grained tokens > made `homelab-flux-read-token` to only allow access to single homelab repo for Repo/Contents as `Read and write`. Expires October 3, 2025.
1. `export GITHUB_TOKEN="{Token Here}"`
1. `flux bootstrap github --token-auth --owner=archlord333 --repository=homelab --branch=main --path=k3s/prod-cluster --personal --components="source-controller,kustomize-controller,notification-controller" --interval=5m0s` 
