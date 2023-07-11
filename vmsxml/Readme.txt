制作虚机：

1. centos7.6-bios 用于虚机 或者 bios类型的裸金属机器；
2. centos7.6-uefi 用于裸金属的uefi模式；


iso操作
1. 插入光盘
	virsh change-media centos7.6-bios   hda    /var/lib/libvirt/images/CentOS-7-x86_64-Minimal-1810.iso   --insert
	virsh change-media centos7.6-bios hda --eject 
	
保存位置:
bios : 10.10.158.22:/var/lib/libvirt/images/centos7.6-bios.qcow2
uefi : 10.10.158.22:/var/lib/libvirt/images/centos7.6-uefi.qcow2




操作 ：

2023/07/11 16:00
关闭NetworkManager
关闭firewalld
关闭selinux
允许root登录
设置root密码 Password.123
安装node-agent

