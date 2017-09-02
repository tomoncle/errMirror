# python runtime exception

### UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 49: ordinal not in range(128)

解决办法,在python文件头部引用以下代码：
```python
import sys  
reload(sys)  
sys.setdefaultencoding('utf8') 
```

###  File "/usr/local/lib/python2.7/dist-packages/tzlocal/unix.py", line 123, in get_localzone
```bash
  File "/usr/local/lib/python2.7/dist-packages/tzlocal/unix.py", line 123, in get_localzone
    _cache_tz = _get_localzone()
  File "/usr/local/lib/python2.7/dist-packages/tzlocal/unix.py", line 62, in _get_localzone
    return pytz.timezone(etctz.replace(' ', '_'))
  File "/usr/lib/python2.7/dist-packages/pytz/__init__.py", line 170, in timezone
    raise UnknownTimeZoneError(zone)
pytz.exceptions.UnknownTimeZoneError: ''
```
解决办法：
>　`vim /usr/lib/python2.7/dist-packages/pytz/__init__.py +170`
```python
if zone in all_timezones_set:
    fp = open_resource(zone)
    try:
        _tzinfo_cache[zone] = build_tzinfo(zone, fp)
    finally:
        fp.close()
else:
    return
    # raise UnknownTimeZoneError(zone)
```
