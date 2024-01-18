# Stable Diffusion on Linux

## PyTorch

There are many different frontends to use Stable Diffusion on linux but when it comes to the backends almost every frontend uses PyTorch ROCm.

Not many consumer GPUs by AMD are officially supported by this backend and this creates a great disadvantage for the end user.

The only way to be able to use some of the unsupported cards is by setting an environment variable called `HSA_OVERRIDE_GFX_VERSION`. This variable indicates the model of the GPU and by setting it correctly PyTorch can be tricked into allowing the card work.

By setting the variable together with the correct launch arguments some unsupported GPUs can use Stable Diffusion.

Unfortunately this method is not definitive and is just a workaround.

### [HSA_OVERRIDE_GFX_VERSION collection](https://github.com/DaniAndTheWeb/sd-data-amd-gpu/blob/main/linux/HSA_GFX_VERSION.MD).

## stable-diffusion.cpp

This project allows the inference of Stable Diffusion without the use of any python dependency (PyTorch is not needed).

The HIP backend allows the use of AMD GPUs and even if the project is quite young and the performance isn't as good as PyTorch based programs the fact that it requires to work only the ROCm toolkit is a great advantage.

The Debian team is working on enabling ROCm and HIP support for any modern AMD GPU and the packages that allow that are already available in Debian Unstable.

With my card (RX 5700 XT - gfx1010, unsupported by ROCm) the inference works perfectly without any strange workaround.

My current setup to allow the usage of the card is using [Distrobox](https://distrobox.it/) with a Debian Unstable container and all the required ROCm and HIP toolkit installed, this way the inference can be run from inside the container on any distro.
