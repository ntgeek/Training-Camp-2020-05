# 请求和响应

## 创建项目

```django
django-admin startproject [name]
```

`startproject`会生成一个Django项目，文件结构如下：

> `name/`:项目容器
>
> > `manage.py`：管理项目的命令行工具
> >
> > `name/`：项目文件
> >
> > >`__init__.py`：Python包定义
> > >
> > >`setting.py`：项目配置文件
> > >
> > >`urls.py`：项目URL声明
> > >
> > >`asgi.py`：运行在 `ASGI` 兼容的Web服务器上的入口
> > >
> > >`wsgi.py`运行在 `WSGI` 兼容的Web服务器上的入口

---

## 启动开发调试服务器

```django
python manage.py runserver [portID]
```

## 创建应用

```django
python manage.py startapp [appname]
```

## 编写视图

编辑`view.py` 

## 编辑`URLconf`

- 函数`include()`允许引用其它 `URLconfs`。每当 `Django` 遇到 `include()` 时，它会截断与此项匹配的 URL 的部分，并将剩余的字符串发送到 `URLconf` 以供进一步处理。

- 函数`path()`
  - `route`(必须)：`route` 是一个匹配 URL 的准则（类似正则表达式）。当 `Django `响应一个请求时，它会从 `urlpatterns` 的第一项开始，按顺序依次匹配列表中的项，直到找到匹配的项。
  - `view`(必须)：当 `Django` 找到了一个匹配的准则，就会调用这个特定的视图函数，并传入一个 `HttpRequest`对象作为第一个参数，被“捕获”的参数以关键字参数的形式传入。
  - `name`：为你的 URL 取名能使你在 `Django` 的任意地方唯一地引用它，尤其是在模板中。这个有用的特性允许你只改一个文件就能全局地修改某个 URL 模式。

---

# 数据库配置

## 配置`setting.py`

1. 默认数据库`SQLite`

2. 通常， `INSTALLED_APPS` 默认包括了以下` Django `的自带应用：

	- `django.contrib.admin`-- 管理员站点， 你很快就会使用它。
	- `django.contrib.auth` -- 认证授权系统。
	- `django.contrib.contenttypes` -- 内容类型框架。
	- `django.contrib.sessions` -- 会话框架。
	- `django.contrib.messages` -- 消息框架。
	- `django.contrib.staticfiles` -- 管理静态文件的框架。
	
3. 初始化数据库

   ```django
   python manage.py migrate
   ```

   这个 `migrate` 命令检查 `INSTALLED_APPS` 设置，为其中的每个应用创建需要的数据表，至于具体会创建什么，这取决于你的 `mysite/settings.py` 设置文件和每个应用的数据库迁移文件。这个命令所执行的每个迁移操作都会在终端中显示出来。

4. 语言时区设置

   ```django
   LANGUAGE_CODE = 'zh-hans'
   TIME_ZONE = 'Asia/Shanghai'
   ```

## 创建模型



