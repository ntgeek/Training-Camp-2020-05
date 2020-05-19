# Html5

* <head> 元素包含了所有的头部标签元素。在 <head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

  可以添加在头部区域的元素标签为: <title>, <style>, <meta>, <link>, <script>, <noscript> 和 <base>。
  
* Html样式实例：(style=“”定义文本样式)

  * background-color
  * font-family
  * color
  * font-size
  * text-align

* alt 属性用来为图像定义一串预备的可替换的文本。替换文本属性的值是用户定义的。

  ```
  <img src="boat.gif" alt="Big Boat">
  ```

* 无序列表<ul>

  ```
  <ul>
  <li>Coffee</li>
  <li>Milk</li>
  </ul>
  ```

* 有序列表 <ol>

  ```
  <ol>
  <li>Coffee</li>
  <li>Milk</li>
  </ol>
  ```

  

* HTML 链接是通过 <a> 标签进行定义

  * ```
    <a href="">This is a link</a>
    ```

* <html> 元素定义了整个 HTML 文档。元素内容是另一个 HTML 元素（body 元素）

* HTML 标签对大小写不敏感：<P> 等同于 <p>。许多网站都使用大写的 HTML 标签。

* **HTML 属性赋予元素意义和语境。****全局属性可用于任何 HTML 元素。**

* | [accesskey](https://www.w3school.com.cn/tags/att_standard_accesskey.asp) | 规定激活元素的快捷键。                                 |
  | ------------------------------------------------------------ | ------------------------------------------------------ |
  | [class](https://www.w3school.com.cn/tags/att_standard_class.asp) | 规定元素的一个或多个类名（引用样式表中的类）。         |
  | [contenteditable](https://www.w3school.com.cn/tags/att_global_contenteditable.asp) | 规定元素内容是否可编辑。                               |
  | [contextmenu](https://www.w3school.com.cn/tags/att_global_contextmenu.asp) | 规定元素的上下文菜单。上下文菜单在用户点击元素时显示。 |
  | [data-*](https://www.w3school.com.cn/tags/att_global_data.asp) | 用于存储页面或应用程序的私有定制数据。                 |
  | [dir](https://www.w3school.com.cn/tags/att_standard_dir.asp) | 规定元素中内容的文本方向。                             |
  | [draggable](https://www.w3school.com.cn/tags/att_global_draggable.asp) | 规定元素是否可拖动。                                   |
  | [dropzone](https://www.w3school.com.cn/tags/att_global_dropzone.asp) | 规定在拖动被拖动数据时是否进行复制、移动或链接。       |
  | [hidden](https://www.w3school.com.cn/tags/att_global_hidden.asp) | 规定元素仍未或不再相关。                               |
  | [id](https://www.w3school.com.cn/tags/att_standard_id.asp)   | 规定元素的唯一 id。                                    |
  | [lang](https://www.w3school.com.cn/tags/att_standard_lang.asp) | 规定元素内容的语言。                                   |
  | [spellcheck](https://www.w3school.com.cn/tags/att_global_spellcheck.asp) | 规定是否对元素进行拼写和语法检查。                     |
  | [style](https://www.w3school.com.cn/tags/att_standard_style.asp) | 规定元素的行内 CSS 样式。                              |
  | [tabindex](https://www.w3school.com.cn/tags/att_standard_tabindex.asp) | 规定元素的 tab 键次序。                                |
  | [title](https://www.w3school.com.cn/tags/att_standard_title.asp) | 规定有关元素的额外信息。                               |
  | [translate](https://www.w3school.com.cn/tags/att_global_translate.asp) | 规定是否应该翻译元素内容。                             |

* window时间事件属性

* | [onafterprint](https://www.w3school.com.cn/tags/event_onafterprint.asp) | script | 文档打印之后运行的脚本。                         |
  | ------------------------------------------------------------ | ------ | ------------------------------------------------ |
  | [onbeforeprint](https://www.w3school.com.cn/tags/event_onbeforeprint.asp) | script | 文档打印之前运行的脚本。                         |
  | onbeforeunload                                               | script | 文档卸载之前运行的脚本。                         |
  | onerror                                                      | script | 在错误发生时运行的脚本。                         |
  | onhaschange                                                  | script | 当文档已改变时运行的脚本。                       |
  | [onload](https://www.w3school.com.cn/tags/event_onload.asp)  | script | 页面结束加载之后触发。                           |
  | onmessage                                                    | script | 在消息被触发时运行的脚本。                       |
  | onoffline                                                    | script | 当文档离线时运行的脚本。                         |
  | ononline                                                     | script | 当文档上线时运行的脚本。                         |
  | onpagehide                                                   | script | 当窗口隐藏时运行的脚本。                         |
  | onpageshow                                                   | script | 当窗口成为可见时运行的脚本。                     |
  | onpopstate                                                   | script | 当窗口历史记录改变时运行的脚本。                 |
  | onredo                                                       | script | 当文档执行撤销（redo）时运行的脚本。             |
  | [onresize](https://www.w3school.com.cn/tags/event_onresize.asp) | script | 当浏览器窗口被调整大小时触发。                   |
  | onstorage                                                    | script | 在 Web Storage 区域更新后运行的脚本。            |
  | onundo                                                       | script | 在文档执行 undo 时运行的脚本。                   |
  | [onunload](https://www.w3school.com.cn/tags/event_onunload.asp) | script | 一旦页面已下载时触发（或者浏览器窗口已被关闭）。 |

* Form事件、Mouse事件、Media事件。[参考链接](https://www.w3school.com.cn/tags/html_ref_eventattributes.asp)

* [HTML 5 视频/音频参考手册](https://www.w3school.com.cn/tags/html_ref_audio_video_dom.asp)

* W3C 的 HTML 4.0 标准仅支持 16 种颜色名，它们是：aqua、black、blue、fuchsia、gray、green、lime、maroon、navy、olive、purple、red、silver、teal、white、yellow。如果使用其它颜色的话，就应该使用十六进制的颜色值。

* ```
  <video src="movie.ogg" controls="controls">
  </video>
  ```

  controls 属性供添加播放、暂停和音量控件。

* 如需在 HTML5 中播放音频

  ```
  <audio src="song.ogg" controls="controls">
  </audio>
  ```

* 什么是 Canvas？
  HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像。

  画布是一个矩形区域，您可以控制其每一像素。

  canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

* canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成：

* 什么是SVG？
  SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
  SVG 用于定义用于网络的基于矢量的图形
  SVG 使用 XML 格式定义图形
  SVG 图像在放大或改变尺寸的情况下其图形质量不会有损失
  SVG 是万维网联盟的标准

* 与其他图像格式相比（比如 JPEG 和 GIF），使用 SVG 的优势在于：

  SVG 图像可通过文本编辑器来创建和修改
  SVG 图像可被搜索、索引、脚本化或压缩
  SVG 是可伸缩的
  SVG 图像可在任何的分辨率下被高质量地打印
  SVG 可在图像质量不下降的情况下被放大

* HTML5 新的 Input 类型

  * email
    url
    number
    range
    Date pickers (date, month, week, time, datetime, datetime-local)
    search
    color

  * ```
    Homepage: <input type="url" name="user_url" />
    ```

  * ```
    <!DOCTYPE HTML>
    <html>
    <body>
    ​
    <form action="/example/html5/demo_form.asp" method="get">
    Date: <input type="date" name="user_date" />
    <input type="submit" />
    </form>
    ​
    </body>
    </html>
    ​
    ```

    