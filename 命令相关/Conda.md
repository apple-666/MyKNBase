教学链接：[https://zhuanlan.zhihu.com/p/348120084](https://zhuanlan.zhihu.com/p/348120084)
# 常用命令
```python
conda create -n 环境名
conda env list 列出环境
Conda activate 环境名 激活你的环境(进入环境)
conda install python=3.6 conda install django=2.2 
	Conda install 包名称 在你的环境中用conda或者pip安装包
Conda list 查看环境中现有的包
conda deactivate # 退出

pip list
更换环境（如py36）：
source activate py36
导出当前环境： conda env export > py36.yaml
会生成一个py36.yaml文件，将其复制到目标机上后执行导入环境操作：
conda env create -f py36.yaml


```


## 环境 relocate：
```python
pip install conda-pack
conda pack -n envname    将old envname打包
conda pack -n rainbow_slt_tool_env -o old_env.tar.gz     在now 目录生成old_env.tar.gz。 has env_resource
然后解压到env文件夹下
```
