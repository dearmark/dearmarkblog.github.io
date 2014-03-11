---
layout: post
title: "Install and Config Octopress"
date: 2014-03-09 02:04:19 +0800
comments: true
categories: 
- octopresss
- blog
---
{% img /images/logo.png Logo%}

## Octepress装得差不多了，记录一些事情

* 要在文章中上传图片，直接copy到/source/images目录下即可。在文章中用 `{% img /images/pic_name.png Caption %}`来引用即可

* 在文章中插入代码，用` ```[language] 这儿放你要插入的代码即可。``` `
* 在html中插入图片，如about me部分。`<p><img src="/images/pic_name.png"></p>`
* rake watch 检测文件变化，实时生成新内容
* 在定制文件`/source/_includes/custom/head.html `把google的自定义字体去掉
* If you are working on a multi-author blog, you can add `author: Your Name` to the metadata for proper attribution on a post. If you are working on a draft, you can add `published: false` to prevent it from being posted when you generate your blog. **If you set published: false, your posts will only be visible in preview mode.**
* Commit
```
rake gen_deploy
git commit -am "`date`" && git push origin source
```
_OR_
``` bash micro script to simplify the publish process http://blog.revolunet.com/blog/2013/04/15/octopress-cheatsheet/
#!/bin/sh
# push.sh : publish & commit with a single command
git add source
git commit -am "`date`" && git push origin source
rake gen_deploy
```
