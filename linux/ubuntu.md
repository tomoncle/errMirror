###dpkg 被中断，您必须手工运行 dpkg --configure -a 解决此问题。
解决:  rm /var/lib/dpkg/updates/* && apt-get update &&  apt-get upgrade

###find . -name *.pyc   >> find: 路径必须在表达式之前: manage.pyc
解决: 出现这种问题是在当前目录存在查找目标，返回到该目录父级目录查找，还有一种情况是查找时，使用通配符需要转义"*.pyc"改为"\*.pyc"
