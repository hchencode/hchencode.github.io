Hexo+github建站备忘
--------

--------

### 建站背景#


昨天在百度一个python用法时进到一个[个人博客](http://www.csuldw.com/)里，查完用法之后突然觉得那个博客做得挺好，内容充实有用，风格简约，同时我也注意到那个博客是Hexo框架的，稍微百度了一下就发现Hexo挺有意思的，也比较适合做轻量级的博客。其中有一个[hexo入门指南](http://www.maintao.com/2014/hexo-beginner%27s-guide/)的文章里说道：

"ghost目前人气最高，号称是要取代WordPress的下一代博客平台。不过问题也正在于此，它的目标定位是博客平台，像WordPress一样重量级。仅用于一个独立博客，有点高射炮打蚊子的意思。最关键的一点，ghost生成的是动态网站，依赖数据库，我的直觉立刻让我放弃掉了ghost。
为什么我要排斥数据库？一个原因是我对纯文本有偏爱，感觉上要比二进制可控。但主要原因还是出于我的一个顾虑，说来可笑：我希望到了年老昏花的时候，这个博客依然在。
那时可能已经写不动了，技术上的事更折腾不了，但我希望它还能运行，能看。站在今天，无法预料那时候是什么操作系统，天知道nodeJS能不能坚持到那天，更别说ghost。唯一能确定的是，**越简单、对环境依赖越少，就越有可能长命百岁。我可不想到时候发现博客打不开了，戴上花镜趴上前去一看，db connection error。**"

看到这段话的最后，我都没忍住笑出声了。这个作者也提到了一些用Hexo做个人博客的好处，我就不赘述了。我自己比较赞同的Hexo的一个优点是博客内容是以纯文本记录的，可以比较好的保存及迁移。


--------

### 建站步骤：#


主要分为三部分：

- 注册[github](https://github.com/)账号并建立仓库(Repsitory);

- 本地安装配置[nodejs](https://nodejs.org/)及[hexo](https://hexo.io/)（注：我的系统是linux Mint 18）;

- 注册域名并与github绑定（可选）.

以下为具体操作：  


#### 注册[github](https://github.com/)账号并建立仓库(Repsitory):#

进入[github](https://github.com/)官网注册账号并建立以**username.github.io**为名的仓库（Repository),username部分必须与注册的用户名完全相同（githubzhi只为每个用户提供一个个人网站）。

#### 本地安装配置[nodejs](https://nodejs.org/)及[hexo](https://hexo.io/):#


**安装nodejs**（官网给了好几种装发，各种安装帖里也列出了多种装发，此处为我自己[安装成功的方法](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)）:


    ~$curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
    ~$sudo apt-get install -y nodejs

**安装hexo:**

**安装：**

    ~$npm install hexo-cli -g
    ~$hexo init blog
    ~$cd blog
    ~/blog$npm install
    ~/blog$hexo server

**配置：**

编辑 /blog/_config.yml文件

- 配置网站名称等；

- 配置**Deployment**

        deploy:
        type: github
        repository: https://github.com/username/username.github.io.git
        branch: master

新建CNAME文件： 在**/myblog/public**目录下新建**CNAME**文件，文件内容很简单，就是自己购买好的域名。

**发布：**

如何写博客内容就不赘述了，主要就是用Markdown文本写好内容，放到**myblog/source/_posts/**文件夹下。

发布博客分两步：

1. 生成静态网页：

        ~/blog$hexo g

2. 向github推送：

        ~/blog$hexo d

此时，应该就可以通过**username.github.io.git**访问网站了。

注册域名并与github绑定（可选）
---

如果有购买好的域名，在购买域名的网站上对域名解析添加两条**CNAME**记录，讲购买的域名解析到**username.github.io.git**.

此时，应该可以通过购买的域名访问网站了。

### DONE!





