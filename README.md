# pxe

# 本文件用于指导如何构建属于自己的PXE网启环境

# 建议采用可刷写openwrt固件的路由器或树莓派\R2S之类卡片电脑作为代码搭载硬件平台，便携性强

# 需要硬件平台操作系统开启HTTP、SAMBA、NFS、DHCP、TFTP服务

# 以下为具体操作步骤

一、下载代码

访问 "https://github.com/fastdie/pxe" ，下载源码；

二、上传代码到硬件平台

用winscp或其他ftp工具将 "grub、iso、wim" 三个文件夹上传至硬件平台的 "/opt/pxe" 下；如果你找不到该文件夹，那就建一个；

备注：如果你采用openwrt路由器作为硬件平台，那么你得通过USB扩展外部存储，否则无法存放网启的PE及微软原版ISO文件。

三、配置tftp服务

配置tftp服务，引导文件目录为 "/opt/pxe/grub"，引导文件名为 "undionly.kpxe"；

四、配置samba服务

配置samba服务，共享目录为 "/opt/pxe/wim"，推荐设置为只读、可浏览、允许guest访问；

五、创建iso目录软链接

假设你的硬件平台为openwrt路由器，那么在它的命令行输入 "ln -s /opt/pxe/iso /www/iso"；其他硬件平台，请自行根据OS的HTTP服务根路径来修改；

备注：创建软链接是为了让你能够通过http协议访问到存放在 "/opt/pxe/iso" 目录下的内容；

六、创建nfs共享文件夹（非必需项）

配置nfs服务，共享目录为  "/opt/pxe/wim"；

备注：NFS共享文件夹是为了网络启动 ubuntu live-cd 而启用的；如果你没有这方面的需求，可以不进行配置；

七、上传winpe镜像文件

本代码仅包含memtest86的引导镜像，你需要将你喜欢的winpe镜像文件上传到 "/opt/pxe/iso" 目录下，并修改 "/opt/pxe/grub/menu.ipxe"文件对应部分内容；

八、 上传微软原版镜像文件

你可以将微软原版镜像文件或修改后的WIM、ESD文件上传到 "/opt/pxe/wim" 目录下；

当你启动到支持网络的winpe环境，你可以通过samba协议加载微软原版镜像文件，借助winpe工具给网启计算机重装系统；
