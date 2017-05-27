# python runtime exception

### UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 49: ordinal not in range(128)

解决办法,在python文件头部引用以下代码：
```python
import sys  
reload(sys)  
sys.setdefaultencoding('utf8') 
```
