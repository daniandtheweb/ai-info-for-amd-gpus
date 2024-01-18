# Text Generation on Linux

## PyTorch

I haven't been able to use reliably any PyTorch based text generation program on my GPU (RX 5700 XT, gfx1010).

## GPT4ll

This project uses parts of `llama.cpp` with a Vulkan backend in order to provide acceleration on any modern AMD GPU.

It's the easiest way to use text generation locally.

## llama.cpp and projects based on it (such as koboldcpp)

`llama.cpp` is an amazing project with different GPU backends to choose from:

### OpenCL

The OpenCL backend just works on most GPUs.

### Vulkan (wip)

A Vulkan backend is work in progress and will eventually replace the OpenCL one. Just like the previous backend it will just work on most hardware.

### HIP

The HIP backend works great but it needs a workaround in order to work on unsupported GPUs.

The Debian team is working on enabling ROCm and HIP support for any modern AMD GPU and the packages that allow that are already available in Debian Unstable.

With my card (RX 5700 XT - gfx1010, unsupported by ROCm) the text generation works perfectly using those packages without any strange workaround.

My current setup to allow the usage of the card is using Distrobox with a Debian Unstable container and all the required ROCm and HIP toolkit installed, this way the text generation can be run from inside the container on any distro.
