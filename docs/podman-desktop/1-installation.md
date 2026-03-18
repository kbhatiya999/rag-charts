# 1. Installation

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

`kubectl` is the Kubernetes CLI. `kind` (Kubernetes in Docker) runs clusters inside Podman containers.

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

**Next:** [2. Setup Cluster](2-setup-cluster.md)
