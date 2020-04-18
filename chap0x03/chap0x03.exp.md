# 实验三



# Systemd动手实战 （asciinema视频）

---
* [命令篇](https://asciinema.org/a/XQ3q3A1bgrlyftZHTfyL6UbBu)
* [实战篇](https://asciinema.org/a/gIOjYnyTylXA6665ZspVOb9ir)



# 本章完成后的自查清单

---

* 如何添加一个用户并使其具备sudo执行程序的权限？
```bash
  1、adduser username 
  #添加用户
  2、sudo usermod -aG sudo username
  # 将用户添加到sudo组
   ```
* 如何将一个用户添加到一个用户组？

```bash
  sudo usermod -aG groupname username
```
* 如何查看当前系统的分区表和文件系统详细信息？
```bash
  fdisk -l  
  # 或 df -T
```  
* 如何实现开机自动挂载Virtualbox的共享目录分区？
```bash
  1、安装增强功能
  2、配置共享文件夹https://blog.csdn.net/skylake_/article/details/53132499
  3、/ etc / fstab文件中，添加 sharing /mnt/share vboxsf defaults 0 0
```
* 基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？
```bash
  1、https://blog.csdn.net/seteor/article/details/6708025
  2、将逻辑卷组挂载到物理卷组下
  3、在物理卷组有足够的剩余空间时，可以对逻辑分区进行扩容
  4、扩容分区      lvextend -L +10G -f -r /dev/vg_server1/local
  5、减少分区容量  lvreduce -L -10G -f -r /dev/vg_server1/local
```
* 如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？
```bash
  在networking.service配置文件的区块链[Service]处填充ExecStart和ExecStop的脚本路径
```
* 如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？实现***杀不死***？
```bash
  将Service区块链的Restart细分设置参数为always，即无论是什么原因退出，总是重启
```


# 参考文献

---
* [命令篇  阮一峰的网络日志](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
* [实战篇  阮一峰的网络日志](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)



