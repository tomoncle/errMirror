# docker 内部运行异常

### Failed to get D-Bus connection: Operation not permitted 
解决方法：
```shell
docker run --privileged  -dti -e "container=docker"  -v /sys/fs/cgroup:/sys/fs/cgroup:ro centos:7 init 
# 或者
docker run --privileged -d -ti -e "container=docker"  -v /sys/fs/cgroup:/sys/fs/cgroup  trinitronx/ansible-base:stable-centos7  /usr/sbin/init

```
