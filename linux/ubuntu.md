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
