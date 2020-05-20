# Django 开发模式

- MVC设计模式

    - Model：用于封装与应用程序的业务逻辑相关的数据及对数据的处理办法
    - View：负责数据的显示和呈现，是对用户的直接输出
    - Controller：负责从用户端收集用户输入，主要处理用户交互。

- MVT模式

    - Model：负责业务对象和数据库（ORM）的对象
    - View：负责业务逻辑，在适当时候调用Model和Template
    - Template：负责把页面展示给用户
    - URL分发器
