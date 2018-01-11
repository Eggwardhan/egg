---
layout: post
title: 使用Github Pages建独立博客
description: Github本身就是不错的代码社区，他也提供了一些其他的服务，比如Github Pages，使用它可以很方便的建立自己的独立博客，并且免费。
category: blog
---
本人在最初本打算原生搭建blog，可惜发现在windows+墙的阻碍下实现 有点困难，遂暂时选择了github page托管。
### why Github?
[Github][]很好的将代码和社区联系在了一起，于是发生了很多有趣的事情，世界也因为他美好了一点点。Github作为现在最流行的代码仓库，已经得到很多大公司和项目的青睐，比如[jQuery][]、[Twitter][]等。为使项目更方便的被人理解，介绍页面少不了，甚至会需要完整的文档站，Github替你想到了这一点，他提供了[Github Pages][]的服务，不仅可以方便的为项目建立介绍站点，也可以用来建立个人博客。

Github Pages有以下几个优点：

<ul>
    <li>轻量级的博客系统，没有麻烦的配置</li>
    <li>使用标记语言，比如<a href="http://markdown.tw">Markdown</a></li>
    <li>无需自己搭建服务器</li>
    <li>根据Github的限制，对应的每个站有300MB空间</li>
    <li>可以绑定自己的域名</li>
</ul>

当然他也有缺点：

* 使用[Jekyll][]模板系统，相当于静态页发布，适合博客，文档介绍等。
* 动态程序的部分相当局限，比如没有评论，不过还好我们有解决方案。
* 基于Git，很多东西需要动手，不像Wordpress有强大的后台


## 购买、绑定独立域名
翻看了知乎推狗爹的比较多[Godaddy][]，但本人因为信息导论课的原因顺手在腾讯云上买了，功能基本也能应付。至于域名解析，
我们选择[DNSPod][]的服务，他们的产品做得不错，易用、免费，收费版有更高端的功能，暂不需要。注册登录之后，按照DNSPod的说法，只需三步（我们插入一步）：

<ul>
	<li>首先添加域名记录，可参考DNSPod的帮助文档：<a href="https://www.dnspod.cn/Support">https://www.dnspod.cn/Support</a></li>
	<li>在DNSPod自己的域名下添加两条<a href="http://baike.baidu.com/view/65575.htm">A记录</a>，地址就是Github Pages的服务IP地址：192.30.252.153_
192.30.252.154（感谢Thomas Baillie大神的指导) 
</li>
	<li>在域名注册商处修改DNS服务:去Godaddy修改Nameservers为这两个地址：f1g1ns1.dnspod.net、f1g1ns2.dnspod.net。如果你不明白在哪里修改，可以参考这里：<a href="https://www.dnspod.cn/support/index/fid/119">Godaddy注册的域名如何使用DNSPod</a></li>
	
	<li>等待域名解析生效</li>
</ul>



## 配置和使用Github
Git是版本管理的未来，他的优点我不再赘述，相关资料很多。推荐这本[Git中文教程][4]。

