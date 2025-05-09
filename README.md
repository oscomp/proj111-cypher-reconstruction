# proj111-cypher-reconstruction
基于openssl实现远程SSH登录的国密改造

## 项目描述

2020年1月 1日，《中华人民共和国密码法》正式实施，从法律层面规范了国家商用密码的应用和管理，这也为推广和应用国密提供了必要的法律保障。目前的openssl目前已经支持了sm2/sm3/sm4国密算法，国密算法目前主要用于浏览器的https应用中。网络应用中仍然有其他协议中使用了加密算法，本赛题希望能够改造当前主流的SSH登录软件以支持国密算法。可选国密改造SSH协议软件有：openssh（C）、libssh（C）、paramiko（PYTHON）、apache-sshd（JAVA）

## 所属赛道

2025年全国大学生操作系统比赛的“OS功能挑战赛道”

## 参赛要求

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生或研究生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评选
- 请遵循“2025年全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

任明帅

- email: renmingshuai@huawei.com

### 难度

简单

## 特征

- 基于openssl提供的国密算法sm2/sm3/sm4改造openssh，使之改造后能够生成国密算法的密钥，并能使用国密算法自登录；
- 编写openssh国密改造的测试用例，使用lcov统计新增代码覆盖率，至少超过50%；
- 基于业界中已有方法进行微创新，可以选择在算法实现方面提高性能；

参考资料：
TASSL： https://github.com/jntass
GMSSL： https://github.com/guanzhi

## 进阶特性

改造paramiko/libssh/apache-sshd软件，使之能够选择使用国密算法登录openssh的服务端sshd。

## License

与改造的软件openssh(BSD)同License

## 预期目标

- 基于openeuler的openssl提供的国密算法改造openssh，使之改造后能够生成国密算法的密钥，并能使用国密算法自登录；
- 基于openeuler的openssl提供的国密算法改造paramiko/libssh/apache-sshd，使之能兼容上面修改的openssh；
- 选择本项目的同学也可提出自己的新想法，得到导师认可支持后亦可加入预期目标或进阶特性。


# 预期目标

### 注意：选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

### 第一题：基本的环境搭建和熟悉

- 在linux系统上编译并运行openssh社区的openssh-8.8p1，也可以使用openEuler系统上的openssh-8.8p1-1.oe1源码编译。
- 修改openssh的配置文件，使用各类支持的密钥交换、公钥认证、完整性认证、对称加密算法进行SSH登录，
  初步比较各类算法的性能。

### 第二题：将openssl提供算法库中的sm3/sm4国密算法适配到openssh中

- 在openssh的完整性认证mac中加入hmac-sm3算法，并能够通过配置这种算法登录；
- 在openssh的对称加密算法cipher中加入sm4-ctr算法，并能够通过配置这种算法登录；

### 第三题：将openssl提供算法库中的sm2国密算法适配到openssh中

- 适配ssh-keygen和ssh-keyscan命令，试它们能够生成和扫描sm2类型的密钥；
- 在openssh的公钥认证算法pubkeyacceptedkeytypes中加入sm2算法，并能够使用sm2密钥进行登录；
- 在openssh的密钥交换算法中加入sm2dh算法，并能够使用这种密钥交换算法进行登录；
