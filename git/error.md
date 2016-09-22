#git error

##git reset 异常：
```shell
fatal: Unable to create '/opt/app/workspace/github/aric-docs/.git/index.lock': 文件已存在.
If no other git process is currently running, this probably means a
git process crashed in this repository earlier. Make sure no other git
process is running and remove the file manually to continue.

删除锁文件：
rm  -f   ../.git/index.lock
git reset HEAD filename
```