要使用Git，需要安装它的客户端，推荐在Linux下使用Git，会比较方便。Windows版的下载地址在这里：[http://code.google.com/p/msysgit/downloads/list](http://code.google.com/p/msysgit/downloads/list "Windows版Git客户端")。其他系统的安装也可以参考官方的[安装教程][5]。

下载安装客户端之后，各个系统的配置就类似了，我们使用windows作为例子，Linux和Mac与此类似。

在Windows下，打开Git Bash，其他系统下面则打开终端（Terminal）。
然后具体教程就不多赘述了，可以看看我的学长[廖雪峰][]的博客,或者自己找找适合自己的。



## 使用GitHub Pages建立博客
与GitHub建立好链接之后，就可以方便的使用它提供的Pages服务，GitHub Pages分两种，一种是你的GitHub用户名建立的`username.github.io`这样的用户&组织页（站），另一种是依附项目的pages。

### User & Organization Pages
想建立个人博客是用的第一种，形如`eggwardhan.github.io`这样的可访问的站，每个用户名下面只能建立一个.
创建好`username.github.io`项目之后，提交一个`index.html`文件，然后`push`到GitHub的`master`分支（也就是普通意义上的主干）。第一次页面生效需要一些时间，大概10分钟左右。

生效之后，访问`username.github.io`就可以看到你上传的页面了，[eggwardhan.github.io][7]就是一个例子。

关于第二种项目`pages`，简单提一下，他和用户pages使用的后台程序是同一套，只不过它的目的是项目的帮助文档等跟项目绑定的内容，所以需要在项目的`gh-pages`分支上去提交相应的文件，GitHub会自动帮你生成项目pages。具体的使用帮助可以参考[Github Pages][]的官方文档：

### 绑定域名
我们在第一部分就提到了在DNS部分的设置，再来看在GitHub的配置，要想让`username.github.io`能通过你自己的域名来访问，需要在项目的根目录下新建一个名为`CNAME`的文件，文件内容形如：

    eggwardhan.com

你也可以绑定在二级域名上：

    blog.eggwardhan.com

需要提醒的一点是，如果你使用形如`eggwardhan.com`这样的一级域名的话，需要在DNS处设置A记录到，而不是在DNS处设置为CNAME的形式，否则可能会对其他服务（比如email）造成影响。

设置成功后，根据DNS的情况，最长可能需要一天才能生效，耐心等待吧。

## Jekyll模板系统
GitHub Pages为了提供对HTML内容的支持，选择了[Jekyll][]作为模板系统，Jekyll是一个强大的静态模板系统，作为个人博客使用，基本上可以满足要求，也能保持管理的方便，你可以查看[Jekyll官方文档][8]。

你可以直接fork[我的项目][11]，然后改名，就有了你自己的满足Jekyll要求的文档了，当然你也可以按照下面的介绍自己创建。

### Jekyll基本结构
Jekyll的核心其实就是一个文本的转换引擎，用你最喜欢的标记语言写文档，可以是Markdown、Textile或者HTML等等，再通过`layout`将文档拼装起来，根据你设置的URL规则来展现，这些都是通过严格的配置文件来定义，最终的产出就是web页面。

基本的Jekyll结构如下：

    |-- _config.yml
    |-- _draft
    |-- _includes
    |-- _layouts
    |   |-- default.html
    |   `-- post.html
    |-- _posts
    |   |-- 2007-10-29-why-every-programmer-should-play-nethack.textile
    |   `-- 2009-04-26-barcamp-boston-4-roundup.textile
    |-- _data
    |-- _site
    `-- index.html


来看看这些都有什么用：

### _config.yml

保存配置数据。很多配置选项都会直接从命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。

### _drafts

drafts 是未发布的文章。这些文件的格式中都没有 title.MARKUP 数据。学习如何使用 drafts.

### _includes

你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签  {% include file.ext %} 来把文件 _includes/file.ext 包含进来。

### _layouts

layouts 是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。 这将在下一个部分进行介绍。标签  {{ content }} 可以将content插入页面中。

### _posts

这里放的就是你的文章了。文件格式很重要，必须要符合: YEAR-MONTH-DAY-title.MARKUP。 The permalinks 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。

### _data

Well-formatted site data should be placed here. The jekyll engine will autoload all yaml files (ends with .yml or .yaml) in this directory. If there's a file members.yml under the directory, then you can access contents of the file through site.data.members.

### _site

一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的 .gitignore 文件中。

### index.html and other HTML, Markdown, Textile files

如果这些文件中包含 YAML 头信息 部分，Jekyll 就会自动将它们进行转换。当然，其他的如 .html， .markdown，  .md，或者 .textile 等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。

### Other Files/Folders

其他一些未被提及的目录和文件如  css 还有 images 文件夹， favicon.ico 等文件都将被完全拷贝到生成的 site 中.

你可以创建任何的文件夹，在根目录下面也可以创建任何文件，假设你创建了`project`文件夹，下面有一个`github-pages.md`的文件，那么你就可以通过`yoursite.com/project/github-pages`访问的到，如果你是使用一级域名的话。文件后缀可以是`.html`或者`markdown`或者`textile`。这里还有很多的例子：[https://github.com/mojombo/jekyll/wiki/Sites](https://github.com/mojombo/jekyll/wiki/Sites)

## Jekyll的配置
Jekyll的配置写在_config.yml文件中，可配置项有很多，我们不去一一追究了，很多配置虽有用但是一般不需要去关心，[官方配置文档][10]有很详细的说明，确实需要了可以去这里查，我们主要说两个比较重要的东西，一个是`Permalink`，还有就是自定义项。

`Permalink`项用来定义你最终的文章链接是什么形式，他有下面几个变量：

* `year` 文件名中的年份
* `month` 文件名中的月份
* `day` 文件名中的日期
* `title` 文件名中的文章标题
* `categories` 文章的分类，如果文章没有分类，会忽略
* `i-month` 文件名中的除去前缀0的月份
* `i-day` 文件名中的除去前缀0的日期

看看最终的配置效果：

* `permalink: pretty` /2018/01/1/slap-chop/index.html
* `permalink: /:month-:day-:year/:title.html` /01-01-2018/slap-chop.html
* `permalink: /blog/:year/:month/:day/:title` /blog/2017/12/31/slap-chop/index.html

我使用的是：

* `permalink: /:title` /github-pages

自定义项的内容，例如我们定义了`title:eggward的博客`这样一项，那么你就可以在文章中使用`{ { site.title }}`来引用这个变量了，非常方便定义些全局变量。

### YAML Front Matter和模板变量
对于使用YAML定义格式的文章，Jekyll会特别对待，他的格式要求比较严格，必须是这样的形式：

    ---
    layout: post
    title: Blogging Like a Hacker
    ---

前后的`---`不能省略，在这之间，你可以定一些你需要的变量，layout就是调用`_layouts`下面的某一个模板，他还有一些其他的变量可以使用：

* `permalink` 你可以对某一篇文章使用通用设置之外的永久链接
* `published` 可以单独设置某一篇文章是否需要发布
* `category` 设置文章的分类
* `tags` 设置文章的tag

上面的`title`就是自定义的内容，你也可以设置其他的内容，在文章中可以通过`{ { page.title }}`这样的形式调用。

模板变量，我们之前也涉及了不少了，还有其他需要的变量，可以参考官方的文档：[https://github.com/mojombo/jekyll/wiki/template-data](https://github.com/mojombo/jekyll/wiki/template-data "Jekyll Template Data")

## 使用Disqus管理评论
模板部分到此就算是配置完毕了，但是Jekyll只是个静态页面的发布系统，想做到关爽场倒是很容易，如果想要评论呢？也很简单。

现在专做评论模块的产品有很多，比如[Disqus][]，还有国产的[多说][]，Disqus对现在各种系统的支持都比较全面，到写博客为止，多说现在仅是WordPress的一个插件，所以我这里暂时也使用不了，多说与国内的社交网络紧密结合，还是有很多亮点的，值得期待一下。我先选择了Disqus。

注册账号什么的就不提了，Disqus支持很多的博客平台，参见下图：
![Disqus sites](/images/githubpages/disqus-site.jpg)

我们选择最下面的`Universal Code`就好，然后会看到一个介绍页面，把下面这段代码复制到你的模板里面，可以只复制到显示文章的模板中：

    <div id="disqus_thread"></div>
    <script type="text/javascript">
        /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
        var disqus_shortname = 'example'; // required: replace example with your forum shortname 这个地方需要改成你配置的网站名

        /* * * DON'T EDIT BELOW THIS LINE * * */
        (function() {
            var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
            dsq.src = 'http://' + disqus_shortname + '.disqus.com/embed.js';
            (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
        })();
    </script>
    <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
    <a href="http://disqus.com" class="dsq-brlink">blog comments powered by <span class="logo-disqus">Disqus</span></a>

配置完之后，你也可以做一些异步加载的处理，提高性能，比如我就在最开始页面打开的时候不显示评论，当你想看评论的时候，点击“显示评论”再加载Disqus的模块。代码很简单，你可以参考我的写法。

    $('#disqus_container .comment').on('click',function(){
            $(this).html('加载中...');
            var disqus_shortname = 'beiyuu';
            var that = this;
            BYB.includeScript('http://' + disqus_shortname + '.disqus.com/embed.js',function(){$(that).remove()}); //这是一个加载js的函数
    });

如果你不喜欢Disqus的样式，你也可以根据他生成的HTML结构，自己改写样式覆盖它的，Disqus现在也提供每个页面的评论数接口，[帮助文档][12]在这里可以看到。

## 代码高亮插件
如果写技术博客，代码高亮少不了，有两个可选插件[DlHightLight代码高亮组件][13]和[Google Code Prettify][14]。DLHightLight支持的语言相对较少一些，有js、css、xml和html，Google的高亮插件基本上任何语言都支持，也可以自定义语言，也支持自动识别，也有行号的特别支持。

Google的高亮插件使用也比较方便，只需要在`<pre>`的标签上加入`prettyprint`即可。所以我选择了Google Code Prettify。

## 搭建本地jekyll环境
这里主要介绍一下在Mac OS X下面的安装过程，其他操作系统可以参考官方的[jekyll安装][15]。

作为生活在水深火热的墙内人民，有必要进行下面一步修改gem的源，方便我们更快的下载所需组建：

    sudo gem sources --remove http://rubygems.org/
    sudo gem sources -a http://ruby.taobao.org/

然后用Gem安装jekyll

    $ gem install jekyll

不过一般如果有出错提示，你可能需要这样安装：

    $ sudo gem install jekyll

我到了这一步的时候总是提示错误`Failed to build gem native extension`，很可能的一个原因是没有安装rvm，[rvm的安装][16]可以参考这里，或者敲入下面的命令：

    $ curl -L https://get.rvm.io | bash -s stable --ruby

然后还需要安装Markdown的解释器，这个需要在你的_config.yml里面设置`markdown:rdiscount`：

    $ gem install jekyll rdiscount

好了，如果一切顺利的话，本地环境就基本搭建完成了，进入之前我们建立的博客目录，运行下面的命令：

    $ jekyll serve --watch

这个时候，你就可以通过`localhost:4000`来访问了。还有关于[jekyll bootstrap][17]的资料，需要自己修改调试的，可以研究一下。



## 结语
如果依旧不成功，请你坚持一下，善用搜索引擎，发挥你的热情继续折腾。

[廖雪峰]:   https://www.liaoxuefeng.com/ "廖雪峰"
[Eggward]:    http://eggwardhan.com  "eggward"
[Github]:   http://github.com "Github"
[jQuery]:   https://github.com/jquery/jquery "jQuery@github"
[Twitter]:  https://github.com/twitter/bootstrap "Twitter@github"
[Github Pages]: http://pages.github.com/ "Github Pages"
[Godaddy]:  http://www.godaddy.com/ "Godaddy"
[Jekyll]:   https://github.com/mojombo/jekyll "Jekyll"
[DNSPod]:   https://www.dnspod.cn/ "DNSPod"
[Disqus]: http://disqus.com/
[多说]: http://duoshuo.com/
[1]:    {{ page.url}}  ({{ page.title }})
[2]: http://markdown.tw/    "Markdown语法"
[3]:    http://baike.baidu.com/view/65575.htm "A记录"
[4]: http://progit.org/book/zh/ "Pro Git中文版"
[5]: http://help.github.com/mac-set-up-git/ "Mac下Git安装"
[6]: http://help.github.com/ssh-key-passphrases/
[7]: http://eggwardhan.github.io
[8]: https://github.com/mojombo/jekyll/blob/master/README.textile
[9]: https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter
[10]: https://github.com/mojombo/jekyll/wiki/configuration
[11]: https://github.com/beiyuu/Github-Pages-Example
[12]: http://docs.disqus.com/developers/universal/
[13]: http://mihai.bazon.net/projects/javascript-syntax-highlighting-engine
[14]: http://code.google.com/p/google-code-prettify/
[15]: https://github.com/mojombo/jekyll/wiki/Install
[16]: https://rvm.io/rvm/install/
[17]: http://jekyllbootstrap.com/
[18]: http://chxt6896.github.com/blog/2012/02/13/blog-jekyll-native.html
[a-record]: https://help.github.com/articles/my-custom-domain-isn-t-working