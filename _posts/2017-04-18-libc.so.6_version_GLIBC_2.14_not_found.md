---
layout: post
title: "解决libc.so.6: version `GLIBC_2.14' not found问题"
date:   2017-04-18 09:46:24 +0800
categories: himdd update
---

## 安装 4.8.x的gcc 
自己google吧。
假设安装在/home/work/soft/gcc-4.8.2
## 查看
```
strings /home/work/soft/gcc-4.8.2/lib64/libc.so.6 |grep GLIBC_ 
GLIBC_2.2.5
GLIBC_2.2.6
GLIBC_2.3
GLIBC_2.3.2
GLIBC_2.3.3
GLIBC_2.3.4
GLIBC_2.4
GLIBC_2.5
GLIBC_2.6
GLIBC_2.7
GLIBC_2.8
GLIBC_2.9
GLIBC_2.10
GLIBC_2.11
GLIBC_2.12
GLIBC_2.13
GLIBC_2.14
GLIBC_2.15
GLIBC_2.16
GLIBC_2.17
GLIBC_2.18
GLIBC_PRIVATE
```
## patchelf 

假定找不到GLIBC_2.14的是$ROOT_DIR/node/node(bin文件)。
```
patchelf --set-interpreter /home/work/soft/gcc-4.8.2/lib64/ld-linux-x86-64.so.2  $ROOT_DIR/node/node
patchelf --set-rpath '$ORIGIN:$ORIGIN/lib:$ORIGIN/lib64:$ORIGIN/../lib:$ORIGIN/../lib64:/home/work/soft/gcc-4.8.2/lib:/home/work/soft/gcc-4.8.2/lib64' $ROOT_DIR/node/node
```

