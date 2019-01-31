---
layout: post
title:  "mac上部署GitHub博客jekyll环境"
date:   2019-01-31 15:30:24 +0800
categories: miaomiao1234 update
---

### 1.如果本机版本过低，可通过brew安装ruby，否则跳过

```
#安装brew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#安装ruby
brew install ruby
```

### 2.通过RubyGems安装Jekyll && bundle

```
gem install jekyll
gem install bundle
```
`#可能需要添加国内 gems 源`<br/>
`#添加方法: `https://ruby.taobao.org/

### 3.执行

```
git clone https://github.com/yourBlogsName/.github.io.git

cd yourBlogsName.github.io

bundle install
```
### 4.预览效果，直接执行

```
rake
```
`默认访问地址为：` http://127.0.0.1:4000/ <br/>
或者
```
bundle exec jekyll serve
```

### 5.进行提交

```
git add .
git commit -m "remarks信息"
git push
```

### 6.如果是自己搭建的环境，修改完成之后执行

```
rake build
```
提交也可以使用
```
rake deploy
```
会自动提交给github，并且通过webhook（需要seting - > Webhooks && Services配置）回调部署机器

### 7.更多<a href="https://jekyllrb.com/">Jekyll</a>

