
------------------------------ build instructions for the kernel
source <path to SDK 2018.3>/settings.sh

export CROSS_COMPILE=arm-linux-gnueabihf-
export ARCH=arm

make mrproper
make rack_controller_defconfig

make -j ARCH=arm UIMAGE_LOADADDR=0x8000 uImage
make ARCH=arm modules
sudo make ARCH=arm INSTALL_MOD_PATH=/<sdcard> modules_install

make ARCH=arm dtbs
