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