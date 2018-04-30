# nginx 代理异常

### upstream server temporarily disabled while reading response header from upstream, client: 183.240.19.16 ...
```
原因: cookie携带的header太多了

配置: 设置proxy_pass上面三行内容
  location / {
      proxy_buffer_size  128k;
      proxy_buffers   32 32k;
      proxy_busy_buffers_size 128k;
      proxy_pass  https://www.google.com;
  }
```
