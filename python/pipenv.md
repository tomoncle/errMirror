# pipenv error

### `$ pipenv lock` 异常
```
Locking [dev-packages] dependencies...
Locking [packages] dependencies...
n <module>
    from .vendor.requirementslib import Requirement
  File "/usr/local/lib/python2.7/dist-packages/pipenv/vendor/requirementslib/__init__.py", line 6, in <module>
    from .models import Requirement, Lockfile, Pipfile
  File "/usr/local/lib/python2.7/dist-packages/pipenv/vendor/requirementslib/models/__init__.py", line 8, in <module>
    from .requirements import Requirement
  File "/usr/local/lib/python2.7/dist-packages/pipenv/vendor/requirementslib/models/requirements.py", line 11, in <module>
    from pkg_resources import RequirementParseError
ImportError: cannot import name RequirementParseError

```
  * `$ pip install -U pipenv`
