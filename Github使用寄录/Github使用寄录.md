# Github使用寄录

## 试图在Clion中将项目文件远程推送至Github的寄录

普通地使用了Clion自带的推送选项，普通地将远程URL设为我自己的Github远程仓库的http地址，然后试图推送时遇到如下报错：

```
fatal: Authentication failed for 'https://github.com/doge60/mavlink_test/'
```

初步判断是本机与github远程连接时由于某些安全校验未通过而被拒绝连接（）。具体是什么暗号对不上花了一小时余排查。。最终锁定为ssh校验未通过的问题，问题描述与解决方法都已经有先人记录下来了：

[如何解决：ssh: connect to host github.com port 22: Connection refused_ssh: connect to host port 22: connection refused-CSDN博客](https://blog.csdn.net/hjy_mysql/article/details/131596257)

按先人指引解决该问题后，仍然报错。。。

最后发现是要先pull，让远程仓库和本地仓库同步，然后再push，不能直接push。。。

即先在终端或git bash中输入：

```
git pull --rebase origin main
```

然后再输入：

```
git push -u origin main
```

或者直接选clion本身自带的提交选项。。。

（第一次推送到远程库，要先pull然后才能push，这tm不是git基本功吗？？？？？？？我tm排一个多小时雷最后就是为了这样一个愚蠢的操作错误。。。。(⊙﹏⊙)我的一个晚上的宝贵的生命。。。。。/(ㄒoㄒ)/~~