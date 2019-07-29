## screen 工具的使用

### 相关功能与概念

- session

这些命令按步骤学下去很容易理解

### 相关命令

| 命令                             | 操作             |
| -------------------------------- | ---------------- |
| screen -ls                       |                  |
| screen -S [session name]         |                  |
| screen -d [session name]         |                  |
| screen -r [session name]         |                  |
| screen -r [session name] -X quit | 删除一个 session |

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