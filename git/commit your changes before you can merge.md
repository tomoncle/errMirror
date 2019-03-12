## git pull异常：
```shell
You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you can merge.
```

##### 有2个解决办法:

* 1.保留你本地的修改
```bash
git merge --abort
git reset --merge

合并后记得一定要提交这个本地的合并
然后在获取线上仓库
git pull
```


* 2.down线上代码版本,抛弃本地的修改
```
不建议这样做,但是如果你本地修改不大,或者自己有一份备份留存,可以直接用线上最新版本覆盖到本地
git fetch --all
git reset --hard origin/master
git fetch

```
