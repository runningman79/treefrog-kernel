
------------------------------ build instructions for the kernel
make -j ARCH=arm UIMAGE_LOADADDR=0x8000 uImage
make ARCH=arm modules
sudo make ARCH=arm INSTALL_MOD_PATH=/<sdcard> modules_install

make ARCH=arm dtbs
