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

# PVE系统挂载新硬盘

> ~~为了挂载一个新硬盘给pve池,导致pve开机卡死,折腾了一下午~~

## 给我整崩溃的方法

> https://www.moewah.com/archives/2546.html
>
> > 到一半重启后进不去了,下面都是解决/etc/fstab文件和挂载修复的问题
> >
> > https://www.csdn.net/tags/NtTaUgzsMDU0NDAtYmxvZwO0O0OO0O0O.html
> >
> > https://blog.csdn.net/DL_ChenBo/article/details/53164882
> >
> > [【linux】解决系统卡在ubuntu loading initial ramdisk_six_water的博客-CSDN博客](https://blog.csdn.net/six_water/article/details/103593515)
> >
> > grub下进pve系统 grub E编辑模式下 修改grub文件中的 `ro quiet amd......(后面这一串都删)....` 改成上面参考中的 `rw init=/bin/bash`
> >
> > > 但后来`真正解决问题`的居然是`从非UEFI启动`	~~我人都傻了~~

## 正常运行的方法

> https://www.cnblogs.com/xiaobo060/p/12829535.html
>
> 改完`/etc/fstab`记得用重新挂载命令
>
> ~~否则就等着在grub下死活进不去系统吧~~

