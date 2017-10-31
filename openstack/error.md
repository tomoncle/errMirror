# openstack error


## nova-compute error

```bash
2017-10-30 10:53:40.716 12380 DEBUG oslo_service.service [req-6c6aca63-1826-4900-b41e-2089ec4df83a - - - - -] ******************************************************************************** log_opt_values /usr/local/lib/python2.7/dist-packages/oslo_config/cfg.py:2888
2017-10-30 10:53:40.717 12380 INFO nova.service [-] Starting compute node (version 12.0.4)
2017-10-30 10:53:40.719 12380 DEBUG nova.virt.libvirt.host [-] Starting native event thread _init_events /usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py:452
2017-10-30 10:53:40.719 12380 DEBUG nova.virt.libvirt.host [-] Starting green dispatch thread _init_events /usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py:458
2017-10-30 10:53:40.720 12380 DEBUG nova.virt.libvirt.host [-] Connecting to libvirt: qemu:///system _get_new_connection /usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py:463
2017-10-30 10:53:40.732 12380 INFO nova.virt.libvirt.driver [-] Connection event '0' reason 'Failed to connect to libvirt'
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host [req-56657389-9773-4c6e-b9be-e367408c2740 - - - - -] Connection to libvirt failed: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host Traceback (most recent call last):
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py", line 528, in get_connection
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     conn = self._get_connection()
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py", line 515, in _get_connection
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     wrapped_conn = self._get_new_connection()
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py", line 467, in _get_new_connection
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     wrapped_conn = self._connect(self._uri, self._read_only)
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/host.py", line 321, in _connect
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     libvirt.openAuth, uri, auth, flags)
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/eventlet/tpool.py", line 141, in proxy_call
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     rv = execute(f, *args, **kwargs)
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/eventlet/tpool.py", line 122, in execute
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     six.reraise(c, e, tb)
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/eventlet/tpool.py", line 80, in tworker
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     rv = meth(*args, **kwargs)
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host   File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in openAuth
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host     if ret is None:raise libvirtError('virConnectOpenAuth() failed')
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory
2017-10-30 10:53:40.756 12380 ERROR nova.virt.libvirt.host 
```

* 解决方法:
  ```bash
  $ service libvirtd restart
  $ service nova-compute status
  $ nova service-list
  ```
