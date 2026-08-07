# GPU Programming
https://learning.oreilly.com/library/view/gpu-programming-with/9781805124542/

https://github.com/PacktPublishing/GPU-Programming-with-CPP-and-CUDA

## CUDA Setup
### Driver
- https://www.nvidia.com/en-us/drivers
- https://www.nvidia.com/en-us/drivers/unix/
- https://docs.nvidia.com/cuda/cuda-installation-guide-linux/#pre-installation-actions

Find and download the correct driver from the nVidia website.
```sh
# Choose the MIT/GPL version from the installer options
sudo sh NVIDIA-Linux-x86_64-595.91.07.run
# driver info
nvidia-smi
cat /proc/driver/nvidia/version
modinfo nvidia | grep ^version
# uninstall the driver
sudo apt-get --purge remove "*nvidia*" "libxnvctrl*"
sudo apt-get purge nvidia*
sudo apt-get autoremove
```

### CUDA Toolkit
- https://developer.nvidia.com/cuda-downloads
- https://developer.nvidia.com/cuda-toolkit-archive

```sh
# I prefer the local .run file on Debian.
# Since my GPU (5070 Ti) latest driver is 595.* I need CUDA 13.2.* from the archive.
# The "_595.71.05_" in the filename is the driver that is included
# with the download and optional during installation.
wget https://developer.download.nvidia.com/compute/cuda/13.2.2/local_installers/cuda_13.2.2_595.71.05_linux.run
sudo sh cuda_13.2.2_595.71.05_linux.run
```

> [!NOTE]
> Please make sure that
> - PATH includes `/usr/local/cuda-13.2/bin`
> - LD_LIBRARY_PATH includes `/usr/local/cuda-13.2/lib64`, or, add `/usr/local/cuda-13.2/lib64` to `/etc/ld.so.conf` and run `ldconfig` as root

```sh
export PATH=/usr/local/cuda-13.2/bin:$PATH
# paste path update to end of file
vim ~/.zshrc
```
> [!TIP]
> To uninstall the CUDA Toolkit, run `cuda-uninstaller` in `/usr/local/cuda-13.2/bin`

```sh
# manual uninstall cuda
sudo apt-get --purge remove "*cuda*" "*cublas*" "*cufft*" "*cufile*" "*curand*" \
 "*cusolver*" "*cusparse*" "*gds-tools*" "*npp*" "*nvjpeg*" "nsight*" "*nvvm*"
 ```