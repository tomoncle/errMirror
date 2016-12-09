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
