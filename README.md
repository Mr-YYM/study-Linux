# study-Linux
学习 Linux 的仓库

## 如何获取（搭建）Linux 环境

- 云主机（推荐，学生有优惠价格，十元一个月）
- 电脑装机
- 虚拟机

## Linux 内核版本

```shell
uname -r # 查看内核版本
# 3.10.0-693.el7.x86_64
```

## Linux 一切皆文件

- `pwd` 查看当前目录
-  `cd` 更改目录 
- `ls` 列出目录的文件

## 小技巧

| 操作     | 操作             |
| -------- | ---------------- |
| curl + u | 快速删掉一行命令 |
|          |                  |
|          |                  |
|          |                  |
|          |                  |
|          |                  |
|          |                  |
|          |                  |
|          |                  |

https://zju.date/alpine-set-timezone/ docker apline 镜像修改时区

https://linuxize.com/post/how-to-set-or-change-timezone-on-centos-7/ 系统时区修改

### 文件解压缩

- `tar.gz`文件解压

  https://blog.csdn.net/qq_38486203/article/details/80067744
  https://www.cnblogs.com/cursorhu/p/5891699.html

### sslocal + proxychains4 实现 Linux Terminals 翻墙(CENTOS 7)

- 安装配置启动 sslocal

  ```shell
  pip install shadowsocks -i https://pypi.tuna.tsinghua.edu.cn/simple
  ```

  ```json
  # 配置 sslocal
  # mkdir /etc/sslocal
  # vim /etc/sslocal/ss.json
  {
    "server":"xxx",
    "local_address": "127.0.0.1",
    "local_port":1080,
    "server_port":12000,
    "password":"xxx",
    "timeout":300,
    "method":"aes-256-cfb"
  }
  ```

  ```shell
  sslocal -c /etc/sslocal/ss.json -d start
  ```

- 安装 proxychains4

  参考：https://github.com/rofl0r/proxychains-ng/releases

  ```shell
  wget https://github.com/rofl0r/proxychains-ng/archive/v4.14.tar.gz
  tar zxvf v4.14.tar.gz
  cd proxychains-ng-4.14
  yum install -y gcc
  ```

  这是源码包，需要我们编译安装。编译前需要修改一些 Makefile , 否则会有 bug，参考:https://github.com/rofl0r/proxychains-ng/issues/53

  - 替换 85 行为：：注意开头加一个 tab。。不然会报错

    ```shell
      $(CC) -shared $(LDFLAGS) $(LD_SET_SONAME)$(LDSO_PATHNAME) -lpthread $(LIBDL) -o $@ $(LOBJS)
    ```

  ```shell
  ./configure --prefix=/usr --sysconfdir=/etc
  make
  make install
  make install-config
  ```
  
  ```ini
  # vim /etc/proxychains.conf
  # 文件最后修改为：
  [ProxyList]
  # add proxy here ...
  # meanwile
  # defaults set to "tor"
  socks5  127.0.0.1 1080
  ```
  
  - 测试运行
  
    ```shell
    proxychains4 curl -I www.google.com
    ```

## 常用命令

### find

| 使用方法                               | 操作       |
| -------------------------------------- | ---------- |
| find [搜索位置] -name [要搜索的文件名] | 简单的搜索 |

### ln

| 使用方法 | 操作 |
| -------- | ---- |
| ln -s    |      |

### scp

| 使用方法                             | 操作                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| 发送指定文件到服务器【别把冒号忘了】 | scp[本地文件的路径] [服务器用户名]@[服务器地址]:[服务器上存放文件的路径] |
| 发送指定文件夹到服务器               | scp -r [本地文件的路径] [服务器用户名]@[服务器地址]:[服务器上存放文件的路径] |

### ssh

- 更方便的操作：使用 ssh [short name] 登陆主机 ➡️ 配置 .ssh/config 文件

  ```she
  vim .ssh/config
  
  Host [short name]
  Hostname [host ip address]
  User [host user name, root for example]
  ```

- 使用公钥密钥实现免密登陆