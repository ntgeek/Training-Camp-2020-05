# Shell教程

## 起始行

```
#!/bin/bash
```

## 向屏幕输出

```
echo 显示内容
```

## 执行Shell程序

```
chmod +x ./name.sh
./name.sh
```

## 变量

1. 和C差不多
使用变量时`${varname} `

2. 只读变量
就常量
定义变量后`readonly varname`

3. 删除变量
使用`unset varname`

## 字符串

1. 单引号
单引号里面字符串原样输出，变量无效

2. 双引号
可以有变量，可以有转义字符

3. 字符串可以拼接，不用`+`号

4. 获取字符串长度
```
str = "abcd"
echo ${#str}
```

5. 提取子串
```
str="abcd"
echo ${str:1:3}
# 全闭区间
```

6. 查找子串
```
str="abcd"
echo `expr index "$strinh" ab`
# 哪个字母先出现就计算哪个
```

## 数组

与C类似，只有一维数组

1. 定义数组
```
name = (v1 v2 ... vn)
# 可以给单独变量赋值，同C一样
```

2. 读取数组
```
${name[index]} 
```

3. 获取数组长度
```
# 获取元素个数
${#name[@]} 或 ${name[*]}
# 获取单个元素长度
${#name[index]}
```

4. 遍历数组
```
${name[@]} 或 ${name[*]}
```

## 注释

以`#`开头的行就是注释

- 多行注释：
```
:<<#
1
2
3
4#
```

## 传参

1. 向脚本传参

脚本内获取参数格式`$n`
`$0`为执行的文件名

另外，还有几个特殊字符用来处理参数：

|参数处理|    说明|
|:--:|:--:|
|`$#`  |传递到脚本的参数个数|
|`$*`  |以一个单字符串显示所有向脚本传递的参数。如`$*`用「"」括起来的情况、以"$1 $2 … $n"的形式输出所有参数。|
|`$$`  |脚本运行的当前进程ID号|
|`$!`  |后台运行的最后一个进程的ID号|
|`$@` | 与`$*`相同，但是使用时加引号，并在引号中返回每个参数。如`$@`用「"」括起来的情况、以"$1" "$2" … "$n" 的形式输出所有参数|
|`$-` | 显示Shell使用的当前选项，与set命令功能相同。|
|`$?`|  显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。|

## 运算符

1. 使用单引号加expr
```
val = `expr 1 + 1`
echo "$val"
```
- 表达式和运算符之间要有空格，例如 2+2 是不对的，必须写成 2 + 2
- 完整的表达式要被 ```` 包含

2. 算数运算符

常用`+`,`-`,`*`,`/`,`%`,`=`,`==`,`!=`

- 条件表达式要放在方括号之间，并且要有空格，例如: `[$a==$b]` 是错误的，必须写成 `[ $a == $b ]`。

3. 关系运算符

关系运算符只支持数字，不支持字符串（除非字符串是数字）

- `-eq`相等
- `-ne`不相等
- `-gt`大于
- `lt`小于
- `ge`大于等于
- `le`小于等于

- 使用方括号，要有空格

4. 布尔运算符

- `!` 非运算
- `-o`或运算
- `-a`和运算

- 使用方括号，要有空格 

5. 逻辑运算符

- `&&`逻辑与
- `||`逻辑或

- 使用方括号，要有空格 

6. 字符串运算符

- `=`是否相等
- `!=`是否不相等
- `-z`长度是否为0
- `-n`长度是否不为0
- `$`是否为空

- 使用方括号，要有空格 

7. 文件测试运算符

用于检测Unix文件各种属性 
- 使用方括号，要有空格 

```
-b file  检测文件是否是块设备文件，如果是，则返回 true。 
-c file  检测文件是否是字符设备文件，如果是，则返回 true。  
-d file  检测文件是否是目录，如果是，则返回 true。   
-f file  检测文件是否是普通文件（既不是目录，也不是设备文件），如果是，则返回 true。 
-g file  检测文件是否设置了 SGID 位，如果是，则返回 true。  
-k file  检测文件是否设置了粘着位(Sticky Bit)，如果是，则返回 true。 
-p file  检测文件是否是有名管道，如果是，则返回 true。   
-u file  检测文件是否设置了 SUID 位，如果是，则返回 true。  
-r file  检测文件是否可读，如果是，则返回 true。 
-w file  检测文件是否可写，如果是，则返回 true。 
-x file  检测文件是否可执行，如果是，则返回 true。   
-s file  检测文件是否为空（文件大小是否大于0），不为空返回 true。    
-e file  检测文件（包括目录）是否存在，如果是，则返回 true。 

# 其他检查符：

-S: 判断某文件是否 socket。
-L: 检测文件是否存在并且是一个符号链接。
```

