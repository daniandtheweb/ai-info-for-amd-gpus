# Status of AI tools for AMD
AMD has some good AI focused tools such as ROCm and HIP (a runtime that allows conversion of CUDA code to make it run on ROCm).

Unfortunately not many gpus are currently compatible with those tools and most of the supported cards are not the consumer ones. This now seems to be changing starting with RDNA3 but the problem persists on older generations.

It's good to remember that there are alternative runtimes as OpenCL and Vulkan that can work flawlessly on almost any gpu (llama.cpp and its forks already implement OpenCL and there are a couple of pull requests to add Vulkan acceleration).

This repository will serve as an attempt to retrieve and organize all the information available around the internet on how to run the newest AI tools on any AMD card.

Every new information about a specific AMD GPU and its settings to use it on stable diffusion can be submitted as an issue or a pull request.

# Stable Diffusion
### [Linux](https://github.com/DaniAndTheWeb/sd-data-amd-gpu/blob/main/linux/stable-diffusion.md)
### [Windows](https://github.com/DaniAndTheWeb/sd-data-amd-gpu/blob/main/windows/stable-diffusion.md)

# Text Generation
### [Linux](https://github.com/DaniAndTheWeb/sd-data-amd-gpu/blob/main/linux/text-gen.md)
### [Windows](https://github.com/DaniAndTheWeb/sd-data-amd-gpu/blob/main/windows/text-gen.md)

