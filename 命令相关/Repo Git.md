```python
[] 代表可选
XXname 代码参数

repo help init                  生成 Repo init 参数的说明和选项列表
repo init --help

repo init -u urlname [options]  当前目录中安装 Repo                （类似于初始化.git）
-u：指定从中检索清单代码库的网址。
-m：选择代码库中的清单文件。如果未选择清单名称，则默认为 default.xml。
-b：指定修订版本，即特定的 manifest-branch。
-g: 
eg:
  repo init -u urlname1 -b xxxx -g open --no-repo-verify --repo-branch=stable


repo sync [project-list-name] 更新本地工作文件 默认同步所有项目的文件 （类似git rebase origin）
-c：仅获取服务器中的当前清单分支
eg：
  repo sync -c  --no-tags   同步最新代码
 


  

```
