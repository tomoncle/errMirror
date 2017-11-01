# sed 语法异常

### sed: -e 表达式 #1, 字符 9: “s”的未知选项↵

* 将分隔符`/`替换为`#`即可:
  ```bash
  # $ sed -i "s/\/home\/test\/work\/pethug/${path}/g" $path/pethug-agent/setting.py
  $ sed -i "s#/home/test/work/pethug#${path}#g" $path/pethug-agent/setting.py
  ```
