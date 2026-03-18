# 2. Setup Cluster

## Create a Kubernetes Cluster with Kind

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
