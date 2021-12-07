# PVE环境下linux虚拟硬盘扩容



> [(49条消息) proxmox ve虚机磁盘扩容_qzhiyong的专栏-CSDN博客](https://blog.csdn.net/qzhiyong/article/details/120040197)
>
> [Proxmox VE 在线扩容磁盘分区【附源码】_kuSorZ_51CTO博客](https://blog.51cto.com/kusorz/2495915)
>
> [Proxmox VE（PVE）进行硬盘扩容操作教程 - 方舟基地 (wnark.com)](https://www.wnark.com/archives/118.html)
>
> 虚拟机硬件->对应硬盘->调整磁盘大小
>
> EXT4文件系统
>
> ```
> lsblk	#查看磁盘挂载情况
> 
> growpart /dev/sda 3  #  表示扩容系统盘的第一个分区（/dev/sda1），根据你自己的分区来
> 
> pvresize /dev/sda3
> 
> 
> df -h	
> df -hT 	#查看磁盘信息
> 
> sudo vgdisplay 	#查询磁盘剩余空间
> lvdisplay	#查询磁盘目录名 
> 
> lvresize -l +100%FREE [diskname]   # 直接把所有剩余空间都分配给centos-root这个LV
> 
> lvextend -l +[容量大小] [磁盘目录名]
> resize2fs -p [磁盘目录名] 
> df -hT
> ```
>
> 

