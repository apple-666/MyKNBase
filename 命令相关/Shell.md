Study:https://blog.csdn.net/weixin_42313749/article/details/120524768

my
```shell
#!/bin/bash

dir1_1=/root/draft/a/
dir1_2=/root/draft/b/

dir2=/root/draft/t1/script/

dir3=/root/draft/t1/

dir4=/root/draft/t1/

# 1,拷贝trace
cp -r $dir1_1 $dir1_2

# 2,到avp/script下执行
cd $dir2
./b2.sh

# 3,到avp下执行index 生成trace id
cd $dir3
./b3.sh
trace_id=111

# 4,到avp下 用trace id执行index
cd $dir4
echo "trace_id:$trace_id"
./b4.sh
~                    
```
