

## django database operations


### 创建一个名为User的app

```cmd
python manage.py startapp User
```


### 模型层定义

```cmd
# vim User/models.py

from django.db import models

# Create your models here.

class User(models.Model):
    name = models.CharField(max_length=32)
    age = models.IntegerField()
    email = models.EmailField()
```


### 配置数据库
ophira是项目名， 在settings.py里面修改DATABASES里的内容，这里我们配置为我们的mysql数据库。

```cmd
# vim ophira/settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'ophira',
        'HOST': 'maxscale.alv.pub',
        'USER': 'alvin',
        'PASSWORD': 'sophiroth',
        'PORT': 4006

    }
}
```

### 添加App

```
# vim settings.py
INSTALLED_APPS = (
User
)
```

### 同步数据库

```cmd
python  manage.py  validate/check  #检测数据库配置是否有错 旧版本是vilidate,新新版是check

python  manage.py  makemigrations  #创建对应数据库的映射语句

python  manage.py  syncdb   同步或者映射数据库
```


### 进入shell模式

```
python manage.py shell
```

#### 导入表

```python
from User.models import User

```

### 添加记录

#### 第一种方式

```
u = User(name='alvin',age=25,email='alvin.wan@sophiroth.com')
u.save()
```

然后就保存了，可以通过select * from user_user查询结果确认一下。

#### 第二种方式

```
User.object.create(name='alvin',age=25,email=alvin.wan@sophiroth.com)
```

### 查询所有记录


all_u = User.objects.all() # 相当于select * from user_user


### 指定条件查询

filter_u = User.objects.filter(name='alvin') # 相当于select * from user_user where name='alvin'


### 指定唯一条件查询


get_u = User.objects.get(id=4)  # get的 条件必须为唯一的，通常为主键。

### 查询结果按指定列排序


#### 顺序查询
order_u = User.objects.order_by('age') #查询到的结果按照age字段从低到高排序。

#### 倒序查询



order_u = User.objects.order_by('-age') #查询到的结果按照age字段从高到低排序。

### 取最前面N行。（limit)

order_u = User.objects.order_by('-age')[:3] #查询到的结果按照age字段高到低排序取最前面三行。


### 多条件结合

#### where 之后排序
先用age=25做条件查询，然后用order_by 排序。

fo_u = User.object.filter(age=25).order_by('name')



### 修改数据


u = User.objects.get(id=4)  #获取一条id=4的数据
u.name="Alvin wan"  #修改name为“Alvin Wan”
u.save() #保存生效。

### 删除数据

u = User.objects.get(id=4)  #获取一条id=4的数据
u.delete() #删除数据， 不需要保存，直接删除。