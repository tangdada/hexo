---
title: 写给后端的前端课
---

先上个结论，目前的Web前端体系就是：以HTML + CSS + JavaScript三项技术为基础而构建的图形界面交互系统。
HTML是文字，CSS是颜料，JavaScript是笔和橡皮。

接下来我将从起源、演进、实战、扩张四个部分来介绍这个体系。

# 一、起源
当我踏入世界的时候，它已经是一片花园了。可是这一切是怎么形成的呢？

追本溯源的有趣之处在于发现这个错综复杂，包罗万象，甚至被称为“宇宙”的系统，原来只是因为50多年前那只“蝴蝶”笨拙的煽动了一下翅膀。

## 1.1 万维网

冷战时期（1947—1991），美国国防部建设了一个军用网，叫做“阿帕网”（ARPAnet），阿帕网于1969年正式启用，这就是Internet（因特网）的前身。53年过去，现在它已发展成为一个基于TCP/IP协议，覆盖全球大部分国家的开放型全球计算机网络系统。

1990年，在因特网的基础上，欧洲粒子物理实验室（CERN）的Tim Berners-Lee和Robert Cailliau为了方便交流科学论文和数据，开发了超文本服务器程序，Tim Berners-Lee把他设计的超文本标记语言文件所构成的系统称为WWW（World Wide Web / Wan Wei Wang）。

![万维网层级.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1eb7da665fd64f6cbb489e86cc7797a4~tplv-k3u1fbpfcp-watermark.image?)

## 1.2 HTML

HTML全称为超文本标记语言（Hyper Text Markup Language），是一种标记语言。它包括一系列标签，通过这些标签可以将网络上的文档格式统一，使分散在Internet上的资源连接为一个逻辑整体。

在WWW的使用中，两项重要的创造发挥了关键的作用。这两项技术是 **超文本(hyper text)** 和 **图形用户界面(GUI)** 。超文本是一种组织信息的方式，它通过超级链接方法将文本中的文字、图表与其他信息媒体相关联。

其格式如下：
```html
<html>
	<head></head>
	<body>
		<h1>标题</h1>
		<p>段落</p>
	</body>
</html>
```

**浏览器**

1990年Tim Berners-Lee在发明HTML的同时也发明了世界上第一款浏览器Nexus。

浏览器是用来检索、展示以及传递Web信息资源的应用程序。它使用统一资源标识符( Uniform Resource Identifier，URI)来标记Web信息资源。通过浏览器的图形用户界面，可以把HTML文件以一种易读的方式展示出来。

1993年NCSA（美国国家超级电脑应用中心）推出了世界上第一款能显示图片的浏览器NCSAMosaic，它是后来IE浏览器的基础，成为了点燃因特网热潮的火种之一。后来这款浏览器的核心开发者成立了网景公司（Netscape），又开发了网景导航者浏览器（Netscape Navigator）以替代NCSAMosaic，之后Netscape Navigator与IE浏览器在市场上分庭抗礼。

同时前端最常用的开发语言 **JavaScript** 也于1995年在Netscape Navigator上首次设计实现，由Netscape公司的Brendan Eich发明，他后来是火狐浏览器的联合创始人。

如今，最流行的浏览器是Google Chrome，它基于开源的浏览器引擎WebKit开发（2008）。

## 1.3 JavaScript

1995 年，当时就职于网景公司的 Brendan Eich 迫于公司的压力，只花了十天就设计了 JS 的最初版本，并命名为 Mocha。后来Netscape与Sun合作，改名为JavaScript。JavaScript是一种解释型的脚本语言，C、C++等语言是先编译后执行，而JavaScript是在程序的运行过程中逐行进行解释。

完整的JavaScript实现包含三个部分：ECMAScript，文档对象模型（DOM），浏览器对象模型（BOM）。打开chrome控制台，即可编写JS代码：
```js
document.body.style.background = 'red';
```

## 1.4 CSS

层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML或XML等文件样式的计算机语言。1994年由哈坤·利提出了CSS的最初建议。1996年底，CSS初稿已经完成，同年12月，层叠样式表的第一份正式标准（Cascading style Sheets Level 1）完成，成为W3C的推荐标准。其代码格式如下：
```css
span {
    display: inline-block;
    width: 100px;
    height: 48px;
    line-height: 48px;
    font-size: 28px;
    color: #fff;
    text-align: center;
    cursor: pointer;
}
```

到此，以HTML为骨架，CSS为外表，JavaScript作为控制，Web前端的3大重量级嘉宾就出场完毕了。

![Web前端体系基础.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/65b160c45c5942e2a541a4374503c8d2~tplv-k3u1fbpfcp-watermark.image?)

浏览器页面的渲染流程如下：

![浏览器页面的渲染机制.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be3e01b9148340c9afe3236db1e40c28~tplv-k3u1fbpfcp-watermark.image?)

那么之后，从1990年开始发展到现在如此丰富的Web前端世界，其间经历了哪些阶段呢？

# 二、演进

## 2.1 只有一种程序员
这个阶段还没有Web前端这个细分工种，开发者以使用的后端语言来划分，比如说做Java的，做C++的。

### 静态页
静态页的阶段不长，自1990年HTML发明开始至1994年W3C成立，之后很快就出现了动态开发HTML的语言。

世界上第一个Web网页（被恢复的副本）：http://info.cern.ch/ ，其代码如下：
```html
<html>
    <head></head>
    <body>
        <header>
            <title>http://info.cern.ch</title>
        </header>

        <h1>http://info.cern.ch - home of the first website</h1>
        <p>From here you can:</p>
        <ul>
            <li><a href="http://info.cern.ch/hypertext/WWW/TheProject.html">Browse the first website</a></li>
            <li><a href="http://line-mode.cern.ch/www/hypertext/WWW/TheProject.html">Browse the first website using the line-mode browser simulator</a></li>
            <li><a href="http://home.web.cern.ch/topics/birth-web">Learn about the birth of the web</a></li>
            <li><a href="http://home.web.cern.ch/about">Learn about CERN, the physics laboratory where the web was born</a></li>
        </ul>
    </body>
</html>
```
可以想像如果按这样的方式把大量的内容转移到网络上，是多么笨拙和费力的事情。那么为了实现**数据的灵活拼装**、**动态加载数据库中的数据** 和 **增加用户交互** ，就出现了动态页面。

