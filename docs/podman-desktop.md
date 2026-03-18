# Podman Desktop

Podman Desktop is a free, open-source GUI for managing containers and local Kubernetes clusters on macOS — a Docker Desktop alternative.

## Prerequisites

1. Open Terminal (`⌘ + Space`, type Terminal) and install **Homebrew** if you don't have it:

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

## Install Podman Desktop

1. In Terminal, run:

   ```bash
   brew install podman-desktop
   ```

2. Open **Finder** (`⌃ + ⌥ + F`) and go to **Applications**. Double-click **Podman Desktop** to launch it.

3. Follow the on-screen setup wizard. When prompted, click **Install** to install the Podman engine.

## Install Podman CLI

1. In Terminal, run:

   ```bash
   brew install podman
   ```

2. Initialize and start the Podman machine:

   ```bash
   podman machine init
   podman machine start
   ```

3. Verify it is running:

   ```bash
   podman info
   ```

## Install kubectl and kind

`kubectl` is the Kubernetes CLI. `kind` runs clusters inside Podman containers.

1. In Terminal, run:

   ```bash
   brew install kubectl kind
   ```

2. Verify both are installed:

   ```bash
   kubectl version --client
   kind version
   ```

## Install Helm

Helm is the Kubernetes package manager used to install charts.

1. In Terminal, run:

   ```bash
   brew install helm
   ```

2. Verify:

   ```bash
   helm version
   ```

## Create a Kubernetes Cluster

1. In Terminal, tell Kind to use Podman as its provider:

   ```bash
   export KIND_EXPERIMENTAL_PROVIDER=podman
   ```

2. Create a cluster named `dev-cluster`:

   ```bash
   kind create cluster --name dev-cluster
   ```

3. Verify the cluster is running:

   ```bash
   kubectl cluster-info --context kind-dev-cluster
   ```

## Verify in Podman Desktop

1. Open **Podman Desktop** from Applications.
2. Click the **Kubernetes** icon in the left sidebar.
3. You should see `kind-dev-cluster` listed as the active context.

## Set kubectl Context

If you have multiple clusters, set the active one:

```bash
kubectl config use-context kind-dev-cluster
```

Check all available contexts:

```bash
kubectl config get-contexts
```

## Delete the Cluster

When you no longer need it:

```bash
kind delete cluster --name dev-cluster
```

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
