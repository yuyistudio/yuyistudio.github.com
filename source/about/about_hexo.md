---
title: 关于建站
date: 2016-11-19 23:12:01
---

该网站的文章全部是使用Markdown编写的，并使用Hexo生成的静态页面，并上传到github上以显示。想如此建站的小伙伴建议读完本文有了大概的思路再去实践。

## Hexo的安装

原理

> 1. hexo是基于node.js的，也就是说hexo是用js实现的，用nodeJs去执行。
	本地预览用的HTTP服务器多半也就直接用了nodeJs。
> 2. hexo可以根据`source`目录下的`markdown`文件生成静态网站，
	每个markdown文件就是网站的一个页面。
> 3. 生成的网站保存在`public`目录下。

1. [安装](#http://baixin.io/2015/08/HEXO%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)
2. [配置](#http://www.isetsuna.com/hexo/install-config/)
3. [万能的官网](#https://hexo.io/docs/writing.html)

## Hexo的使用

基本命令

```shell
# 生成 source/_post/filename.md 文件
# 修改此文件观察效果
hexo new post filename 

# generate命令会重新生成网页静态文件
# md编辑的时候应该使用utf8编码，要不然会乱码
hexo g    # generate 重新生成网页静态文件。md编辑的时候应该使用utf8编码，要不然会

# server命令开启本地预览。默认端口`4000`。
# Linux或者windows git bash下可以用`&`放到后台执行
# 不需要每次生成代码后都重启。
hexo s
```

每次改完`md`文件后，`hexo g`重新生成文件即可预览效果。可能遇到修改不生效的问题，多半是浏览器缓存导致的。

## 同步到git

原理
> `hexo deploy`命令将`public`目录下面的所有文件保存到`_config.xml`指定的地方

修改_config.xml

```shell
deploy:
  type: git
  repository: git@github.com:yuyistudio/yuyistudio.github.com.git
  branch: master
```

`github`应该只将`master`分支的文件作为网页来展示，所以这里必须使用`master`分支。该分支保存了`Hexo`生成的静态网页。

使用下面的命令，将生成的静态网站同步到git的master分支，这时候别人就能看到你的网站了。

```shell
hexo d	# hexo deploy
```

其他文件（如你编写的`md`文件），需要手动保存到`git`上。所以新建一个空分支，假设叫做`hexo`，将代码手动push到分支`hexo`上。至于需要保存什么文件就是自己决定了，最起码你自己写的md文件得保存一下吧。

你可以使用下面这个`.gitignore`，然后把`git status`显示的其他文件都保存到刚才新建的分支上面即可。

```shell
public
.deploy_git/
.npmignore
db.json
npm-debug.log
```

`hexo d`执行的时候不需要先将分支切换到`master`，所以可以将默认分支设置为分支`hexo`。本地可以就一直都在分支`hexo`，不用切换到master，这样修改和`push`源文件都会方便一些。



