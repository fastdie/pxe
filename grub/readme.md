# 该目录用于存放IPXE引导文件和多重引导菜单文件
# undionly.kpxe IPXE引导文件，内置菜单，引导后默认查找tftp根目录下的boot.ipxe
# memdisk syslinux的组件，可以用于引导软盘映像、硬盘映像或某些ISO映像
# boot.ipxe 多重引导菜单文件，可用于根据硬件特征自定义引导过程，详见该文件内置备注
# boot.ipxe.cfg 多重引导菜单配置文件，存储自定义变量
# menu.ipxe 多重引导菜单主文件，详见该文件内置备注