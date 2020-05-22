# Django模板

- 模板使代码和数据分离

## 模板标签

使用`render()`函数返回，参数为`请求`,`模板页面`,`变量字典集`

### 变量

```django
view:{"HTML变量名":"view变量名"}
html:{{变量名}}
```

### 列表

使用`.`可以取出传入变量的列表的元素

### 字典

使用`.key`取出传入字典对应key的值

### 过滤器

```django
{{变量名 | 过滤器}}
```

- 类似管道可多段链接
- 有些过滤器有参数。 过滤器的参数跟随冒号之后并且总是以双引号包含

- `default`：如果view传入的为false，则使用默认值
- `length`:返回对象长度
- `filesizeformat`：更易读的方式显示文件大小
- `date`:`Y-m-d H:i:s`格式时间
- `truncatechars`：截断字符
- `safe`将字符串标记为安全，不转义

### if/else标签

```django
{% if condition1 %}
	display1
{% elif condition2 %}
	display2
{% else %}
	display
{% endif %}
```

### for标签

```django
{% for X in Y [reversed]%}
	{{ Y }}
{% endfor %}
```

- 遍历字典：用`for`和`.items`分别获取

在 {% for %} 标签里可以通过 `{{forloop}}` 变量获取循环序号。

- `forloop.counter`: 顺序获取循环序号，从 1 开始计算
- `forloop.counter0`: 顺序获取循环序号，从 0 开始计算
- `forloop.revcounter`: 倒叙获取循环序号，结尾序号为 1
- `forloop.revcounter0`: 倒叙获取循环序号，结尾序号为 0
- `forloop.first`（一般配合if标签使用）: 第一条数据返回 True，其他数据返回 False
- `forloop.last`（一般配合if标签使用）: 最后一条数据返回 True，其他数据返回 False



- 可选的 {% empty %} 从句：在循环为空的时候执行（即 in 后面的参数布尔值为 False ）。

### ifequal/ifnotequal 标签

- `{% ifequal %} `标签比较两个值，当他们相等时，显示在 `{% ifequal %}` 和` {% endifequal %}` 之中所有的值。

  ```django
  {% ifequal section 'sitenews' %}
      <h1>Site News</h1>
  {% else %}
      <h1>No News Here</h1>
  {% endifequal %}
  ```

  

### 注释标签

- 使用`{# #}`

### include标签

`{# include #}`标签允许模板中包含其他模板内容

## 模板继承

所有的 {% block %} 标签告诉模板引擎，子模板可以重载这些部分。

```django
# 主文件
{% block name %}
{% endblock %}
```

```django
{% extends "主文件.html" %}
{% block name %}
{% endblock %}
```

## csrf_token

`csrf_token` 用于form表单中，作用是跨站请求伪造保护。
如果不用`｛% csrf_token %｝`标签，在用` form` 表单时，要再次跳转页面会报403权限错误。
用了`｛% csrf_token %｝`标签，在 `form` 表单提交数据时，才会成功。

## 自定义标签和过滤器

1. 在 `app` 目录下创建 `templatetags` 目录(目录名只能是 `templatetags`)。

2. 在 `templatetags` 目录下创建任意 `py` 文件，如：`my_tags.py`

3. 在该 `py `文件下：

```python
from django import template

register = template.Library()   #register的名字是固定的,不可改变
```

4、利用装饰器 `@register.filter` 自定义过滤器。

**注意：**装饰器的参数最多只能有 2 个。

```django
@register.filter
def my_filter(v1, v2):
    return v1 * v2
```

5、利用装饰器 `@register.simple_tag` 自定义标签。

```django
@register.simple_tag
def my_tag1(v1, v2, v3):
    return v1 * v2 * v3
```

6、在使用自定义标签和过滤器前，要在 `html` 文件 `body` 的最上方中导入该 `py` 文件。

```django
{% load my_tags %}
```

7、在 HTML 中使用自定义过滤器。

```django
{{ 11|my_filter:22 }}
```

8、在 HTML 中使用自定义标签。

```django
{% my_tag1 11 22 33 %}
```

9、语义化标签

- 在该 `py` 文件中导入 `mark_safe`。

```python
from django.utils.safestring import mark_safe
```

定义标签时，用上` mark_safe `方法，令标签语义化，相当于` jQuery` 中的 `html() `方法。

和前端HTML文件中的过滤器` safe` 效果一样。

```python
@register.simple_tag
def my_html(v1, v2):
    temp_html = "<input type='text' id='%s' class='%s' />" %(v1, v2)
    return mark_safe(temp_html)
```

在HTML中使用该自定义标签，在页面中动态创建标签。

```django
{% my_html "zzz" "xxx" %}
```

## 配置静态文件

1、在项目根目录下创建 statics 目录。

2、在` settings `文件的最下方配置添加以下配置：

```
STATIC_URL = '/static/' # 别名 
STATICFILES_DIRS = [ 
    os.path.join(BASE_DIR, "statics"), 
]
```

3、在 `statics `目录下创建` css `目录，`js` 目录，`images` 目录，`plugins` 目录， 分别放 `css文件`，`js文件`，`图片`，`插件`。

4、把`bootstrap` 框架放入插件目录` plugins`。

5、在 HTML 文件的`head `标签中引入` bootstrap`。

**注意：**此时引用路径中的要用配置文件中的别名 `static`，而不是目录` statics`。

```
<link rel="stylesheet" href="/static/plugins/bootstrap-3.3.7-dist/css/bootstrap.css">
```

在模板中使用需要加入 `{% load static %}`代码