# Podman Desktop

Podman Desktop is a free, open-source GUI for managing containers and local Kubernetes clusters on macOS — a Docker Desktop alternative.

---

## Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Skip if already installed. Homebrew is the package manager used for everything below.

---

## Install Podman Desktop

```bash
brew install podman-desktop
```

Open **Finder** (`⌃ + ⌥ + F`), go to **Applications**, and launch **Podman Desktop**. Follow the setup wizard and click **Install** when prompted.

---

## Install Podman CLI

```bash
brew install podman
```

Then initialize and start the Podman machine:

```bash
podman machine init
podman machine start
```

Verify it is running:

```bash
podman info
```

---

## Install kubectl and kind

```bash
brew install kubectl kind
```

`kubectl` is the Kubernetes CLI. `kind` runs clusters inside Podman containers. Verify both:

```bash
kubectl version --client
kind version
```

---

## Install Helm

```bash
brew install helm
```

Helm is the Kubernetes package manager used to deploy charts. Verify:

```bash
helm version
```

---

## Create a Kubernetes Cluster

```bash
export KIND_EXPERIMENTAL_PROVIDER=podman
kind create cluster --name dev-cluster
```

This tells Kind to use Podman as the container provider, then creates a cluster named `dev-cluster`. Verify it is running:

```bash
kubectl cluster-info --context kind-dev-cluster
```

Open **Podman Desktop**, click the **Kubernetes** icon in the left sidebar — you should see `kind-dev-cluster` listed as the active context.

---

## Switch Context

```bash
kubectl config use-context kind-dev-cluster
```

Use this when you have multiple clusters and need to switch between them. List all contexts:

```bash
kubectl config get-contexts
```

---

## Delete the Cluster

```bash
kind delete cluster --name dev-cluster
```

Removes the cluster when you no longer need it.

---

## Quick Setup

Already read this before? Run this and you're done.

```bash
# Install everything
brew install podman-desktop podman kubectl kind helm

# Start Podman
podman machine init
podman machine start

# Create cluster
export KIND_EXPERIMENTAL_PROVIDER=podman
kind create cluster --name dev-cluster

# Verify
kubectl cluster-info --context kind-dev-cluster
```
