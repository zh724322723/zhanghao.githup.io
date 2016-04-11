title: "创建属于你自己的github博客"
date: 2015-04-30 20:09:51
tags: [git, github, hexo, blog]
categories: hexo
---
## 如何创建一个属于你自己的博客
经过2天的折腾，终于把github博客搭建了起来,使用的工具是hexo。过程中遇到了小小的困难通过google和咨询朋友整个过程还算比较顺利。我决定把这个过程中遇到的问题及解决办法和大家分享一下。
### 准备工作
#### 1.github注册
- 1.1首先需要在[github](https://github.com/)注册自己的账号。
![](/2015/04/30/buildGitHubBlog/img/githubsignup.bmp)
账号注册好后面回用到，也可跳过该步骤用到时再注册。

#### 2.git安装
不了解git的同学，建议先学习下git的基本用法。英文好的同学可直接到[git官网](http://git-scm.com/book/en/v2)学习，英语不好的同学可参考[http://www.bootcss.com/p/git-guide/](http://www.bootcss.com/p/git-guide/),强烈建议阅读英文文档。
2.1首先到[git官网](http://git-scm.com/downloads)下载相应操作系统的git版本，下载后傻瓜式安装。

#### 3.node.js安装
在[nodejs官网 https://nodejs.org/](https://nodejs.org/)下载nodejs。
![](/2015/04/30/buildGitHubBlog/img/node.bmp)
点击Install安装吧。
#### 4.安装hexo
hexo的使用文档参见官网说明[http://hexo.io/zh-cn/](http://hexo.io/zh-cn/)。
##### 4.1用npm命令安装hexo
``` bash
    npm install hexo-cli -g
```
安装hexo服务器
``` bash
    npm install hexo-server --save
```
##### 4.2在githup创建仓库
登录刚才已注册好的github账户，点击下图展示区域建立仓库。
![](/2015/04/30/buildGitHubBlog/img/github01.bmp)
![](/2015/04/30/buildGitHubBlog/img/github02.bmp)
注意项目的名字要和注册时的用户名一样。
##### 4.3生成并配置git ssh公钥
生成ssh公钥的方法参考[官方说明文档](https://git-scm.com/book/zh/v1/%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E7%94%9F%E6%88%90-SSH-%E5%85%AC%E9%92%A5)
``` bash
    ssh-keygen
```
##### 4.4用hexo创建blog项目
``` bash
    hexo init blog
    cd blog
    npm install
```
启动服务预览我们刚才建立的项目
```
    hexo server -i localhost
```
在浏览器输入 `localhost:4000/`
##### 4.5将博客站点发布到ggithub
修改_config.yml配置文件
```
    deploy:
      type: git
      repo: https://github.com/zhanghao87/zhanghao87.github.io.git
      branch: master
      message: updated:{{ now("YYYY-MM-DD HH:mm:ss") }}
```
把repo：地址改为注册的github地址。
发布博客到github
``` bash
    hexo deploy
```