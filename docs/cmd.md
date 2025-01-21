---
title: "Cmd"
---

# [Cmd](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)

- `pwd`：获取当前工作路径
- `chmod 777 file.txt`：修改文件权限，三位数分别对应当前用户、用户组、所有用户。7 代表二进制 111，分别代表 rwx 读写执行权限
- `echo hello > hello.txt`：将 echo 的输出重定向到 txt 文件中
- `ls | grep hello log.txt`：在 ls 结果中找出含"hello"的项，`|`表示将 ls 程序与 grep 程序的输入输出连接起来，grep 更适合单纯的查找或匹配文本
- `awk '{print $1}' log.txt`：打印 log.txt 中每行第一个参数，awk 更适合对格式化文本进行较复杂格式处理
- `sed -n "20 p" log.txt`：打印 log.txt 第 20 行，sed 更适合编辑匹配到的文本
- `bash ./test.sh`：执行 test.sh 脚本
- `sort -g log.txt`：按照数字顺序排序
- `wc log.txt log2.txt`：word counts 结果为三个数字，分别是行数、单词数、字节数
- `sudo echo 3 > /sys/class/backlight/thinkpad_screen/brightness` 权限不足，应改为 `echo 3 | sudo tee /sys/class/backlight/thinkpad_screen/brightness`：因为 echo 并不知道 `|` 的存在，它们只知道从自己的输入输出流中进行读写。因此 shell (权限为您的当前用户) 在设置 sudo echo 前尝试打开 brightness 文件并写入，但是系统拒绝了 shell 的操作因为此时 shell 不是 sudo 根用户
- 程序进程管理
  - `CTRL-C`：发送 SIGINT 信号，终止程序
  - `CTRL-Z`：发送 SIGQUIT 信号，终止程序
  - `kill -TERM %2`：发送 SIGTERM 信号，退出 2 号进程
  - `CTRL-Z`：发送 SIGTSTP 信号，暂停程序
  - `fg`：在前台恢复暂停的程序
  - `bg`：在后台恢复暂停的程序
  - `jobs`：查看当前终端中尚未完成的任务 pid
  - `pgrep`：找出 pid
  - `%<pid>`：引用 pid
