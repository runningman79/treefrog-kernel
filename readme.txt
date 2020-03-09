---------------- build instructions for the kernel

0) export CROSS_COMPILE=arm-linux-gnueabihf-

1) make ARCH=arm mrproper

-- rack_controller
2) make ARCH=arm rack_controller_defconfig
-- node controller
2) make ARCH=arm node_controller_defconfig

3) make -j ARCH=arm UIMAGE_LOADADDR=0x8000 uImage
4) make ARCH=arm modules
5) sudo env PATH=$PATH make ARCH=arm INSTALL_MOD_PATH=/<sdcard> modules_install
6) make ARCH=arm dtbs

Note for modules_install: rc_src/deploy now has a lib subdirectory. if you make modules_install
with INSTALL_MOD_PATH set to a temp dir, you can copy the dir below (lib/modules/xxx) to deploy/

=====================

FYI - to make the def config:

1) make ARCH=arm menuconfig or make ARCH=arm config, etc to create your .config
2) make savedefconfig to create defconfig (optimized config)
3) copy defconfig to arch/arm/configs/<saved config>
