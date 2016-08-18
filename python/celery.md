# celery异常 

### 使用django+celery+redis,调用任务接口异常1
```
Can't pickle <type 'cStringIO.StringO'>: attribute lookup cStringIO.StringO failed 
```
原因: pickle不能序列化非纯python语言编写的对象,如request对象,引用了cStringIO这个非python库,就会报以上异常.去掉这个参数,或者对象即可,当然你可以使用python语言重新封装该对象.


### 使用django+celery+redis,调用任务接口异常2
```
[2016-08-18 17:41:41,842: CRITICAL/MainProcess] Task iaasms.cpms.cloud.nova.flavor_create[6fe21e0b-b065-4494-9c4b-b0f23688adf8] INTERNAL ERROR: PicklingError("Can't pickle <class 'celery.utils.log.ProcessAwareLogger'>: attribute lookup celery.utils.log.ProcessAwareLogger failed",)
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/celery/app/trace.py", line 283, in trace_task
    uuid, retval, SUCCESS, request=task_request,
  File "/usr/local/lib/python2.7/dist-packages/celery/backends/base.py", line 271, in store_result
    request=request, **kwargs)
  File "/usr/local/lib/python2.7/dist-packages/djcelery/backends/database.py", line 29, in _store_result
    traceback=traceback, children=self.current_task_children(request),
  File "/usr/local/lib/python2.7/dist-packages/djcelery/managers.py", line 42, in _inner
    return fun(*args, **kwargs)
  File "/usr/local/lib/python2.7/dist-packages/djcelery/managers.py", line 181, in store_result
    'meta': {'children': children}})
  File "/usr/local/lib/python2.7/dist-packages/djcelery/managers.py", line 87, in update_or_create
    return get_queryset(self).update_or_create(**kwargs)
  File "/usr/local/lib/python2.7/dist-packages/djcelery/managers.py", line 70, in update_or_create
    obj, created = self.get_or_create(**kwargs)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/query.py", line 424, in get_or_create
    return self._create_object_from_params(lookup, params)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/query.py", line 457, in _create_object_from_params
    obj.save(force_insert=True, using=self.db)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/base.py", line 589, in save
    force_update=force_update, update_fields=update_fields)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/base.py", line 617, in save_base
    updated = self._save_table(raw, cls, force_insert, force_update, using, update_fields)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/base.py", line 698, in _save_table
    result = self._do_insert(cls._base_manager, using, fields, update_pk, raw)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/base.py", line 731, in _do_insert
    using=using, raw=raw)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/manager.py", line 92, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/query.py", line 921, in _insert
    return query.get_compiler(using=using).execute_sql(return_id)
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/sql/compiler.py", line 920, in execute_sql
    for sql, params in self.as_sql():
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/sql/compiler.py", line 878, in as_sql
    for obj in self.query.objs
  File "/usr/local/lib/python2.7/dist-packages/django/db/models/fields/__init__.py", line 627, in get_db_prep_save
    prepared=False)
  File "/usr/local/lib/python2.7/dist-packages/djcelery/picklefield.py", line 104, in get_db_prep_value
    return force_text(encode(value, self.compress, self.protocol))
  File "/usr/local/lib/python2.7/dist-packages/djcelery/picklefield.py", line 68, in encode
    pickle.dumps(value, pickle_protocol), compress_object),
PicklingError: Can't pickle <class 'celery.utils.log.ProcessAwareLogger'>: attribute lookup celery.utils.log.ProcessAwareLogger failed
```
原因.我的任务接口中的返回值对象含有不能序列化的参数,或者该对象就不能序列化, 如果没有要求,删掉该返回值,即不写 return xxx ,
当然你想return 的话要检测该对象的序列化参数或对象是否是纯python库.举个例子,假如返回的对象含有c++的库,就会抛出异常
