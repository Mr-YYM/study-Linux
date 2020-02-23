# Git

## 简介 Preference

## 安装

https://linuxize.com/post/how-to-install-git-on-centos-7/

Centos 默认的 yum 安装的 git 版本只有`1.8`，太旧了，我们需要额外添加一个源

```ini
# sudo vim /etc/yum.repos.d/wandisco-git.repo
[wandisco-git]
name=Wandisco GIT Repository
baseurl=http://opensource.wandisco.com/centos/7/git/$basearch/
enabled=1
gpgcheck=1
gpgkey=http://opensource.wandisco.com/RPM-GPG-KEY-WANdisco

# 添加完成后执行 yum instll git 即可
```

#### 初始配置

```shell
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
```

## 代理设置

### 走 HTTP 代理

```shell
git config --global http.proxy "http://127.0.0.1:1087"
git config --global https.proxy "http://127.0.0.1:1087"
```

### 走 socks5 代理（如 Shadowsocks）

```shell
git config --global http.proxy "socks5://127.0.0.1:1086"
git config --global https.proxy "socks5://127.0.0.1:1086"
```

### 取消设置

```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```