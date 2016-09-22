#docker run常见异常记录

###运行：docker run -dit -m 512m -p 6379:6379 kingaric/redis  
```shell
error:
WARNING: Your kernel does not support swap limit capabilities, memory limited without swap.
      
原因没有开启cgroups中的swap account，解决办法如下：
修改：/etc/default/grub　
修改参数：GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"　
保存更新：sudo update-grub
重启系统：reboot
```
