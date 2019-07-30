## screen 工具的使用

screen 的作用总结下来大概有两个：

- 保持程序在后台的运行

  我们通常是通过 ssh 连接我们的云主机的，新手一开始会选择直接在 ssh 上运行一些程序。但是这样就会带来一个问题就是，当我们退出我们的 ssh 窗口的时候，我们的程序就会跟着停止，原因简单说就是因为我们的程序是运行在 `sshd /root@pts/[id]` 的子进程上的，当我们关闭 ssh 的时候，  `sshd /root@pts/[id]`  会自动终结，他连带的所有子进程自然就会结束。因此我们要在云主机上运行我们的程序就要另辟蹊径，一个简单的方法就是使用 screen 这个工具。将自己的程序运行在 screen session 下，关闭 ssh 连接，程序就不会自动结束了。具体的原理分析可以参看文章：[Linux 技巧：让进程在后台运行更可靠的几种方法](https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/)

- 辅助开发、运维的工具

  程序员在进行开发、运维工作的时候，往往需要同时需要多个命令行窗口进行同时操作。利用这个工具就可以省去多开终端的麻烦，脱离鼠标仅仅使用键盘就能完成许多事情。

  ![](https://raw.githubusercontent.com/Mr-YYM/study-Linux/master/Linux_tools/01-screen/assets/01-screen-split.png)

### 相关功能与概念

- session
- detach

这些命令按步骤学下去很容易理解

### 操作命令

| 命令                             | 操作                               |
| -------------------------------- | ---------------------------------- |
| screen -ls                       | 列出当前所有的 session             |
| screen -S [session name]         | 新建一个叫 session name 的 session |
| screen -d [session name]         | detach 某个session                 |
| screen -r [session name]         |                                    |
| screen -r [session name] -X quit | 删除一个 session                   |

### 快捷键命令

**在每个screen session 下，所有命令都以 ctrl+a(C-a) 开始**

| 命令    | 操作                                                         |
| ------- | ------------------------------------------------------------ |
| C-a d   | 暂时中断会话 ➡️ screen 会提示：[detached from [id].[session name]] |
| 🌟Tips   | 暂时中断之后，想要恢复就使用 screen -r [session name] 命令就可以恢复啦！！ |
| C-a c   | 创建一个新的运行 shell 的窗口并切换到该窗口                  |
| C-a p   | 切换到上一个窗口                                             |
| C-a n   | 切换到下一个窗口                                             |
| C-a "   | 查看包含所有的窗口列表                                       |
| 🌟Tips   | 学会新建窗口与切换后，就要开始了解如何分割屏幕，在每个子屏上我们可以使用以上的切换命令来选择每个子屏显示哪个窗口 |
| C-a S   | 水平分割屏幕 Horizontally                                    |
| C-a \|  | 垂直分割屏幕 Vertically                                      |
| C-a Tab | 分割屏幕后，切换不同的次屏                                   |
| C-a Q   | 分屏后退出除当前窗口外的所有窗口                             |
| C-a X   | 分屏后取消当前窗口                                           |
| C-a k   | kill 掉当前窗口【c 命令创建的那个】，当最后一个也 kill 掉，整个 session 就会被删掉 |