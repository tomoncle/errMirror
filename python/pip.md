# python pip常见异常

### command 'x86_64-linux-gnu-gcc' failed with exit status 1
```
解决办法：sudo apt-get install libxml2-dev libxslt1-dev zlib1g-dev
```

### build/temp.linux-x86_64-2.7/_openssl.c:433:30: fatal error: openssl/opensslv.h: 没有那个文件或目录
```
解决办法：sudo apt-get install libssl-dev
```

### UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 49: ordinal not in range(128)
解决办法,在python文件头部引用以下代码：
```python
import sys  
reload(sys)  
sys.setdefaultencoding('utf8')  
```

### error: Setup script exited with error: command 'gcc' failed with exit status 1
```
解决办法：sudo apt-get install python-dev
```

### pip install cryptography 失败
```
解决办法：apt-get install libffi-dev openssl libssl-dev
```

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
      
      
### tornado/speedups.c:2:20: fatal error: Python.h: No such file or directory
```
解决办法： sudo apt-get install python-dev　或者 sudo apt-get install python3-dev
```

### /usr/include/python2.7/Python.h:19:20: fatal error: limits.h: No such file or directory
```
解决方案：Alpine linux uses musl libc. You probably need to install musl-dev.即 apk add musl-dev 
```


### /usr/lib/gcc/x86_64-alpine-linux-musl/4.8.3/../../../../x86_64-alpine-linux-musl/bin/ld: cannot find -lgcc_s
```
解决方案：　apk add linux-headers libgcc
```


### SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)
```
解决方案：
```

### No module named singledispatch
```
解决方案： pip install singledispatch
```

### No module named singledispatch
```
解决方案： pip install backports_abc
```
### Error loading MySQLdb module: No module named MySQLdb
```
解决方案： sudo pip install MySQL-python
```
### pip install MySQL-python==1.2.3
```
Collecting MySQL-python==1.2.3 (from -r r.txt (line 12))
  Downloading https://files.pythonhosted.org/packages/9a/81/924d6799494cf7fb24370335c2f782088d6ac4f79e4137d4df94cea3582c/MySQL-python-1.2.3.tar.gz (70kB)
    100% |████████████████████████████████| 71kB 63kB/s
    Complete output from command python setup.py egg_info:
    sh: mysql_config: not found
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-install-MFHfIW/MySQL-python/setup.py", line 15, in <module>
        metadata, options = get_config()
      File "setup_posix.py", line 43, in get_config
        libs = mysql_config("libs_r")
      File "setup_posix.py", line 24, in mysql_config
        raise EnvironmentError("%s not found" % (mysql_config.path,))
    EnvironmentError: mysql_config not found

    ---------------------------------------
```
* ubuntu: `$ sudo apt install libmysqlclient-dev python-dev`
* alpine: `$ apk add mariadb-dev mariadb-client mariadb-libs`

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

### pip2.7 install 
```
Traceback (most recent call last):
  File "/usr/local/bin/pip2.7", line 6, in <module>
    from pip._internal import main
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/__init__.py", line 40, in <module>
    from pip._internal.cli.autocompletion import autocomplete
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/cli/autocompletion.py", line 8, in <module>
    from pip._internal.cli.main_parser import create_main_parser
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/cli/main_parser.py", line 12, in <module>
    from pip._internal.commands import (
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/commands/__init__.py", line 6, in <module>
    from pip._internal.commands.completion import CompletionCommand
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/commands/completion.py", line 6, in <module>
    from pip._internal.cli.base_command import Command
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/cli/base_command.py", line 20, in <module>
    from pip._internal.download import PipSession
  File "/usr/local/lib/python2.7/dist-packages/pip/_internal/download.py", line 15, in <module>
    from pip._vendor import requests, six, urllib3
  File "/usr/local/lib/python2.7/dist-packages/pip/_vendor/requests/__init__.py", line 97, in <module>
    from pip._vendor.urllib3.contrib import pyopenssl
  File "/usr/local/lib/python2.7/dist-packages/pip/_vendor/urllib3/contrib/pyopenssl.py", line 46, in <module>
    import OpenSSL.SSL
  File "/usr/lib/python2.7/dist-packages/OpenSSL/__init__.py", line 8, in <module>
    from OpenSSL import rand, crypto, SSL
  File "/usr/lib/python2.7/dist-packages/OpenSSL/SSL.py", line 118, in <module>
    SSL_ST_INIT = _lib.SSL_ST_INIT
AttributeError: 'module' object has no attribute 'SSL_ST_INIT'
```
* 解决：
```
$ sudo rm -rf /usr/lib/python2.7/dist-packages/OpenSSL
$ sudo rm -rf /usr/lib/python2.7/dist-packages/pyOpenSS*
$ sudo pip2.7 install pyopenssl
```

