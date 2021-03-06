# Linux文件与目录管理

- 绝对路径：从根目录`/`开始写起，`/etc/apt/sources.list`
- 相对目录：从`/home/pomelo/a`到`/home/pomelo/b`，写`cd ../b`
- `.`表示当前目录，`..` 表示上级目录

---

## 目录管理常用命令及参数

- `ls`: 列出目录及文件名
- `cd`：切换目录
- `pwd`：显示目前的目录
- `mkdir`：创建一个新的目录
- `rmdir`：删除一个空的目录
- `cp`: 复制文件或目录
- `rm`: 移除文件或目录
- `mv`: 移动文件与目录，或修改文件与目录的名称
- `man`: 查看各命令作用

---

1. `ls`显示目录文件

   ```
   -a ：全部的文件，连同隐藏文件( 开头为 . 的文件) 一起列出来(常用)
   -d ：仅列出目录本身，而不是列出目录内的文件数据(常用)
   -l ：长数据串列出，包含文件的属性与权限等等数据；(常用)
   ```

2. `cd`切换目录

   ```
   cd 相对路径或绝对路径
   ```

3. `pwd`显示当前目录

   -P ：显示出确实的路径，而非使用连结 (link) 路径。

4. `mkdir`创建目录

   ```
   -m ：配置文件的权限
   -p ：帮助你直接将所需要的目录(包含上一级目录)递归创建
   -----------
   mkdir -p /a/b/c
   mkdir -m 755 test
   ```

5. `rmdir`删除空目录

   **-p ：**连同上一级空的目录也一起删除

6. `cp`复制

   ```
   -a：相当于 -pdr 的意思，至于 pdr 请参考下列说明；(常用)
   -d：若来源档为连结档的属性(link file)，则复制连结档属性而非文件本身；
   -f：为强制(force)的意思，若目标文件已经存在且无法开启，则移除后再尝试一次；
   -i：若目标档(destination)已经存在时，在覆盖时会先询问动作的进行(常用)
   -l：进行硬式连结(hard link)的连结档创建，而非复制文件本身；
   -p：连同文件的属性一起复制过去，而非使用默认属性(备份常用)；
   -r：递归持续复制，用于目录的复制行为；(常用)
   -s：复制成为符号连结档 (symbolic link)，即捷径文件；
   -u：若 destination 比 source 旧才升级 destination
   ```

7. `rm`移除

   ```
   -f ：就是 force 的意思，忽略不存在的文件，不会出现警告信息；
   -i ：互动模式，在删除前会询问使用者是否动作
   -r ：递归删除
   ```

8. `mv`移动

   ```
   -f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
   -i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
   -u ：若目标文件已经存在，且 source 比较新，才会升级 (update)
   ```

---

## 文件查看命令及参数

- `cat` 由第一行开始显示文件内容
- `tac` 从最后一行开始显示
- `nl ` 显示的时候，顺道输出行号！
- `more` 一页一页的显示文件内容
- `less` 与 more 类似，但是比 more 更好的是，他可以往前翻页！
- `head` 只看头几行
- `tail` 只看尾巴几行

---

1. `cat`

   ```
   -A ：相当于 -vET 的整合选项，可列出一些特殊字符而不是空白而已；
   -b ：列出行号，仅针对非空白行做行号显示，空白行不标行号！
   -E ：将结尾的断行字节 $ 显示出来；
   -n ：列印出行号，连同空白行也会有行号，与 -b 的选项不同；
   -T ：将 [tab] 按键以 ^I 显示出来；
   -v ：列出一些看不出来的特殊字符
   ```

2. `tac` 与`cat`相反，参数相同

3. `nl`

   ```
   -b ：指定行号指定的方式，主要有两种：
   -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；
   -b t ：如果有空行，空的那一行不要列出行号(默认值)；
   -n ：列出行号表示的方法，主要有三种：
   -n ln ：行号在荧幕的最左方显示；
   -n rn ：行号在自己栏位的最右方显示，且不加 0 ；
   -n rz ：行号在自己栏位的最右方显示，且加 0 ；
   -w ：行号栏位的占用的位数。
   ```

4. `more`

   ```
   空格 (space)：代表向下翻一页；
   Enter         ：代表向下翻『一行』；
   /字串         ：代表在这个显示的内容当中，向下搜寻『字串』这个关键字；
   :f            ：立刻显示出档名以及目前显示的行数；
   q             ：代表立刻离开 more ，不再显示该文件内容。
   b 或 [ctrl]-b ：代表往回翻页，不过这动作只对文件有用，对管线无用。
   ```

5. `less`

   ```
   空格(space)：向下翻动一页；
   [pagedown]：向下翻动一页；
   [pageup]  ：向上翻动一页；
   /字串     ：向下搜寻『字串』的功能；
   ?字串     ：向上搜寻『字串』的功能；
   q         ：离开 less 这个程序；
   ```

6. `head` `tail`

   ```
   -n :显示的行数，默认10行
   ```

---

## Linux链接

Linux 链接分两种，一种被称为硬链接（Hard Link），另一种被称为符号链接（Symbolic Link）。默认情况下，`ln` 命令产生硬链接。

```
ln a b       # a与b产生硬链接
ln -s a c    # a与c产生符号链接
# 符号链接相当于Windows的快捷方式
# 硬链接为两个文件同时指向一个inode节点
```

