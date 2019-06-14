## aptitude 安装失败
```bash
$ sudo apt-get install libcwidget3
$ sudo apt-get install libsigc++-2.0-0c2a
$ sudo apt install libxapian22 apt-xapian-index
$ sudo apt install aptitude
```


## dpkg 被中断，您必须手工运行 dpkg --configure -a 解决此问题。
解决:  rm /var/lib/dpkg/updates/* && apt-get update &&  apt-get upgrade

## find . -name *.pyc   >> find: 路径必须在表达式之前: manage.pyc
解决: 出现这种问题是在当前目录存在查找目标，返回到该目录父级目录查找，还有一种情况是查找时，使用通配符需要转义"*.pyc"改为"\*.pyc"


## ubuntu菜单栏不显示时间
```bash
$ sudo apt-get install indicator-datetime 
$ sudo dpkg-reconfigure --frontend noninteractive tzdata 
$ sudo killall unity-panel-service
```

## ModuleNotFoundError: No module named 'apt_pkg'

* `$ sudo apt-get remove --purge python-apt`
* `$ sudo apt-get install python-apt --fix-missing`
* `$ cd /usr/lib/python3/dist-packages`
* `$ sudo cp apt_pkg.cpython-34m-x86_64-linux-gnu.so apt_pkg.so`

## 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系
```bash
root@tomoncle-ubuntu:~# apt install python3.6-dev
正在读取软件包列表... 完成
正在分析软件包的依赖关系树       
正在读取状态信息... 完成       
有一些软件包无法被安装。如果您用的是 unstable 发行版，这也许是
因为系统无法达到您要求的状态造成的。该版本中可能会有一些您需要的软件
包尚未被创建或是它们已被从新到(Incoming)目录移出。
下列信息可能会对解决问题有所帮助：

下列软件包有未满足的依赖关系：
 python3.6-dev : 依赖: libpython3.6-dev (= 3.6.8-1~16.04.york1) 但是它将不会被安装
                 依赖: libexpat1-dev 但是它将不会被安装
E: 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系。
```

* 1.安装aptitude `$ apt -y install aptitude`
* 2.使用aptitude安装软件包 `$ aptitude install python3.6-dev`
```bash
root@tomoncle-ubuntu:~# aptitude install python3.6-dev
下列“新”软件包将被安装。         
  libexpat1-dev{ab} libpython3.6{a} libpython3.6-dev{a} python3.6-dev 
0 个软件包被升级，新安装 4 个， 0 个将被删除， 同时 32 个将不升级。
需要获取 41.6 MB 的存档。 解包后将要使用 63.0 MB。
下列软件包存在未满足的依赖关系：
 libexpat1-dev : 依赖: libexpat1 (= 2.1.0-7) 但是 2.1.0-7ubuntu0.16.04.3 已安装。
下列动作将解决这些依赖关系：

     保持 下列软件包于其当前版本：
1)     libexpat1-dev [未安装的]   
2)     libpython3.6-dev [未安装的]
3)     python3.6-dev [未安装的]   



是否接受该解决方案？[Y/n/q/?] n
下列动作将解决这些依赖关系：

     降级 下列软件包：                                             
1)     libexpat1 [2.1.0-7ubuntu0.16.04.3 (now) -> 2.1.0-7 (xenial)]



是否接受该解决方案？[Y/n/q/?] Y
下列软件包将被“降级”：
  libexpat1 
下列“新”软件包将被安装。
  libexpat1-dev{a} libpython3.6{a} libpython3.6-dev{a} python3.6-dev 
0 个软件包被升级，新安装 4 个， 1 个被降级， 0 个将被删除， 同时 32 个将不升级。
需要获取 41.7 MB 的存档。 解包后将要使用 63.0 MB。
您要继续吗？[Y/n/?] Y
读取： 1 http://mirrors.aliyun.com/ubuntu xenial/main amd64 libexpat1 amd64 2.1.0-7 [71.4 kB]
读取： 2 http://mirrors.aliyun.com/ubuntu xenial/main amd64 libexpat1-dev amd64 2.1.0-7 [115 kB]
读取： 3 http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial/main amd64 libpython3.6 amd64 3.6.8-1~16.04.york1 [1,457 kB]
读取： 4 http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial/main amd64 libpython3.6-dev amd64 3.6.8-1~16.04.york1 [39.5 MB]                   
读取： 5 http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial/main amd64 python3.6-dev amd64 3.6.8-1~16.04.york1 [508 kB]                       
已下载 41.7 MB，耗时 23分 3秒 (30.1 kB/s)                                                                                                              
dpkg：警告：即将把 libexpat1:amd64 从 2.1.0-7ubuntu0.16.04.3 降级到 2.1.0-7
(正在读取数据库 ... 系统当前共安装有 222314 个文件和目录。)
正准备解包 .../libexpat1_2.1.0-7_amd64.deb  ...
正在将 libexpat1:amd64 (2.1.0-7) 解包到 (2.1.0-7ubuntu0.16.04.3) 上 ...
正在选中未选择的软件包 libexpat1-dev:amd64。
正准备解包 .../libexpat1-dev_2.1.0-7_amd64.deb  ...
正在解包 libexpat1-dev:amd64 (2.1.0-7) ...
正在选中未选择的软件包 libpython3.6:amd64。
正准备解包 .../libpython3.6_3.6.8-1~16.04.york1_amd64.deb  ...
正在解包 libpython3.6:amd64 (3.6.8-1~16.04.york1) ...
正在选中未选择的软件包 libpython3.6-dev:amd64。
正准备解包 .../libpython3.6-dev_3.6.8-1~16.04.york1_amd64.deb  ...
正在解包 libpython3.6-dev:amd64 (3.6.8-1~16.04.york1) ...
正在选中未选择的软件包 python3.6-dev。
正准备解包 .../python3.6-dev_3.6.8-1~16.04.york1_amd64.deb  ...
正在解包 python3.6-dev (3.6.8-1~16.04.york1) ...
正在处理用于 libc-bin (2.23-0ubuntu11) 的触发器 ...
正在处理用于 doc-base (0.10.7) 的触发器 ...
Processing 1 added doc-base file...
正在处理用于 man-db (2.7.5-1) 的触发器 ...
正在设置 libexpat1:amd64 (2.1.0-7) ...
正在设置 libexpat1-dev:amd64 (2.1.0-7) ...
正在设置 libpython3.6:amd64 (3.6.8-1~16.04.york1) ...
正在设置 libpython3.6-dev:amd64 (3.6.8-1~16.04.york1) ...
正在设置 python3.6-dev (3.6.8-1~16.04.york1) ...
正在处理用于 libc-bin (2.23-0ubuntu11) 的触发器 ...
                                 
```
