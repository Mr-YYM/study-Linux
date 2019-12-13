# Chrony

## 简介

Chrony是一个开源的自由软件，它能保持系统时钟与时钟服务器（NTP）同步，让时间保持精确。

它由两个程序组成：chronyd和chronyc。

chronyd是一个后台运行的守护进程，用于调整内核中运行的系统时钟和时钟服务器同步。它确定计算机增减时间的比率，并对此进行补偿。

## 安装与启动

```shell
yum install -y chrony
systemctl start chronyd.service
systemctl enable chronyd.service
```





## Reference

1. https://cloud.tencent.com/developer/article/1008065