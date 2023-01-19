# Here is stored all the known data for Linux systems about the working versions of GFX for any AMD graphic card.
The environment variable HSA_OVERRIDE_GFX_VERSION is the main issue when it comes to get an AMD GPU working with stable diffusion on Linux.
Setting this variable correctly before the launch of the program allows to use even Renoir GPUs (AMD 4000 series APUs) if they have enought VRAM reserved.

#GPUs                     HSA_OVERRIDE_GFX_VERSION
RX 5700XT = 10.3.0

#APUs
Renoir (4700u confirmed, usable with 4 GB of reserved VRAM and 12 GB of RAM configured inside the BIOS, recommended at least 12 GB of RAM or the pc will be unresponsive) = 9.0.0
