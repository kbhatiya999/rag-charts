# GPU Inference with Podman

Run AI inference inside a Linux container on macOS using the Apple GPU — powered by LibKrun's Virtio-GPU bridge between Vulkan and Metal.

---

## Create a GPU-Enabled Machine

In **Podman Desktop**, go to **Settings → Resources → Podman**.

Click **Create new** and set the **Machine provider** to **libkrun (GPU enabled)**. Set CPU and memory as needed, then click **Create**.

Start the machine once created.

**Note:** You need to delete any existing Podman machine first to avoid port conflicts. LibKrun replaces the default Apple Hypervisor provider.

---

## Verify GPU is Available

```bash
podman machine ssh
ls /dev/dri
```

You should see `card0` and `renderD128`. If both are present the GPU is accessible inside the VM.

Exit the SSH session:

```bash
exit
```

---

## Run Inference

```bash
podman run --rm -it --device /dev/dri \
  -v ~/models:/models:Z \
  quay.io/slopezpa/fedora-vgpu-llama
```

`--device /dev/dri` passes the GPU into the container. `-v ~/models:/models:Z` mounts a local folder where you store your model files.

Inside the container, run inference against a GGUF model:

```bash
main -m /models/your-model.gguf -ngl 99 -p "Your prompt here"
```

`-ngl 99` offloads all layers to the GPU. Adjust down if you run out of VRAM.

---

## Quick Setup

Already done this before?

1. Open **Podman Desktop** → **Settings → Resources → Podman** → **Create new** → select **libkrun (GPU enabled)** → **Create** → **Start**.
2. Run:

```bash
podman run --rm -it --device /dev/dri \
  -v ~/models:/models:Z \
  quay.io/slopezpa/fedora-vgpu-llama
```
