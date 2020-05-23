# Django模型

## 数据库配置

在项目的 settings.py 文件中找到 DATABASES 配置项，将其信息修改为：

```mysql
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',  # 或者使用 mysql.connector.django
        'NAME': 'test',
        'USER': 'test',
        'PASSWORD': 'test123',
        'HOST':'localhost',
        'PORT':'3306',
    }
}
```



上面包含数据库名称和用户的信息，它们与 MySQL 中对应数据库和用户的设置相同。Django 根据这一设置，与 MySQL 中相应的数据库和用户连接起来。

## 定义模型

### 创建APP

```
django-admin startapp appname
```

类名代表了数据库表名，且继承了`models.Model`，类里面的字段代表数据表中的字段(name)，数据类型则由`CharField`（相当于varchar）、`DateField`（相当于datetime）， `max_length` 参数限定长度。

### 数据库创建

```
$ python manage.py migrate   # 创建表结构
$ python manage.py makemigrations TestModel  # 让 Django 知道我们在我们的模型有一些变更
$ python manage.py migrate TestModel   # 创建表结构
```

