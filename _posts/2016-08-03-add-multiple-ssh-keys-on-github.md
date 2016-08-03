--
layout: post
title: 'add multiple ssh keys on github'
date:   2016-08-03 09:46:24 +0800
categories: himdd update
---

GitHub后台可以添加多个SSH Keys，但是同一个SSH Keys只能在添加在一个帐号上（添加时提示“Key is already in use”）。理由很容易想到，SSH公钥使用时相当于用户名密码，不可能两个不同的帐号使>用同一个用户名密码。要想在多个GitHub帐号上添加公钥，就要在本地生成多个SSH Keys，每个GitHub帐号对应一个不同的SSH Keys。步骤如下：

1. 生成一个新的SSH KEY

{% highlight bash %}
rry@thk:~$ ssh-keygen -t rsa -C 'xx@xx.com'
Generating public/private rsa key pair.
Enter file in which to save the key (~/.ssh/id_rsa): ~/.ssh/id_rsa2 #这里输入一个新的ssh key文件名
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in ~/.ssh/id_rsa2.
Your public key has been saved in ~/.ssh/id_rsa2.pub.
The key fingerprint is:
3a:01:17:b3:f9:26:5b:53:b3:69:be:71:a8:66:f6:96 xxxx
The key is randomart image is:
+--[ RSA 2048]----+
|      o          |
|       =         |
|    . +   o      |
|     . . . +     |
|      o S +      |
|       B + .     |
|      +  .+ +    |
|       .E..+     |
|       +.oo      |
+-----------------+
larry@thk:~$ ssh-add ~/.ssh/id_rsa2
Identity added: ~/.ssh/id_rsa2 (~/.ssh/id_rsa2)
{% endhighlight %}

~/.ssh/id_rsa2为新SSH Keys文件名，根据实际情况修改，保证每次不一样即可。

2. 打开新生成的~/.ssh/id_rsa2.pub文件，将里面的内容添加到GitHub后台。

3. 打开~/.ssh/config文件（没有则创建），添加一个Host：

{% highlight bash %}
#建一个github别名，新建的帐号使用这个别名做克隆和更新
Host github2
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa2.pub
{% endhighlight %}

4. 将GitHub SSH仓库地址中的git@github.com替换成新建的Host别名。

如原地址是：git@github.com:freehost/mail.git，替换后应该是：github2:freehost/mail.git
如果是新建的仓库，直接使用替换后的URL克隆即可。如果已经使用原地址克隆过了，可以使用命令修改：
{% highlight bash %}
git remote set-url origin github2:freehost/mail.git
{% endhighlight %}