## echo

- `\c`不换行

- 显示定向结果至文件
```
echo string > file
```

- 原样输出使用单引号

- 显示命令执行结果
```
echo `command`
```

## printf 

```
printf format-string [arguments]
```

- 格式控制符：`%s``%c``%d``%f`
- `%-10s`,加有`-`为左对齐，无则右对齐；浮点小数格式同C

- 转义符
    - `\a` 警告字符
    - `\b` 后退
    - `\c` 抑制换行
    - `\f` 换页
    - `\n` 换行
    - `\r` 回车
    - `\t` 水平制表符
    - `\v` 垂直制表符
    - `\0ddd` 1-3位八进制字符

## test

用于检查某个条件是否成立，可用于数值、字符和文件

## 流程控制

### if...else

1. if

```
if condition
then
    command1
    command2
fi
```

- 单行写带上分号

2. if...else...

```
if condition
then 
    command1
    command2
else
    command
fi
```

3. if...elif...else

```
if condition1
then
    command1
elif condition2
then
    command2
else
    command
fi
```

- if...else语句常和test使用

### for循环

```
for var in i1 i2 ...iN
do
    command1
    command2
done
```

- in列表可包含替换、字符串、文件

### while循环

```
while condition
do
    command
done
```

### let

用于执行一个或多个表达式，变量计算不需要加上$

### until循环

```
until condition
do
    command
done
```

### case

```
case value in
var1)
    command1
    command2
    ;;
var2)
    command1
    command2
    ...
    ;;
...
*）
    command
    ;;
esac
```

- value可以为变量或常数
- 如果没有捕获模式，则捕获`*`
- 支持正则表达式

### 跳出循环

1. break

2. continue


## 函数

- 函数定义

```
[ function ] funname [()]

{

    action;
    
    [return int;]
}
```

示例

```
funwithreturn(){
    echo "输入第一个num"
    read aNum
    echo "输入第二个num"
    read bNum
    return $(($aNum+$bNum))
}
```

- 函数在使用前必须要定义

- 函数传参和脚本传参类似，参数多于10要用方括号`${10}`

|参数处理|说明|
|:--:|:--:|
|`$#`|  传递到脚本或函数的参数个数|
|`$*`|  以一个单字符串显示所有向脚本传递的参数|
|`$$`|  脚本运行的当前进程ID号|
|`$!`|  后台运行的最后一个进程的ID号|
|`$@`|  与`$*`相同，但是使用时加引号，并在引号中返回每个参数。|
|`$-`|  显示Shell使用的当前选项，与set命令功能相同。|
|`$?`|  显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。|

## 输入、输出重定向

|命令  |  说明|
|:--:|:--:|
|`command > file`|  将输出重定向到 file。|
|`command < file`  |将输入重定向到 file。|
|`command >> file` |将输出以追加的方式重定向到 file。|
|`n > file`    |将文件描述符为 n 的文件重定向到 file。|
|`n >> file`   |将文件描述符为 n 的文件以追加的方式重定向到 file。|
|`n >& m`  |将输出文件 m 和 n 合并。|
|`n <& m`  |将输入文件 m 和 n 合并。|
|`<< tag`  |将开始标记 tag 和结束标记 tag 之间的内容作为输入。|

需要注意的是文件描述符 0 通常是标准输入（STDIN），1 是标准输出（STDOUT），2 是标准错误输出（STDERR）。

一般情况下，每个 Unix/Linux 命令运行时都会打开三个文件：

- 标准输入文件(stdin)：stdin的文件描述符为0，Unix程序默认从stdin读取数据。
- 标准输出文件(stdout)：stdout 的文件描述符为1，Unix程序默认向stdout输出数据。
- 标准错误文件(stderr)：stderr的文件描述符为2，Unix程序会向stderr流中写入错误信息。

- Here Document

Here Document 是 Shell 中的一种特殊的重定向方式，用来将输入重定向到一个交互式 Shell 脚本或程序。

```
command << delimiter
    document
delimiter
```

- `/dev/null`文件

```
command > /dev/null
```

/dev/null 是一个特殊的文件，写入到它的内容都会被丢弃；如果尝试从该文件读取内容，什么也读不到。但是 /dev/null 文件非常有用，将命令的输出重定向到它，会起到"禁止输出"的效果。

## 文件包含

和其他语言一样，Shell 也可以包含外部脚本。这样可以很方便的封装一些公用的代码作为一个独立的文件。

```
. filename
或
source filename
```
