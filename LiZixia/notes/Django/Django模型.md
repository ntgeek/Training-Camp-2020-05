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

