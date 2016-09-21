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