### 动态页
这是后端写Web页面的时代，运行在服务端用于编写动态页面的语言包括PHP、ASP、JSP。这一部分如果勾起了你的回忆，你可能暴露年龄了。

#### PHP
1994年由Rasmus Lerdorf 创建的开源项目：Personal Home Page，后正式更名为：PHP: Hypertext Preprocessor，即“超文本预处理器”，是在服务器端执行的脚本语言，尤其适用于Web开发并可嵌入HTML中。

根据W3Techs2019年12月6号发布的统计数据，PHP在WEB网站服务器端使用的编程语言所占份额高达78.9%。在内容管理系统的网站中，有58.7%的网站使用WordPress（PHP开发的CMS系统），这占所有网站的25.0%。

*开始使用：*\
下载一个[XAMPP](https://blog.csdn.net/weixin_42516074/article/details/115993042)，通过它启动一个本地的Apache服务，新增一个.php后缀的文件，即可编写一个简单的helloworld程序。页面代码如下：
```php
<!DOCTYPE html>
<html>
<body>

<?php
echo "Hello World 大清！";
?>

</body>
</html>
```

![phpdemo.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bd9cc9bbbe704590beabc7643ac70bb9~tplv-k3u1fbpfcp-watermark.image?)

#### ASP
1996年微软推出的ASP（Active Server Pages/动态服务器页面）简单、易于维护 ， 是小型页面应用程序的选择。2002推出的ASP.NET，ASP.NET 是一个免费的 Web 开发框架，用于通过 HTML、CSS、JavaScript 以及服务器脚本来构建网页和网站，它通过 **IIS** （Internet Information Server，基于Windows的互联网信息服务）解析执行后可以得到动态页面。

*开始使用：*\
安装[.net SDK](https://docs.microsoft.com/zh-cn/aspnet/core/getting-started/?view=aspnetcore-6.0&tabs=windows)，安装完成后，根据命令新建一个ASP.NET Web应用。
```sh
dotnet new webapp -o aspnetcoreapp
cd aspnetcoreapp
dotnet watch run
```

修改项目中Pages文件下Index.cshtml文件，代码如下：

```java
@page
@model IndexModel
@{
    ViewData["Title"] = "Home page";
}

<div class="text-start">
    <h1 class="display-4">Welcome 大清</h1>
    <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
</div>
```
![asp.net.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d99e5f4d152c4a81a6f990848b04602c~tplv-k3u1fbpfcp-watermark.image?)

#### JSP

1997年Servlet技术的产生以及紧接着JSP的产生，为Java对抗PHP、ASP等服务器端语言带来了筹码。JSP将Java代码和特定变动内容嵌入到静态的页面中，实现以静态页面为模板，动态生成其中的部分内容。2003年11月24日发布了J2EE（Java 2 平台企业版）1.4， 该版本中包含了JSP2.0，JSP 2.0支持表达语言(expression language)。

*开始使用：*\
安装java开发环境 JDK，配置JAVA_HOME环境变量，安装Tomcat 服务器（配置环境变量CATALINA_HOME为tomcat安装目录），在`tomcat安装目录\webapps\ROOT`下添加 test.jsp。

下面是使用java代码实现的日期格式化和99乘法表，代码如下：
```jsp
<%@ page language="java" contentType="text/html; charset=utf-8"%>
<%@ page import="java.io.*,java.util.*" %>
<%@ page import="javax.servlet.*,java.text.*" %>

<html>
    <head>
        <title>JSP页面</title>
    </head>
    <body>
        <%!
	String nineTable() {
            StringBuilder builder = new StringBuilder();
            for(int i=1;i<=9;i++){
                for(int j=1;j<=i;j++){
                    builder.append(i + "*" + j + "=" + i*j + "&nbsp;&nbsp;&nbsp;&nbsp;");
                }
                builder.append("<br/>");
            }
            return builder.toString();
        }
        %>
	<%
            Date dNow = new Date( );
            SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd HH:mm:ss");
	%>
	<div style="padding-left: 40px;">
            <p>Hello 大清！现在时间是：<%= ft.format(dNow) %></p>
            <p>
                <% 
                    String sum1;
                    sum1=nineTable();
                    out.print(sum1);
		%>
            </p>
	</div>
    </body>
</html>
```

![jspdemo.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/109075ec427b447cb0eed9b51ffeca04~tplv-k3u1fbpfcp-watermark.image?)

在这个阶段前端和后端还没有清晰的界限，那么我们所说的前后端分离出现在什么时候呢？

## 2.2 前后端分离

我们可以参考下国内什么时候出现前端开发的职位。我在百度上以前端和招聘两个关键字搜索到最早的 [前端招聘信息](https://www.cnblogs.com/andywu/articles/1187276.html) 在2008年左右。

当时对于Web前端开发的职位要求：
> 1.熟悉 ActionScript 面向对象的编程，能独立完成 Flash 前台脚本及后台动作实现互动功能编程；
> 
> 2.熟悉 Flash 与ASP.NET之间的数据传递；
> 
> 3.熟悉javascript，能够应用第三方的开源js库，比如prototype，jquery等；
>
> 4.有三年以上相关工作经验；
>
> 5.具有高超的艺术修养，美术或设计专业大专以上学历，有良好的美术功底和优秀的创意、实现能力；
>
> 6.熟练使用设计及网页制作工具，如photoshop、fireworks、dreamweaver、flash等，有良好的设计能力并具备熟练网页制作技巧，熟悉HTML/css/javascript等并能熟练手工编辑修改HTML源代码，能熟练美化ASP/PHP/JSP等程序动态页面；
> 
> 7.熟悉网站建设的流程和网页设计制作流程，能独立完成大、中型网站页面设计，有成功的网页设计案例；
>
> 8.热爱网站工作，喜欢从事网站设计、策划、制作；
>
> 9.具有高深的flash制作功底者优先考虑；
>
> 10.对dhtml，javascript，xml等有充分的了解，能熟练使用javascript进行客户端编程。

[2010年各大厂招聘前端开发的职位描述](http://uicss.cn/fed-position-descriptions/)，包括阿里、腾讯、网易等。可以大概看出当时对于前端的定义和技能要求：\
这段时期属于一个承上启下的阶段，要会使用ASP/PHP/JSP等动态语言，也要会使用js库（jQuery），甚至还要会使用Photoshop和通过ActionScript制作Flash动画。

我认为职责的分离还是为了业务的需要，一方面用户产生了日益增长的对交互体验提升的需要，另一方面后端产生了日益增长的业务量压力的技术需要，前后端分离后，各自专注于解决不同的业务痛点。

对于前端来说这段时期有2项技术举足轻重，分别是jQuery和Ajax，jQuery可以让开发者可以专注于前端交互，Ajax可以高效的与后端进行数据通信。

### jQuery
2006年1月由John Resig发布的jQuery是一个快速、简洁的JavaScript框架，它的设计宗旨是：Write Less，Do More。jQuery是一个里程碑，它易于上手，使得开发者可以更加语义化的编写前端交互逻辑，在此之后的10年里一直占据着前端开发框架的统治地位。

### Ajax
2005年Jesse James Garrett提出了Ajax（Asynchronous Javascript And XML），它是一种Web数据交互方式。Ajax 在浏览器与 Web 服务器之间使用XMLHttpRequest对象进行异步数据传输（HTTP 请求）。使用Ajax的最大优点，就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户操作，并避免了在网络上传输那些没有改变的额外信息。


*开始使用：*
```js
<!DOCTYPE html>
<html>
    <head>
        <!-- 直接使用网络上的jQuery包，也可以下载jQuery包到本地 -->
        <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
        <script type="text/javascript">
            // 这里使用 Vercel 部署了一个网易云音乐的接口服务 https://netease-cloud-music-api-ruby-mu.vercel.app
            var apiServer = 'https://netease-cloud-music-api-ruby-mu.vercel.app'
            $(document).ready(function () {
                // 页面事件：点击搜索按钮
                $('#search-btn').on('click', function () {
                    handleSearchSong()
                })

                // 页面事件：输入框敲击回车
                $('#search-ipt').on('keyup', function (e) {
                    if (e.keyCode === 13) {
                        handleSearchSong()
                    }
                })

                // 从后端查询数据 并 显示在页面
                function handleSearchSong() {
                    var keyword = $('#search-ipt').val()
                    if (!keyword) return
                    $.get(`${apiServer}/search?keywords=${keyword}`, function (data, status) {
                        var songList = data.result.songs
                        addSongToPanel(songList)
                    })
                }

                // 显示歌曲列表到页面上
                function addSongToPanel(songList) {
                    $('#song-list').empty()
                    songList.forEach((item) => {
                        var imgStl = 'style="display: inline-block;width: 40px;height: 40px;margin-right: 20px;"'
                        var diabled = item.fee === 1 ? '' : 'disabled' // 是否有权限播放
                        $('#song-list').append(
                            `<div><img ${imgStl} src=${item.artists[0].img1v1Url} /><span>${item.name}</span><span>歌手：${item.artists[0].name}</span><button id=${item.id} ${diabled} class="play-btn">播放</button></div>`
                        )
                    })
                }

                // 页面事件：点击播放按钮
                $('#song-list').on('click', '.play-btn', function (e) {
                    var id = e.target.id
                    $.get(`${apiServer}/song/url?id=${id}`, function (data, status) {
                        var audioUrl = (data.data[0] || {}).url
                        console.log('audioUrl', audioUrl)
                        if (audioUrl) {
                            $('#song-player').empty()
                            $('#song-player').append(`
                            <audio controls>
                            <source src=${audioUrl} type="audio/ogg">
                            您的浏览器不支持 audio 元素。
                            </audio>
                            `)
                        }
                    })
                })
            })
        </script>
    </head>
    <body>
        <div class="page">
            <div class="header">
                <input id="search-ipt" type="text" placeholder="请输入关键字搜索歌曲" />
                <button id="search-btn">搜索</button>
            </div>

            <div class="body">
                <div id="song-list"></div>
                <div id="song-player"></div>
            </div>
        </div>
    </body>
</html>
```

![jquery.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bbf3a0b580cd403daea7f0000c35dd33~tplv-k3u1fbpfcp-watermark.image?)

加入一点简单的css样式，在`<head>...</head>`中加上如下style标签：

```css
<style type="text/css">
            button {
                border: none;
                cursor: pointer;
            }
            .page {
                width: 400px;
            }
            .page .header {
                display: flex;
                justify-content: space-around;
                background: rgb(210, 0, 1);
                padding: 12px;
            }
            .page .header #search-ipt {
                flex: 1;
                border: none;
            }
            .page .header #search-btn {
                border: none;
            }
            .body {
                position: relative;
            }
            #song-list {
                height: 600px;
                overflow-y: auto;
            }
            #song-list > div {
                height: 60px;
                display: flex;
                align-items: center;
                padding: 0 12px;
                background: rgb(243, 244, 246);
                border-bottom: 1px solid rgb(223, 224, 226);
            }
            #song-list > div > span {
                width: 130px;
                display: inline-block;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
            }
            .body #song-player {
                position: absolute;
                text-align: center;
                width: 100%;
                bottom: 0;
                left: 0;
                background: rgba(255, 255, 255, 0.6);
            }
</style>
```

![jq_ajax.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/81d58e719ad74ada97c56ad0bb0ac79c~tplv-k3u1fbpfcp-watermark.image?)

*说明：*\
这里需要利用 [Node.js](http://nodejs.cn/) 启动一个http服务，Node.js安装完成之后在项目根目录下命令行执行：\
`npm install http-server -g`\
然后执行：
`http-server`，项目就运行起来啦。

## 2.3 工程化框架和构建生态

主要指 MVC和MVVM开发框架。

目前Web前端岗位主流市场正处于这个阶段，也可以说是这个阶段如日中天的时候。最大的特点是开发框架从开发者手中接管了对DOM操作（DOM节点的CRUD）的工作，并且还进行了优化，开发者的精力可以更加倾注于业务逻辑的编写。

MVC由模型M、视图V、控制器C组成；MVVM由模型M、视图V、视图模型VM组成，类似于Java的springMVC，其中比较有代表性的有3个框架：

| 名称| 类型 | 维护者 | 时间 | 开源 |衍生框架| 关注度|
| --- | --- |---|---|---|---|---|
| Angular | MVVM |Google| 2009|开源|不详| <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/15051993d0934d3892bfdce8bc919240~tplv-k3u1fbpfcp-zoom-1.image" /> |
| React | MVC |Facebook| 2013|开源|Next.js / RN| <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f78b1a521c5341fe9dbd079f499f6ecf~tplv-k3u1fbpfcp-zoom-1.image" /> |
| Vue | MVVM |尤雨溪| 2014|开源|Nuxt.js / uni-app| <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d48400515153438584608419d9a51bc2~tplv-k3u1fbpfcp-zoom-1.image" /> |

与开发框架齐头并进的，还有一个庞大的前端构建生态。开发中节省下来的复杂度需要由构建工具来承担。

React 官方文档中对构建生态的概括非常准确，一组 JavaScript 构建工具链通常由这些组成：

>一个 package 管理器，比如 Yarn 或 npm。它能让你充分利用庞大的第三方 package 的生态系统，并且轻松地安装或更新它们。
>
>一个打包器，比如 webpack 或 Parcel。它能让你编写模块化代码，并将它们组合在一起成为小的 package，以优化加载时间。
>
>一个编译器，例如 Babel。它能让你编写的新版本 JavaScript 代码，在旧版浏览器中依然能够工作。

![构建流程.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/04ff16d98d354e2d95e1bb06122836ca~tplv-k3u1fbpfcp-watermark.image?)

### React

下面我们用React来重写上面的音乐播放页。

*开始使用：*\
根据 [React官方](https://zh-hans.reactjs.org/) 提供的脚手架生成一个新项目。这个例子使用的是React 17版本，目前React已经更新到18了。前端框架的更迭真可谓是日新月异啊。

Node.js 版本要求： Node >= 14.0.0 和 npm >= 5.6，实际上我们唯一需要依赖的环境就只有Node.js，你可以非常轻松的安装到你的电脑上。

#### 初始化项目

```sh
npx create-react-app my-app
cd my-app
npm run start
```

#### 编写页面
将App.js文件后缀改为 `.jsx`，jsx 同时兼容 html 和 js 写法的模板文件，`npm i axios --save`下载一个依赖库。

修改App.jsx文件，内容如下：
```jsx
import React from 'react'
import axios from 'axios'
import './App.css'

const apiServer = 'https://netease-cloud-music-api-ruby-mu.vercel.app'
export default class App extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            keyword: '',
            songList: [],
            audioUrl: '',
        }
    }
    handleSearch() {
        if (!this.state.keyword) return
        axios.get(`${apiServer}/search?keywords=${this.state.keyword}`).then((res) => {
            this.setState({ songList: res.data.result.songs })
        })
    }
    play(id) {
        axios.get(`${apiServer}/song/url?id=${id}`).then((res) => {
            this.setState({ audioUrl: (res.data.data[0] || {}).url })
        })
    }
    handleKeyUp(e) {
        if (e.keyCode === 13) {
            this.handleSearch()
        }
    }
    handleInput(e) {
        this.setState({ keyword: e.target.value })
    }
    handleClick(letter) {
        this.setState({ justClicked: letter })
    }
    render() {
        return (
            <div id="counter" className="page">
                <div className="header">
                    <input
                        id="search-ipt"
                        type="text"
                        placeholder="请输入关键字搜索歌曲"
                        onChange={(e) => {
                            this.handleInput(e)
                        }}
                        onKeyUp={(e) => {
                            this.handleKeyUp(e)
                        }}
                    />
                    <button
                        id="search-btn"
                        onClick={() => {
                            this.handleSearch()
                        }}
                    >
                        搜索
                    </button>
                </div>
                <div className="body">
                    <div id="song-list">
                        {this.state.songList.map((song) => (
                            <div key={song.id}>
                                <img
                                    style={{ display: 'inline-block', width: '40px', height: '40px', marginRight: '20px' }}
                                    src={song.artists[0].img1v1Url}
                                    alt=""
                                />
                                <span>{song.name}</span>
                                <span>歌手：{song.artists[0].name}</span>
                                <button
                                    id="{song.id}"
                                    disabled={song.fee !== 1}
                                    className="play-btn"
                                    onClick={() => {
                                        this.play(song.id)
                                    }}
                                >
                                    播放
                                </button>
                            </div>
                        ))}
                    </div>
                    <div id="song-player">
                        {this.state.audioUrl && (
                            <audio controls>
                                <source src="{audioUrl}" type="audio/ogg" />
                                您的浏览器不支持 audio 元素。
                            </audio>
                        )}
                    </div>
                </div>
            </div>
        )
    }
}
```
对比jQuery的例子可以发现，DOM的`empty()`、`append()`等操作没有了，取而代之的是`setState()`方法。也就是我们只需要控制数据就可以实现页面的变更了，不再需要对具体的DOM节点进行增删改。

最后，将之前一个例子中的CSS样式代码拷贝到App.css中即可。

当然这只是一个学习的例子，完整的项目还需要更加工程化的结构，下面我们来搭建一个相对完善的前端系统。

# 三、实战

前端的前辈们在上面各种开发框架的基础上又叠加出更加全面的生态，我们可以方便的使用脚手架快速的搭建起一个标准的项目。在这里我们需要一个包管理工具 `npm` ，它类似于Java生态中的Maven，npm会随着Node.js的安装顺带一起安装到你的电脑上。你可以在命令行通过 `npm -v` 查看版本信息。

目前跟React比较，[Vue.js](https://v3.cn.vuejs.org/) 提供了更加集成化的搭建项目的脚手架。这里我们使用[vue-cli](https://cli.vuejs.org/zh/guide/)，来搭建一个《上下班调研系统》。

它是一个 **SPA（单页面应用）**，即所有前端页面资源会一次性加载到客户端；与之对应的是多页应用，即每次只返回多个页面之中被请求的子页面资源（Js、HTML、CSS）。

Node.js环境和vue-cli版本：`@vue/cli 4.5.12`，Vue CLI 4.x 需要 `Node.js >= v8.9`。\
下载脚手架：`npm install -g @vue/cli`

## 3.1 初始化项目
命令行执行：`vue create working-hours`

选项配置：

![vue-cli-option.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/65d19ab62c6d40b5a1ceb4bd2b4146af~tplv-k3u1fbpfcp-watermark.image?)

在项目根目录下打开命令行，执行 `npm run serve`，浏览器打开控制台显示的地址，就可以看到项目初始的页面了。

## 3.2 修改首页
修改文件App.vue和Home.vue，同时添加页面入口。

*App.vue代码如下：*
```js
<template>
    <div id="app">
        <router-view></router-view>
    </div>
</template>

<style lang="less">
html,
body,
#app {
    height: 100%;
    margin: 0;
}
</style>
```

*Home.vue代码如下：*
```js
<template>
    <div class="entry">
        <router-link to="/working-hours">下班了吗？</router-link>
    </div>
</template>

<style lang="less">
.entry {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    & > a {
        font-size: 48px;
        font-weight: bold;
        background-image: linear-gradient(90deg, #007cf0, #ff7875);
        background-clip: text;
        color: transparent;
        letter-spacing: 8px;
    }
}
</style>
```

## 3.3 添加子页面

在项目的views文件夹下新建3个页面，分别是 `WorkingHours.vue`、`Record.vue`、`Statistics.vue`：

*WorkingHours.vue代码如下：*
```js
<template>
    <div>
        <div class="menu">
            <router-link to="/">首页</router-link>
            <router-link to="/working-hours/record">上报数据</router-link>
            <router-link to="/working-hours/statistics">统计</router-link>
        </div>
        <div class="body">
            <router-view />
        </div>
    </div>
</template>
<style lang="less">
.menu {
    padding: 16px;
    border-bottom: 1px solid #eee;
    a {
        font-weight: bold;
        color: #2c3e50;
        margin-right: 16px;
        &.router-link-exact-active {
            color: #42b983;
        }
    }
}
.body {
    padding: 16px;
}
</style>
```

*Record.vue代码如下：*
```html
<template>
    <div>page record.</div>
</template>
```

*Statistics.vue代码如下：*
```html
<template>
    <div>page statistics.</div>
</template>
```

## 3.4 添加路由
也就是声明浏览器输入的链接地址和页面文件之间的匹配关系。

修改 router/index.js 如下：
```js
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)

const routes = [
    {
        path: '/',
        name: 'Home',
        component: () => import('../views/Home.vue'),
    },
    {
        path: '/working-hours',
        name: 'WorkingHours',
        component: () => import('../views/WorkingHours.vue'),
        redirect: '/working-hours/record',
        children: [
            {
                path: 'record',
                name: 'Record',
                component: () => import('../views/Record.vue'),
            },
            {
                path: 'statistics',
                name: 'Statistics',
                component: () => import('../views/Statistics.vue'),
            },
        ],
    },
]

const router = new VueRouter({
    routes,
})

export default router
```
这时我们点击“上报数据”和“统计”两个超链接，可以看到路由切换的效果。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/720e113415f34462843ba3aa29e51ee5~tplv-k3u1fbpfcp-watermark.image?)

## 3.5 添加业务代码
为了更加快速的实现业务功能，我们可以引入生态中开源的UI组件库，组件库中包含了按钮、表格、表单等常用基础组件。

组件库在前端开发生态中位置：
![前端体系层级.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/44b2f2fb406947d4aba23fb159521c56~tplv-k3u1fbpfcp-watermark.image?)

这里我们使用饿了么的组件库[element-ui@2.15.7](https://element.eleme.cn/#/zh-CN/component/installation)，在项目根目录下运行如下命令，下载组件库代码包：
`npm i element-ui -S`。

修改 main.js 引入组件库，内容如下：
```js
import Vue from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'

// 全局引入饿了么组件库 
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(ElementUI);

Vue.config.productionTip = false

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount('#app')
```

修改“上报数据”页面Record.vue，代码如下：\
首先下载一个用于发起http请求的js库axios：`npm i axios --save`
```js
<template>
    <div>
        <div class="btn-wrap">
            <el-button type="primary" size="small" @click="handleAdd">上报</el-button>
        </div>
        <div class="table-wrap">
            <el-table v-loading="loading" :data="tableData" style="width: 100%" stripe>
                <el-table-column prop="startTime" label="上班时间"> </el-table-column>
                <el-table-column prop="endTime" label="下班时间"> </el-table-column>
                <el-table-column prop="job" label="职业"> </el-table-column>
                <el-table-column prop="company" label="公司" show-overflow-tooltip> </el-table-column>
                <el-table-column prop="gender" label="性别"> </el-table-column>
                <el-table-column prop="age" label="年龄段"> </el-table-column>
                <el-table-column prop="remark" label="备注" show-overflow-tooltip> </el-table-column>
                <el-table-column fixed="right" label="操作" width="120">
                    <template slot-scope="scope" v-if="scope.row.isSelf">
                        <el-button type="text" size="small" @click="handleEdit(scope.row)">编辑</el-button>
                        <el-button type="text" size="small" @click="handleDel(scope.row)">删除</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </div>
        <div class="page-wrap">
            <el-pagination layout="prev, pager, next" background :total="page.total" @current-change="handlePageChg"> </el-pagination>
        </div>

        <el-dialog :title="ruleForm.id ? '修改' : '新增'" :close-on-click-modal="false" :visible.sync="dialogVisible" width="600px" :before-close="handleClose">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px">
                <el-form-item label="上班时间" prop="startTime">
                    <el-time-select v-model="ruleForm.startTime" :picker-options="{ ...pickerOption, maxTime: ruleForm.endTime }"> </el-time-select>
                </el-form-item>
                <el-form-item label="下班时间" prop="endTime">
                    <el-time-select v-model="ruleForm.endTime" :picker-options="{ ...pickerOption, minTime: ruleForm.startTime }"> </el-time-select>
                </el-form-item>
                <el-form-item label="职业" prop="job">
                    <el-select v-model="ruleForm.job" placeholder="请选择职业">
                        <el-option v-for="item in jobList" :key="item" :label="item" :value="item"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="公司" prop="company">
                    <el-input :maxlength="16" v-model="ruleForm.company" placeholder="16个字以内"></el-input>
                </el-form-item>
                <el-form-item label="性别" prop="gender">
                    <el-select v-model="ruleForm.gender">
                        <el-option label="男" value="男"></el-option>
                        <el-option label="女" value="女"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="年龄段" prop="age">
                    <el-select v-model="ruleForm.age">
                        <el-option label="00后" value="00后"></el-option>
                        <el-option label="90后" value="90后"></el-option>
                        <el-option label="80后" value="80后"></el-option>
                        <el-option label="70后" value="70后"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="备注" prop="remark">
                    <el-input type="textarea" :maxlength="140" v-model="ruleForm.remark" placeholder="140个字以内"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('ruleForm')" :loading="saveLoading">确定</el-button>
                    <el-button @click="dialogVisible = false">取消</el-button>
                </el-form-item>
            </el-form>
        </el-dialog>
    </div>
</template>

<script>
import axios from 'axios'

const serverApi = 'https://vercel-egg.vercel.app/api' // 后端服务地址
const defaultForm = {
    id: '',
    startTime: '',
    endTime: '',
    job: '',
    company: '',
    gender: '',
    age: '',
    remark: '',
}
export default {
    data() {
        return {
            tableData: [],
            loading: false,
            saveLoading: false,
            page: {
                pageSize: 10,
                currentPage: 1,
                total: 0,
            },
            dialogVisible: false,
            pickerOption: {
                start: '00:00',
                step: '00:30',
                end: '24:00',
            },
            ruleForm: Object.assign({}, defaultForm),
            rules: {
                startTime: [{ required: true, message: '请输入上班时间', trigger: 'blur' }],
                endTime: [{ required: true, message: '请输入下班时间', trigger: 'blur' }],
                gender: [{ required: true, message: '请选择性别', trigger: 'blur' }],
                company: [{ max: 16, message: '公司名称不能超过16个字', trigger: 'blur' }],
                remark: [{ max: 140, message: '备注不能超过140个字', trigger: 'blur' }],
            },
            jobList: ['IT互联网技术', '电子/通信/半导体技术', '产品', '设计', '运营', '市场', '人事/行政/法务', '财务', '高级管理', '金融', '销售', '传媒'],
        }
    },
    methods: {
        getRecord() {
            this.loading = true
            axios
                .get(`${serverApi}/workingHour/retrieve?pageNo=${this.page.currentPage}`)
                .then((res) => {
                    this.tableData = res.data.list
                    this.page.total = res.data.page.total
                })
                .finally(() => {
                    this.loading = false
                })
        },
        handlePageChg(cpage) {
            this.page.currentPage = cpage
            this.getRecord()
        },
        handleAdd() {
            this.ruleForm = Object.assign({}, defaultForm)
            this.dialogVisible = true
        },
        handleClose() {
            this.dialogVisible = false
        },
        submitForm(formName) {
            this.$refs[formName].validate((valid) => {
                if (valid) {
                    this.saveRecord()
                } else {
                    return false
                }
            })
        },
        saveRecord() {
            this.saveLoading = true
            const createOrUpdate = this.ruleForm.id ? 'update' : 'create'
            axios
                .get(`${serverApi}/workingHour/${createOrUpdate}`, { params: this.ruleForm })
                .then(() => {
                    this.$message.success('保存成功')
                    this.dialogVisible = false
                    this.getRecord()
                })
                .catch((err) => {
                    this.$message.warning(err?.response?.data)
                })
                .finally(() => {
                    this.saveLoading = false
                })
        },
        resetForm(formName) {
            this.$refs[formName].resetFields()
        },
        handleEdit(row) {
            this.ruleForm = Object.assign({}, row)
            this.dialogVisible = true
        },
        handleDel(row) {
            this.$confirm('确认删除吗？', '提示').then(() => {
                axios
                    .get(`${serverApi}/workingHour/delete?id=${row.id}`)
                    .then(() => {
                        this.$message.success('删除成功')
                        this.getRecord()
                    })
                    .catch((err) => {
                        this.$message.warning(err?.response?.data)
                    })
            })
        },
    },
    created() {
        this.getRecord()
    },
}
</script>
<style lang="less" scoped>
.btn-wrap {
    text-align: right;
    border-bottom: 1px solid #eee;
    padding-bottom: 16px;
}
.page-wrap {
    padding-top: 12px;
    text-align: right;
}
</style>
```

修改“统计”页面Statistics.vue，代码如下：\
首先下载一个用于实现图表的js库echarts：`npm install echarts@5.3.2 --save`
```js
<template>
    <div class="container" id="chart-box1" v-loading="loading"></div>
</template>

<script>
import axios from 'axios'
import * as echarts from 'echarts'

const serverApi = 'https://vercel-egg.vercel.app/api' // 后端服务地址
export default {
    data() {
        return {
            loading: false,
        }
    },
    methods: {
        async getPieData() {
            this.loading = true
            const res = await axios.get(`${serverApi}/workingHour/pie`)
            this.loading = false
            let seriesData = []
            for (let key in res.data) {
                seriesData.push({
                    name: key,
                    value: res.data[key],
                })
            }
            this.renderChart(seriesData)
        },
        renderChart(seriesData) {
            let myChart = echarts.init(document.getElementById('chart-box1'))

            myChart.setOption({
                title: {
                    text: '下班时间统计',
                    left: 'center',
                },
                legend: {
                    top: 'bottom',
                },
                series: [
                    {
                        name: 'Nightingale Chart',
                        type: 'pie',
                        radius: [50, 170],
                        center: ['50%', '50%'],
                        roseType: 'area',
                        itemStyle: {
                            borderRadius: 8,
                        },
                        label: {
                            show: true,
                            formatter: '{b}\n{d}%',
                        },
                        data: seriesData,
                    },
                ],
            })
        },
    },
    mounted() {
        this.getPieData()
    },
}
</script>

<style lang="less" scoped>
.container {
    width: 500px;
    height: 500px;
}
</style>
```
这样，一个简单的应用就编码完成了。\
接下来可以命令行运行`npm run build`，把代码编译、压缩成静态文件（根目录下会多出一个dist文件夹），那么怎么把这个页面部署到公网环境，让其他人可以访问到呢？

>说明：上面代码中用到的后端服务，通过 Node.js + [mongoDB](https://cloud.mongodb.com/) 实现，并通过 [Vercel](vercel.com) 发布到公网。

## 3.6 发布到公共网络
将项目部署到公共网络，有以下4种方式。

### 云服务器
如果你是商用，复杂，定制的应用服务，最好还是花钱买一个服务器。云服务器厂商包括：Azure、AWS、阿里云、腾讯云、华为云等。在拥有一台服务器后，就可以开始部署了，用于部署服务的Web 应用服务器包括：Tomcat、Nginx、IIS（Windows）等。\
这里以`nginx`为例：
- 安装nginx，网上有很多在线、离线安装的教程
- 配置服务入口\
        首先上传上面项目中打包生成的dist文件夹到服务器上，比如上传到服务器上的这个位置：`/opt/web/dist`，然后根据你安装的nginx目录，找到nginx服务配置文件，比如：`/usr/local/nginx/conf/nginx.conf`，在文件http{...}代码块内加入如下代码：
        
        server {
            listen       8081;
            server_name  localhost;
            location / {
                root   /opt/web/dist;
                index  index.html;
            }
        }
    保存后，重启nginx：`/usr/local/nginx/sbin/nginx -s reload`。
- 开放端口（防火墙）\
    云服务器提供商一般有配置页面可以直接操作。![开放端口.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/07a0b2642fc64a759a893ed72f89adf3~tplv-k3u1fbpfcp-watermark.image?)

这样就可以通过IP:8081访问你的页面了，当然完善的流程后面还有域名申请，域名绑定IP，网站ICP备案，https认证（SSL证书）等

### 第三方平台托管
在web1.0的时代，Web服务几乎是广播式的。那个blog盛行的年代，大家通过个人主页来发布信息，展示自我。\
第三方托管平台有`Github`、`Gitee`、`WordPress`等。Github 提供了 GitHub Pages服务来发布博客页，国内的Gitee类似。这些服务通常还会推荐你使用一些博客模板来生成内容，比如`WorkPress`、`Hexo`等。\
根据W3Techs2019年12月6号发布的统计数据，使用WordPress（PHP语言）开发的网站占所有网站的1/4。我这里使用 [Hexo](https://hexo.io/zh-cn/) 及它衍生的 hexo-theme-next 主题，半小时即可完成一个博客站点：https://hexo-one-dun.vercel.app/ 。

### Serverless 提供商
Serverless平台包括：小程序平台、Vercel等。\
上面《上下班调研系统》就通过Vercel部署到了公网，访问地址：https://working-hours-tau.vercel.app/ 。

### CDN服务提供商
可以通过七牛云、阿里云OSS、腾讯云OSS等进行静态页面托管，只需要给文件资源地址绑定一个域名即可。

# 四、扩张
随着数字化进程的开展，政府和企业侧需求激增，带来很多的前端就业岗位。再加上Web前端行业的从业门槛不高、终端设备的普遍支持、开发生态的完善等原因，涌现出很多的前端开发人员，前端代码也像苔藓般蔓延到更多的领域。\
如果Web前端向自动化、智能化发展的话，还是需要高精尖的设计和开发人员铺路，普通从业人员只做一些打磨和修补的工作。\
正如吴军老师在《硅谷来信2016》中提到的：
>在未来的智能时代，真正受益于技术进步的个人可以不超过人口的2%。坦率地讲，仅仅会写几行JavaScript的人不属于我说的2%的行列，这些人恰恰在未来是要被计算机淘汰的。......如果有些人就满足于五年（正常工作大约10000小时）坚持不懈地写JavaScript，非常糟糕，因为这是低水平重复，即便五年后你把它练熟了，可能JavaScript已经过时了，或者是由计算机来写了。

## BFF
Backends For Frontends是一种专门为前端设计的后端API服务，虽然有人认为它能解决一些问题，比如：
1. api接口频繁变动的问题
2. 前后端多次请求的性能问题
3. 字段的冗余和一致性问题

但是我认为它主要提供了一种便捷的解决方案，以及承载溢出的劳动力。

*开始使用：*\
如果你已经安装了Node.js，新建一个server.js文件，其内容如下：
```js
const http = require('http')

const hostname = '127.0.0.1'
const port = 3000

const server = http.createServer((req, res) => {
    res.statusCode = 200
    res.setHeader('Content-Type', 'text/plain')
    res.end('Hello World\n')
})

server.listen(port, hostname, () => {
    console.log(`Server running at http://${hostname}:${port}/`)
})
```
然后在文件目录命令行执行：`node ./server.js` 即可启动一个最简单的api服务。最后浏览器打开控制台上显示的链接即可查看运行结果。

#### Egg.js
Egg.js是一个阿里团队基于Node.js和Koa打造的一个企业级后端服务框架，它是开源的。下面我们使用它来写两个连接mongo数据库的api接口。\
前提：npm版本 >=6.1.0，准备一个本地或者远程能链接的 [mongoDB数据库](https://cloud.mongodb.com/)。

1. 初始化项目
```sh
mkdir egg-example && cd egg-example
npm init egg --type=simple
npm i

// 启动项目
npm run dev
```
2. 安装mongoDB JavaScript工具库： `npm i egg-mongoose --save`
3. 在config/plugin.js中注册egg-mongoose\
    内容如下：
    ```js
    module.exports = {
        mongoose: {
            enable: true,
            package: 'egg-mongoose',
        },
    }
    ```
4. 修改config/config.default.js，配置mongoDB链接\
    内容如下：
    ```js
    module.exports = (appInfo) => {
        const config = (exports = {})

        config.keys = appInfo.name + '_1650010446983_6736'

        config.middleware = []

        const userConfig = {}

        config.mongoose = {
            url: 'mongodb://127.0.0.1:27017/local', // local 是数据库名
            options: {
                useUnifiedTopology: true,
            },
        }

        return {
            ...config,
            ...userConfig,
        }
    }
    ```
5. 在app文件夹下新建一个model目录，并在目录下新建一个student.js\
    内容如下：
    ```js
    module.exports = (app) => {
        const mongoose = app.mongoose
        const Schema = mongoose.Schema

        const StudentSchema = new Schema({
            name: { type: String },
            age: { type: Number },
            gender: { type: String, enum: ['男', '女'] },
        })

        return mongoose.model('Student', StudentSchema, 'student')
    }
    ```
6. 在app文件夹下新建一个service目录，并在目录下新建一个student.js\
    内容如下：
    ```js
    const Service = require('egg').Service

    class StudentService extends Service {
        // 查询学生
        async list() {
            return this.ctx.model.Student.find()
        }
        // 新增学生
        async add(student) {
            return this.ctx.model.Student.create(student)
        }
    }

    module.exports = StudentService
    ```
7. 在app/controller目录下新建student.js\
    内容如下：
    ```js
    const Controller = require('egg').Controller

    class HomeController extends Controller {
        // 查询学生
        async list() {
            const { ctx } = this
            let studentList = await ctx.service.student.list()
            ctx.body = studentList
        }
        // 新增学生
        async add() {
            const { ctx } = this
            const student = ctx.request.query
            const result = await ctx.service.student.add(student)
            ctx.body = result
        }
    }

    module.exports = HomeController
    ```
8. 修改路由文件app/router.js\
    内容如下：
    ```js
    module.exports = (app) => {
        const { router, controller } = app
        router.get('/', controller.home.index)
        router.get('/student/list', controller.student.list)
        router.get('/student/add', controller.student.add)
    }
    ```
9. 浏览器或者Postman验证结果
    ```
    http://127.0.0.1:7001/student/add?name=wang&age=18&gender=男
    http://127.0.0.1:7001/student/list
    ```

## 手机APP&桌面应用
**手机APP**\
手机APP运行在IOS和Andriod两大平台，开发方式目前有三种：
1. native app，使用原生语言开发
2. hybrid app，使用原生语言+Web语言混合开发
3. web app，使用Web语言开发

相比原生开发或者使用FLutter（Dart语言），Web语言通过容器和转译的方式，使得APP开发更加便捷和容易，虽然牺牲了性能和体验。\
目前比较成熟的Web跨端开发的框架包括：React Native、uni-app、taro。

**桌面应用**\
思路都是使用HTML + CSS + JS的方式来实现桌面端应用，目前比较流行的框架包括Electron 和 Tauri，其中Electron的技术方案是Chromium + Nodejs，Tauri是采用Webview + Rust语言来实现。

## WebGL
WebGL是一种在浏览器里展示3D场景和模型的技术。随着硬件设备以及浏览器性能的提升，数字孪生、沉浸式体验等方面的需求。它得到了越来越多的应用。直接使用WebGL进行开发，还是有一定门槛，需要数学、图形学、着色器编程语言等比较专业的知识。同样在这个领域，也已经存在一片“花园”了，我们可以采用框架来使用WebGL，比如 `three.js`。

### three.js
*开始使用：*\
首先下载 [three.js](https://threejs.org/build/three.js) 库文件，新建一个html文件，内容如下：
```js
<!DOCTYPE html>
<html>
    <body>
        <script src="./three.js"></script>
        <script>
            const scene = new THREE.Scene() // 场景
            const color = new THREE.Color(0x7298a5)
            scene.background = color
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 1000) // 视角
            camera.position.z = 5

            // 渲染器
            const renderer = new THREE.WebGLRenderer()
            renderer.setSize(window.innerWidth, window.innerHeight)
            document.body.appendChild(renderer.domElement)

            // 物体模型
            const geometry = new THREE.BoxGeometry()
            const material = new THREE.MeshNormalMaterial()
            const cube = new THREE.Mesh(geometry, material)
            cube.castShadow = true
            scene.add(cube)

            // 动画
            function animate() {
                requestAnimationFrame(animate)
                cube.rotation.z += 0.01
                cube.rotation.y += 0.01
                renderer.render(scene, camera)
            }
            animate()
        </script>
    </body>
</html>
```

![three-3d.gif](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/241191cca87047ca8171c76b25f41cc1~tplv-k3u1fbpfcp-watermark.image?)

### CSS 3D
利用CSS3的transform属性，也能实现简单的3D交互效果。\
只需设置容器变换方式为：`transform-style: preserve-3d`，让其维持3D显示的特性，然后设置其子元素为：`transform: rotateY(xxdeg) translateZ(xxpx)`，使其在3D空间内偏移即可。全部代码如下：
```js
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>CSS 3D示例</title>
        <style>
            :root {
                --item-height: 150px;
            }
            html,
            body {
                height: 100%;
            }
            body {
                perspective: 1000px;
                background: #7298a5;
                overflow: hidden;
            }
            .wrap {
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                width: 800px;
                height: var(--item-height);
                margin: auto;
                transform-style: preserve-3d;
                animation: carousel 15s linear 0s infinite;
            }
            .list {
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                margin: auto;
                list-style: none;
                transition: 0.5s;
            }
            .item {
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                width: 300px;
                height: var(--item-height);
                margin: auto;
                line-height: var(--item-height);
                text-align: center;
                font-size: 50px;
                color: #fff;
                background: #ffd591;
                border: 1px solid #eee;
            }
            .item:hover {
                cursor: pointer;
                color: #ff4d4f;
            }
            @keyframes carousel {
                0% {
                    transform: rotateX(10deg) rotateY(0deg);
                }
                100% {
                    transform: rotateX(10deg) rotateY(360deg);
                }
            }
        </style>
    </head>
    <body>
        <div class="wrap">
            <ul class="list">
                <li class="item">1</li>
                <li class="item">2</li>
                <li class="item">3</li>
                <li class="item">4</li>
                <li class="item">5</li>
                <li class="item">6</li>
                <li class="item">7</li>
                <li class="item">8</li>
                <li class="item">9</li>
                <li class="item">10</li>
            </ul>
        </div>

        <script>
            let list = document.querySelector('.list')
            let items = list.querySelectorAll('.item')
            let itemWidth = items[0].offsetWidth //单个图片的宽度
            let perimeter = items.length * itemWidth //算出所有图片的宽度（周长）
            let radius = perimeter / (2 * Math.PI) //算出半径
            let angle = 360 / items.length //计算每张图片旋转的角度

            Array.from(items).forEach((item, index) => {
                //把图片通过位移和旋转拼成圆环
                item.style.transform = `rotateY(${angle * index}deg) translateZ(${radius}px)`
            })
        </script>
    </body>
</html>
```

![css3-3d.gif](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86b6376f8b5348948fb880ff92920e37~tplv-k3u1fbpfcp-watermark.image?)

CSS3中与3D相关的属性：\
transform： 变换\
perspective： 摄像机距离屏幕的距离\
perspective-origin： 摄像机在X轴和Y轴的坐标\
transform-style： 变换方式\
backface-visibility： 背面是否显示\
matrix3d：变换矩阵

## WSAM
在Node.js中文官网教程中提供了如下信息：\
`WebAssembly` 是一种高性能的类汇编语言，可以从包括 C/C++、Rust 和 AssemblyScript 在内的无数语言进行编译。 目前，Chrome、Firefox、Safari、Edge 和 Node.js 都支持它！

有多种方法可用于生成 WebAssembly 二进制文件，包括：
- 手工编写 WebAssembly（.wat）并使用 wabt 等工具转换为二进制格式
- 在 C/C++ 应用程序中使用 emscripten
- 在 Rust 应用程序中使用 wasm-pack
- 如果你喜欢类似 TypeScript 的体验，则使用 AssemblyScript

这意味着某些原来只能运行在操作系统上的程序，也能在浏览器或者Node.js环境运行，它们原来是用C++或者Rust等语言编写。

# 总结
文章结束了，一段通过搜索引擎对信息的重新排列，个人感觉挺有意思的，像一只小青蛙在一片片带着画面的时间荷叶间跳跃前进，从1969年跳到了当下，回过头拍了一张剪影，紧接着又跳入无限。

<script src="https://cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome/css/font-awesome.min.css"/>
<script src="https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget/autoload.js"></script>
