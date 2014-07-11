---
layout: default
title: Ubuntu下github connect错误解决（转载）
excerpt: connect to host github.com port 22 Connection timed out
tags: [Coding]
---
{{ page.title }}
================

原网址：http://blog.163.com/zhou_411424/blog/static/197362156201281725033556/

```
zhoulc@zhoulc-PC:~$ ssh git@github.com
ssh: connect to host github.com port 22: Connection timed out
```

解决办法：（linux下）

```
~$ cd ~

~$ cd .ssh/

~$ touch config
```

在.ssh目录下创建一个config文件，输入如下内容：

```
Host github.com
User xxx@163.com （你注册github时的邮箱，这里使用注册的用户名也行）
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
可以把以上内容拷到config文件里面，注意修改你的邮箱，保存并关闭
进行测试是否连接上github.com
zhoulc@zhoulc-PC:~/.ssh$ cd ~
zhoulc@zhoulc-PC:~$ ssh -T git@github.com
The authenticity of host '[ssh.github.com]:443 ([207.97.227.248]:443)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '[ssh.github.com]:443,[207.97.227.248]:443' (RSA) to the list of known hosts.
Hi zhou411424! You've successfully authenticated, but GitHub does not provide shell access.
出现Hi xxx!......表示连接成功。
```

{{ page.date | date: "%Y-%m-%d" }}
