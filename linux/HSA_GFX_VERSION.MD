# Here is stored all the known data for Linux systems about the working versions of GFX for any AMD graphic card.
The environment variable `HSA_OVERRIDE_GFX_VERSION` is the main issue when it comes to get an AMD GPU working with stable diffusion on Linux.
Setting this variable correctly before the launch of the program allows to use even Renoir GPUs (AMD 4000 series APUs) if they have enought VRAM reserved.

## GPUs
### RX 5700XT (Navi 10 - RDNA 1.0)
#### HSA_OVERRIDE_GFX_VERSION=10.3.0
Graphics/Compute: GFX10.1 (gfx1010)

Working with `--no-half --precision full` as launch arguments.

Navi GPUs seems to have lost its functioning state with ROCm starting with version 5.3; this means that only PyTorch versions built for ROCm 5.2 are functional for now.

#### PyTorch 1.13.1 ROCm 5.2 (latest official working version) - Python 3.10.6
`pip install torch==1.13.1+rocm5.2 torchvision==0.14.1+rocm5.2 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/rocm5.2`

#### PyTorch 2.0.0 Nightly ROCm 5.2 (latest nightly working version) - Python 3.10.6
Download and manually install the 3 files stored here: [AMD repository](https://repo.radeon.com/rocm/manylinux/.private-9bd8754a636553e1d1ce3e107bf18c00/20231018/).

## APUs
### Renoir (Vega - GCN 5.1)
#### HSA_OVERRIDE_GFX_VERSION=9.0.0
Graphics/Compute: GFX9 (gfx90c)

Ryzen 4700U confirmed, usable with 4 GB of reserved VRAM and at least 12 GB of RAM configured inside the BIOS, the RAM recommendation is to not make the pc go unresponsive. No special launch arguments are required.


### Valve Steam Deck's APU (Navi - RDNA 2.0)
#### HSA_OVERRIDE_GFX_VERSION=10.3.0
Graphics/Compute: GFX10.3 (gfx1033)

(Old data, need updated testing and report.) Generates black images with [this model](https://huggingface.co/Linaqruf/anything-v3.0/blob/main/Anything-V3.0-pruned.ckpt) and no arguments (running in f16), does not crash, must use with 4 GB of reserved VRAM configured inside the BIOS to prevent crash. Run `export HSA_OVERRIDE_GFX_VERSION=10.3.0` before launch.py. tested ~1d before automatic rocm install [PR](https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/6709). Monitored GPU usage with [System Monitoring Center](https://github.com/hakandundar34coding/system-monitoring-center) in discover store. This is appearing to generate on gpu. Other tests were not so close. Unknown if 16gb swapfile enabled during the test. Followed [this](https://www.reddit.com/r/steamdeck_linux/comments/102hzav/guide_how_to_install_rocm_for_gpu_julia/) Running with `--precision full --no-half --lowvram/--medvram` takes too long+black output, or crashes system. I likely installed rocm5.2 like so within the venv: `pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/rocm5.2` Also tried  @brkirch's improvements with combinations of `--upcast-sampling` (did not try with --opt-sub-quad-attention) without success [PR+commit](https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/6510/commits/2cc077193d4203404bae9c7d88dff326ea4e4a71) using [openjourney](https://huggingface.co/prompthero/openjourney/blob/main/mdjrny-v4.ckpt) and [1.5](https://huggingface.co/runwayml/stable-diffusion-v1-5/blob/main/v1-5-pruned-emaonly.ckpt) models, seeing promising [comment](https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/6510#issuecomment-1387442388).
