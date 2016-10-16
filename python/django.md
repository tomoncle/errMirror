#django开发异常

### 'id' can only be used as a field name if the field also sets 'primary_key=True'. 
```shell
root@aric-ThinkPad-E450:/opt/app/workspace/iaasms# python manage.py makemigrations &&  python manage.py migrate
CommandError: System check identified some issues:

ERRORS:
storage.Volume_Attachments: (models.E004) 'id' can only be used as a field name if the field also sets 'primary_key=True'.
storage.Volume_Links: (models.E004) 'id' can only be used as a field name if the field also sets 'primary_key=True'.

```
解决办法: 修类属性id 为其他名称,例如:a_id ,c_id 等等,在该数据库中id默认是为主键设置的.


### RuntimeError at /host/add  
### You called this URL via POST, but the URL doesn't end in a slash and you have APPEND_SLASH set. Django can't redirect to the slash URL while maintaining POST data. Change your form to point to localhost:8000/host/add/ (note the trailing slash), or set APPEND_SLASH=False in your Django settings.

解决办法：form表单提交时，action 以'/'结束 。即 action="/host/add/"


### django post 提交 Forbidden (403)
解决办法：导入 from django.views.decorators.csrf import csrf_exempt  在post 请求函数上加 @csrf_exempt 装饰器
