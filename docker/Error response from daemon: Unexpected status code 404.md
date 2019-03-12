# docker search error

```shell
[root@VM_0_3_centos ~]# docker search tomoncle.online/mysql
Error response from daemon: Unexpected status code 404
```

* 原因：`docker search`只适用于V1版本的docker registry，如果使用V2版本的docker registry需要使用HTTP方式获取,所以有上面错误
* Enable v1 API before using docker search
* Use a curl like that : curl -X GET localhost:5000/v2/_catalog


* 参考：[error-response-from-daemon-unexpected-status-code-404](https://stackoverflow.com/questions/38186367/error-response-from-daemon-unexpected-status-code-404)
