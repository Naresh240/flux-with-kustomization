# flux-with-kustomization

# Installing flux
    wget https://github.com/fluxcd/flux2/releases/download/v0.27.4/flux_0.27.4_linux_amd64.tar.gz 
    tar xvf flux_0.27.4_linux_amd64.tar.gz
    mv flux /usr/bin
# Create github token
    export GITHUB_TOKEN="provide github token"
# Flux Bootstraping
    export GITHUB_USER="naresh240"
    export GITHUB_REPO="flux-with-kustomization"
    export GITHUB_BRANCH="feature/naresh"
    export GITHUB_DIR="./clusters"
  
    flux bootstrap github \
      --owner=$GITHUB_USER \
      --repository=$GITHUB_REPO \  
      --branch=$GITHUB_BRANCH \
      --path=$GITHUB_DIR \
      --token $GITHUB_TOKEN
# Tell Flux to pull the manifests from Git and upgrade itself with:
    flux reconcile source git flux-system
# Verify that the controllers have been upgrade with:
    flux check
