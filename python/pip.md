#python pip常见异常

### command 'x86_64-linux-gnu-gcc' failed with exit status 1
解决办法：sudo apt-get install libxml2-dev libxslt1-dev zlib1g-dev 

### build/temp.linux-x86_64-2.7/_openssl.c:433:30: fatal error: openssl/opensslv.h: 没有那个文件或目录
解决办法：sudo apt-get install libssl-dev

### UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 49: ordinal not in range(128)
解决办法：

      import sys  
      reload(sys)  
      sys.setdefaultencoding('utf8')  

### error: Setup script exited with error: command 'gcc' failed with exit status 1
解决办法：sudo apt-get install python-dev

### pip install cryptography 失败
解决办法：apt-get install libffi-dev openssl libssl-dev


### pip install中出现UnicodeDecodeError: 'ascii' codec can't decode byte 0xe4 in position 16: ordinal not in range(128)


      使用echo $LANG命令：

      [root@localhost tools]# echo $LANG
      en_US.UTF-8

      可以看出系统默认语言为en_US.UTF-8

      对于Python设定语言可以在site-packages中创建sitecustomize.py，Python会自动加载
      [root@localhost site-packages]# pwd
      /usr/local/lib/python2.7/site-packages

      [root@localhost site-packages]# cat sitecustomize.py
      import sys
      sys.setdefaultencoding('utf-8')
      如果涉及到中文只需将utf-8修改为gb2312 即可。
      
      
###tornado/speedups.c:2:20: fatal error: Python.h: No such file or directory
解决办法： sudo apt-get install python-dev　或者 sudo apt-get install python3-dev


###/usr/include/python2.7/Python.h:19:20: fatal error: limits.h: No such file or directory
解决方案：Alpine linux uses musl libc. You probably need to install musl-dev.即 apk add musl-dev 



###/usr/lib/gcc/x86_64-alpine-linux-musl/4.8.3/../../../../x86_64-alpine-linux-musl/bin/ld: cannot find -lgcc_s
解决方案：　apk add linux-headers libgcc



###SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)
解决方案：


### No module named singledispatch
解决方案： pip install singledispatch

### No module named singledispatch
解决方案： pip install backports_abc

### pip list异常
```shell
Exception:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/pip/basecommand.py", line 122, in main
    status = self.run(options, args)
  File "/usr/lib/python2.7/dist-packages/pip/commands/list.py", line 80, in run
    self.run_listing(options)
  File "/usr/lib/python2.7/dist-packages/pip/commands/list.py", line 142, in run_listing
    self.output_package_listing(installed_packages)
  File "/usr/lib/python2.7/dist-packages/pip/commands/list.py", line 151, in output_package_listing
    if dist_is_editable(dist):
  File "/usr/lib/python2.7/dist-packages/pip/util.py", line 366, in dist_is_editable
    req = FrozenRequirement.from_dist(dist, [])
  File "/usr/lib/python2.7/dist-packages/pip/__init__.py", line 286, in from_dist
    assert len(specs) == 1 and specs[0][0] == '=='
AssertionError

Storing debug log for failure in /tmp/tmp3VdLYx

```
解决办法：
* 方法1. `pip install --upgrade distribute `
* 方法2. 
```
pip --version # 1.5.4
curl -O https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
pip --version # 6.0.8
hash -r # reset bash cache
```
* 方法3.
```
pip install -U setuptools
pip install -U pip
```
