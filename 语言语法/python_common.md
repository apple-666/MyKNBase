# 多线程
```python
多线程 lock锁学习参考文档
https://blog.kamino.link/2021/03/01/Python-Multithreading-in-detail/
```

# Json解析
```python
Condif的类：
class Config(object):
    @staticmethond
    def parse_config_info(file_path):
        try:
            with open(file_path, 'r', encoding='ut***) a**
                c_dict = json.load(f)
        except E**:
            return False, None
        return True, c_dict

class InrConf(Config):
    inr_config = {}

    @classmethod
    def parse_inr_config(cls):
        path = "**.json"
        ret, config_dict = cls.parse_config_info(path)
        ***
        return ret, config_dict

    @classmethod
    def inr_config_ini(cls):
        ret, c = cls.parse_slt_config()
        if:
            cls.inr_config = c

    @classsss
    def update**(cls, k, v):
        cls.inr_config.updata({k:v}

    @cccc
    def get_kkkk_config(cls):
        return cls.inr_config.get("xx", n)
        
        
```
