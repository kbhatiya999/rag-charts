# Podman Desktop + Freelens

Podman Desktop manages containers and local Kubernetes clusters. Freelens is a free, open-source GUI for browsing and managing those clusters — no CLI needed.

---

## Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Skip if already installed.

---

## Install Tools

```bash
brew install --cask podman-desktop
brew install helm
brew install kind
brew install kubernetes-cli
brew install --cask freelens
```

---

## Podman Desktop Setup

### 1. Launch and Create a Machine

Open **Finder** (`⌃ + ⌥ + F`), go to **Applications**, and launch **Podman Desktop**.

On first launch the setup wizard appears. Click **Install** when prompted — this creates and starts your Podman machine automatically.

### 2. Install the Kind Extension

1. Click **Extensions** in the left sidebar.
2. Search for **Kind**.
3. Click the install icon next to it.
4. Go to the **Installed** tab and confirm it is active.

### 3. Create a Kubernetes Cluster

1. Click **Kubernetes** in the left sidebar.
2. Click **Create new cluster**.
3. Select **Kind** as the provider.
4. Give it a name (e.g. `dev-cluster`) and click **Create**.

Podman Desktop will spin up the cluster and set it as your active context.

---

## Freelens Setup

### 1. Launch Freelens

Open **Freelens** from **Applications**. It automatically reads your kubeconfig and detects `dev-cluster`.

### 2. Browse the Cluster

Click on `dev-cluster` in the sidebar to connect. From here you can browse **Workloads**, **Deployments**, **Pods**, **Services**, and more — all without touching the terminal.

---

## Quick Setup

Already done this before? Just reinstall the tools.

```bash
brew install --cask podman-desktop
brew install helm
brew install kind
brew install kubernetes-cli
brew install --cask freelens
```

Then launch **Podman Desktop** to recreate the machine and cluster, and **Freelens** to connect.
