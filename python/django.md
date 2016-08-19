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


