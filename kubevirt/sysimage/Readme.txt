1、 选择好主机，比如10.10.158.21，将iso文件放到主机的指定位置，/data/Centos1810.iso,如果内存比较大的话，可以使用/run 目录。
2、 指定系统盘和iso文件的位置，选择vm.yaml进行创建，打开novnc窗口进行系统安装
3、 安装完系统，将vm删除，去掉cdrom，调整启动顺序，从硬盘启动。
4、 将制作好的系统盘，上传到任一virt-launcher的pod中。
5、 使用qemu-img将raw格式的sysdisk.img文件转为qcow2文件  qemu-img convert -c -f raw -O qcow2 centos76.img centos76.qcow2
6、 将转换了的qcow2文件从virt-launcher的pod中拿出来，
7、 还有一种方法，使用virt-launcher的镜像启动一个容器，将目录过载过去，省去了来回拷贝文件，用于替代4,5,6步骤。
     docker run --privileged --entrypoint /bin/bash  --mount type=bind,source=/run/make_images,target=/opt --rm -it k8s-deploy/virt-launcher:v0.57.1
8、 将qcow2文件改名为disk.img，使用Dockerfile制作系统镜像， docker built -t 10.10.95.6:8443/k8s-deploy/vmimage:centos7.6 .
9、 将镜像推送到harbor仓库， docker push 10.10.95.6:8443/k8s-deploy/vmimage:centos7.6
10、linux类型的镜像都可以通过这种方式进行创建。



