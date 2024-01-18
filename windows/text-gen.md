# Text Generation on Windows

## PyTorch

I haven't tested anything yet.

## GPT4ll

This project uses parts of `llama.cpp` combined with a Vulkan backend in order to provide acceleration on any modern AMD GPU.

It's the easiest way to use text generation locally.

## llama.cpp and projects based on it

`llama.cpp` is an amazing project with different GPU backends to choose from.

### OpenCL

The OpenCL backend just works on most GPUs.

### Vulkan (wip)

A Vulkan backend is work in progress and will eventually replace the OpenCL one. Just like the previous backend it will just work on most hardware.

### HIP

It should work on Windows using a GPU supported by ROCm.
