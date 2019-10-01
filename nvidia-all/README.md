# Nvidia driver 435/430/418/415/410/396 series AIO installer

LIBGLVND compatible, with 32 bit libs and DKMS enabled out of the box (you will still be asked if you want to use the regular package). Installs for all currently installed kernels.
Unwanted packages can be disabled with switches in the PKGBUILD. Defaults to complete installation.

You may need/want to add a pacman hook for nvidia depending on your setup : https://wiki.archlinux.org/index.php/NVIDIA#DRM_kernel_mode_setting

Vulkan dev drivers : https://developer.nvidia.com/vulkan-driver

Regular drivers : https://www.nvidia.com/object/unix.html


# How to generate a package for a driver that isn't listed (390 and lower branches are not supported) :
- When you are prompted for driver version, select "custom" (choice 8).
- You'll then be asked the branch group. Select either "Vulkan dev" (choice 2) for Vulkan dev drivers or "stable or regular beta" (choice 1) for every other driver.
- Now you have to enter the version number of the desired driver. Vulkan dev drivers version is usually formatted as `mainbranch.version.subversion` (i.e.: 415.22.01) while the stable or regular beta drivers version is usually `mainbranch.version` (i.e.: 415.25)
- To finish, you'll be asked if you want dkms(recommended) or regular modules, similarly to the usual drivers versions.

# Optimus users :
- A great tool exists for you and works with these nvidia-all packages: https://github.com/Askannz/optimus-manager
- 435.17 beta has introduced PRIME render offload support. You can learn more about the needed setup here: http://us.download.nvidia.com/XFree86/Linux-x86_64/435.17/README/primerenderoffload.html

# Mostlyportable-gcc users :
- For non-dkms nvidia-all packages, setting your `CUSTOM_GCC_PATH` in .cfg is enough.
- For dkms nvidia-all packages, you'll need to make DKMS aware of your mostlyportable-gcc build. See: https://github.com/Tk-Glitch/PKGBUILDS/issues/334#issuecomment-537197636
