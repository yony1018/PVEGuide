[(49条消息) proxmox ve虚机磁盘扩容_qzhiyong的专栏-CSDN博客](https://blog.csdn.net/qzhiyong/article/details/120040197)

> EXT4文件系统
>
> ```
> df -h	
> df -hT 	#查看磁盘信息
> 
> sudo vgdisplay 	#查询磁盘剩余空间
> lvdisplay	#查询磁盘目录名 
> 
> lvextend -l +[容量大小] [磁盘目录名]
> resize2fs -p [磁盘目录名] 
> df -hT
> ```
>
> 

