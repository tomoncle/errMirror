# requests Exceptions

### requests.exceptions.ProxyError: HTTPConnectionPool(host='127.0.0.1', port=53284): Max retries exceeded with url: http://172.16.4.31:8500/v1/status/leader (Caused by ProxyError('Cannot connect to proxy.', NewConnectionError('<requests.packages.urllib3.connection.HTTPConnection object at 0x7f79040a1810>: Failed to establish a new connection: [Errno 111] Connection refused',)))
* 方法1:设置环境变量
  ```python
  import os

  print filter(lambda x: x.lower().endswith('_proxy'), os.environ)
  for k in list(os.environ.keys()):
      if k.lower().endswith('_proxy'):
          # 这些个功能都只能改变python进程的环境变量
          del os.environ[k]
  ```
* 方法2:清空代理
  ```python
  import requests

  proxy = {
      'http': None,
      'https': None
  }
  res = requests.get('http://172.16.4.31:8500/v1/status/leader', proxies=proxy)
  print res.status_code
  print res.content
  ```
