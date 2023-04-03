Linux下常用命令
# 文件相关
```python
ll -t   时间降序
ll -rt  时间升序
ll -al  详细信息

查找目录下 有str的文件
grep -rn "apple_come" ./

查找目录下符合文件名的文件
find -n "*apple*"
```

# 磁盘空间相关
```python
du:
  -h 可读信息
  --max-depth=目录层数
常用：
du -h ./ --max-dipth=1 

df:
  查看文件系统的占用
常用：
  df -h
```
  
