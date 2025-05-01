# 第一章

## 什么是Linux

## 什么是Linux内核

## 什么是Linux系统发行版
 内核无法被用户直接使用，需要配合应用程序才能被用户使用。
 在内核之上，封装系统应用程序，组合在一起就称之为Linux。
 发行版众多 Ubuntu  CentOS

 ## 什么是虚拟机
简单来说：就是一个虚拟电脑。在系统中，通过软件： 虚拟硬件，并给虚拟的硬件安装操作系统，即可得到虚拟的电脑——虚拟机。

## 为什么要使用虚拟机？
学习Linux 需要有linux系统环境。
通过虚拟机得到可以使用的系统环境

## 虚拟化技术 
 vmware workstation软件可提供虚拟机

## 下载 VMware workstation
可在github找安装包 
https://github.com/201853910/VMwareWorkstation/releases/download/16.0/VMware-workstation-full-16.2.4-20089737.exe

1. 默认下载
2. 确认在电脑中是否安装成功
（网络和Internet-高级网络设置-更改适配器选项-确认vmnet1 vmnet8是打开的状态）
快捷键Ctrl + R - 输入ncpa.cpl回车

## 下载安装Linux系统发行版 Ubuntu
https://releases.ubuntu.com/jammy/
64-bit PC AMD64 sever install image

打开VMware
1. 创建新的虚拟机- 新規仮想マシン
2. 选择典型（安装方便）- 標準
3. 选择光盘镜像文件 会默认识别杠瞎子啊的Ubuntu
4. 设置虚拟机名以及存放位置-默认即可
5. 指定虚拟硬盘磁盘容量-建议40GB
6. 可以对虚拟机做一些细微的设置 -暂时不需要 可以设置的有：  创建后开启虚拟机
   内存
   处理器
   新CD/DVD
   网络适配器
   USB控制器
   声卡
   打印机
   显示器
7. 自动安装虚拟机系统 10min左右
8. 输入用户名和密码 回车 成功
## 远程链接Linux系统-使用Rlogin
* 掌握操作系统图形化 命令行2种操作模式
* 理解为什么使用命令行操作linux系统
* 掌握使用finashell软件链接linux操作系统

## RLogin install
url: https://github.com/kmiya-culti/RLogin/releases/
1. 打开网址 程序概要-安装下载
2. 点击 从GitHub下载
3. 在顶部选择最新的版本
4. 安装完成 打开
5. 固定在桌面或者任务栏
## 启动Rlogin 连接服务器
1. 点击左上角的文件 新建- 服务器连接
2. 输入服务器名称 比如正在使用的ubuntu
3. 输入服务器ip(在Linux里通过ifconfig获取)
4. 输入用户名和密码 点击ok
5. 第一次连接服务器 会提示是否信任 点击确认
6. 更新列表 点击确认
7. 当看到cara$ -连接完成
8. 把VMware最小化 以后通过rlogin操作linux

## WSL（Windows Subsystem for Linux）
使用WSL获得ubuntun系统环境（辅助）
传统方式需要安装完整的虚拟机 如VMware（主流）
使用WSL 轻量化获得Linux系统（简单 好用 轻量化 省内存）

## 开启windows系统的WSL功能
1. windows图标右击-应用和功能
2. 程序和功能-启用或关闭Windows功能
3. 下拉-适用于linux的Windows子系统-确定
4. 重启电脑
5. WSL部署
6. 打开windows应用商店-搜索Ubuntu-获取下载
7. 点击打开-等待安装
8. 提示创建用户名和密码
9. 成功部署Ubuntu操作系统（能显示当前坂本号
10. 安装windows terminal（就是power shell）(ubuntu自带的终端窗口不好用)
11. Windows商店安装
12. 能够在power shell操作Ubuntu
13. 进入wsl里的ubuntu窗口-（箭头）设置-默认配置文件 - 点击Ubuntu -保存

## 虚拟机快照
平时使用 可能会损坏linux操作系统 重装会很麻烦
VMware虚拟机支持未虚拟机制作快照
通过快照将当前虚拟机的状态保存下来  以后可以通过快照恢复虚拟机到保存的状态

1. 首先确定虚拟机是关机状态（推荐关闭状态 效率高）
2. 找到虚拟机-右击-快照管理-拍摄快照-设置此次快照名和备注
3. 打开快照-选择自己保存的快照-提示是否要恢复-是


# 第二章

## linux目录结构
树型结构
Windows：多个盘符 c d e盘
Linux：无盘符概念 只有一个根目录 "/ " 所有文件都在下面

## linux 命令
在linux中 命令有通用格式：
command[-options][parameter]
* command：命令本身
* -option: 可选 非必填 命令的一些选项，可以通过选项控制命令的行为细节
* parameter：可选 非必填 多用于命令的指向目标
* 例
✅ 1. 查看目录内容
   * 命令：
   ls -l /home/code
   * 拆解：
   1. ls 命令本身
   2. -l 是选项，表示以列表形式详细显示
   3. /home/code 是参数，表示要查看的目录
   * 作用说明：
   以列表的形式，显示 /home/code 目录内的内容（包括权限、所有者、文件大小等信息）。

✅ 2. 查找包含关键字的代码行
  * 命令：
  grep -rn "TODO" ./src
  * 拆解：
  1. grep 命令本身
  2. -r 是选项，表示递归搜索子目录
  3. -n 是选项，表示输出匹配行的行号
  4. "TODO" 是要搜索的关键词
  5. ./src 是参数，表示从当前目录下的 src 目录开始查找
  *  作用说明：
  在 ./src 目录及其子目录下递归查找包含 "TODO" 的代码行，并显示其行号，帮助快速定位代码中的标记任务。

  ### ls命令
  作用：列出目录下的内容
  rlogin命令行输入：ls 
  显示用户honme目录：echo $HOME
   * ls命令的参数
   ✅ -a ：显示所有文件，包括隐藏文件（以.开头的文件）。
   ✅ -l ：用列表，（竖向盘列形式）详细显示文件信息（权限、大小、修改时间等）。
   ✅ -h ：以更友好的方式显示文件大小（比如用 KB、MB，而不是一堆字节数），通常和 -l 搭配使用。h需要和l一起使用
   ls 的参数和选项 是可以混合使用的 
      比如：
      * ls -alh
      * ls -lh
      * ls -a -l
      * ls -lh /
   ### cd命令（change directory）
   cd命令 + 路径 切换到指定目录下
   cd /切换到根目录
   cd命令直接执行 回到用户的HOME

   ### pwd命令（print work directory）
   查看当前目录状态 在哪个目录
   pwd命令无选项 无参数

   ### 相对路径和绝对路径
   ✅ 绝对路径（absolute path）
   从根目录 / 开始写的完整路径，像地图的完整地址。
   /home/cara/testfile 表示从系统最顶层开始，逐级进入到 testfile 文件
   
   ✅ 相对路径（relative path）
   从当前所在位置出发写的路径，就像“从我这里怎么走”。
   ../Documents 表示从当前目录的上一级进入 Documents 目录。

   ### 特殊路径符
   * . （一个点）代表当前目录，相当于“这里”。
   ./run.sh 表示执行当前目录下的 run.sh 文件。
   * ..（两个点）代表上一级目录，相当于“往回走一级”
   cd .. 表示返回到上一级目录。
   *  ~（波浪号）代表当前用户的 home 目录，相当于“我的家”。
   cd~ 回到home目录
   cd ~ 会跳转到 /home/你的用户名，比如 /home/cara。

   ### mkdir（make directory）创建目录（文件夹）
   语法： mkdir [-p] 路径
   参数必填:路径
   -p选项可选：自动创建不存在的父目录 适用于创建连续多层级的目录
   mkdir app 创建当前目录下的 app  
   mkdir -p a/b/c 连续创建 a、a/b、a/b/c 三层目录（若不存在）  

   ### touch 创建文件
   touch 路径
   
   ### cat 查看文件内容
   cat是直接将内容全部显示出来
   cat 路径

   ### more 查看文件内容
   more支持翻页 

   ### cp（copy） 复制文件或文件夹
   cp [-r] 源路径 目标路径
   参数说明：
   -r（可选）：递归复制整个目录，复制文件夹时必须加
   参数1（必填）：要复制的文件或目录（源）
   参数2（必填）：复制后的位置或名字（目标）

   ### mv （move） 移动文件或文件夹 或直接改名
   mv 源路径 目标路径
   参数说明：
   参数1（必填）：要移动或重命名的文件或目录（源）
   参数2（必填）：目标位置或新的名字（目标）
   例：
   * 把 file.txt 移动到 /home/cara/  
     mv file.txt  /home/cara/ 
   * 给文件改名（在当前目录下）  
     mv oldname.txt newname.txt
   * 将当前目录下的 app2 文件夹移到上一级目录（与当前目录同级）
     mv app2 ../ 

   ### rm （remove）删除文件文件夹 -通配符
   * rm [-r] [-f] 路径1 路径2 ... 路径n
   参数说明：
   -r（可选）：递归删除，用于删除文件夹
   -f（可选）：强制删除，不会弹出确认提示（force）
   路径1 2 ... n（必填）：要删除的文件或文件夹，多个路径之间用空格分隔
   
   * 通配符
   test* 匹配以test开头
   *test 以test结尾
   *test* 任何含test

   ### which（查看命令路径）
   which 命令名
   which cd
   which pwd
   which ls
   用来查看某个命令实际是哪个程序，以及它的路径（通常位于 /bin、/usr/bin 等）。

   ### find 命令（查找文件或目录）
   find [起始路径] [匹配条件] [操作]
   * 起始路径（必填）：从哪个目录开始查找，比如 .（当前目录）、/home 等
   * -name（匹配条件）：按名称查找，可配合通配符使用（比如 通配符*.txt）
   *  -type（可选）：指定类型，f 表示文件，d 表示目录
   * -size、-mtime、-user 等：按大小、修改时间、用户等条件过滤
   * 操作（可选）：如 -exec 后跟命令，对找到的结果进行操作（如删除）

   find 可以按名称、类型、时间等多种条件，递归查找文件或文件夹，非常强大灵活。
   1. 在当前目录及子目录中查找所有 .txt 文件 
    find . -name "*.txt"  
   2. 查找 /home/cara 目录下所有子目录  
    find /home/cara -type d 
   3. 查找并直接删除所有 .log 文件（谨慎使用）  
    find . -name "*.log" -delete   
   1. 查找所有大于 10MB 的文件
    find . -type f -size +10M  

   ### grep（查找文本内容）
   在文件里一行一行地查，找出包含关键词的行，并把这些行显示出来。
   grep [-n] 关键字 文件路径
   * 关键字（必填）：要查找的文本内容（可以是字符串、正则表达式）
   * 文件路径（必填）：在哪个文件或文件夹中查找
   * -n（可选）：显示匹配行的行号，方便定位
   例：
   1. 查找 main.py 文件中包含 "TODO" 的行      
   grep "TODO" main.py 
   2. 查找 syslog 中包含 "error" 的行，并显示行号
   grep -n "error" /var/log/syslog  

   ### wc 统计文件内容信息 文件行数单词数量
   wc [-l -w -c] 文件路径
   * -l：显示行数（lines）
   * -w：显示单词数（words）
   * -c：显示字节数（characters / bytes）
   * 文件路径（必填）：要统计的目标文件
   统计文件中的行数、单词数、字节数，可按需显示不同统计信息。
   例：
   1. 同时显示行、词、字节数  
   wc file.txt             
   2. 只显示行数 
   wc -l file.txt          
   3. 只显示单词数 
   wc -w file.txt          
   4. 只显示字节数
   wc -c file.txt   

   ### 管道符（pipe）| 管道符后面的命令，是用来处理前面命令的输出结果的。
   命令1 | 命令2
   把前一个命令的结果作为后一个命令的输入来用，实现多个命令组合处理数据。
   * 例子：ls -l | grep "txt" 从当前目录中查找以 .txt 结尾的文件
   1. 先执行 ls -l 
   2. 输出：
      -rw-r--r-- 1 cara cara  1234 Apr 29  file.txt
      -rw-r--r-- 1 cara cara  5678 Apr 29  notes.md
      -rw-r--r-- 1 cara cara  4321 Apr 29  report.txt
   3. 把这些输出交给 grep "txt" 处理
      ls -l | grep "txt"
   4. grep "txt" 只保留包含 txt 的行，结果是：
      -rw-r--r-- 1 cara cara  1234 Apr 29  file.txt
      -rw-r--r-- 1 cara cara  4321 Apr 29  report.txt
   
   ### ✅ 常用命令 + 管道符组合（适合开发者）

   * ps aux | grep nginx 
   查找正在运行的 nginx 进程
   * ls -l | grep ".sh" 
   列出当前目录中所有 .sh 脚本文件
   * cat file.txt | wc -l 
   统计 file.txt 的总行数
   * grep "error" logfile.log | wc -l  
   查找并统计日志中包含 "error" 的行数
   * find . -name "*.py" | wc -l  
   统计当前目录下 .py 文件的数量
   * du -sh * | sort -h
   查看当前目录下每个文件/文件夹的大小，并按大小排序
   * ls | sort
   将文件名按字典序排序
   * cat file.txt | sort | uniq 
   对文件内容排序后去重（常用于清洗数据）
   * df -h | grep "/dev"
   查看真实设备的磁盘使用情况
   * ss -tuln | grep 80 
   查看监听 80 端口的服务（适用于新系统）
   * history | grep git 
   查找历史命令中使用过的 git 命令

   ### echo 在命令行输出指定内容
   将指定的内容输出到终端（打印出来），常用于测试、提示信息、查看变量值等。
   echo 输出内容
   echo pwd 输出结果pwd
   echo'pwd' 输出结果 当前路径/home/cara
   ''使用这个包裹起来 将作为命令去执行

   ### 重定向符> >> （把输出写入文件）
   将命令的输出写入到文件中，代替默认的终端显示。
   可用于保存结果、生成日志、追加内容等。
   * ** > 覆盖写入 **
   将内容写入文件，如果文件已存在会覆盖原内容。
   把 Hello 写入 hello.txt，原内容会被清除
   * 例子：hello.txt 内容为hello
   * echo "abc" > hello.txt  # 把abc写入 hello.txt，原内容会被清除
   cat  hello.txt 
   现在这个文件结果是abc
   * ** >> 追加写入 **
   echo "abc" >> hello.txt # 把 abc添加到 hello.txt 的末尾
   cat  hello.txt 
   现在这个文件结果是hello abc

   ### tail（查看文件最后几行内容）
   查看文件尾部的内容，常用于查看最新日志、输出结果等。
   快速查看文件的末尾几行内容，适合用来看“最新”的数据。
   tail [-f -n 行数] 路径
   -f 表示持续跟踪文件的最新的更改（要想停止 ctrl c 就可以强制停止跟踪）
   -n 指定显示的行数 默认显示最后10行

   tail test.txt
   tail -n 15 test.txt
## vi vm编辑器
vi vim  visualface的简称 
vi 是 Linux 中最经典的文本编辑器，几乎所有发行版都内建支持。

是一个在终端中使用的“纯键盘操作”的文本编辑器。

不像你平时用的图形化编辑器（如 VS Code、记事本），vim 没有鼠标，全靠键盘！

它是程序员、系统管理员在 Linux 终端下常用的工具之一，很多服务器只有终端，没有图形界面，这时 vim 就是必备技能。

vim 是 vi 的增强版本，即 Vi IMproved，完全兼容 vi，功能更强大。
支持语法高亮、代码缩进、查找替换、Shell 脚本编辑等高级功能。
vim = vi + 更多功能，是程序员常用的终端文本编辑器。


vi vim三种工作模式
| 模式名称       | 含义/用途                                         |     常用操作键                       |
|----------------|------------------------------------------------- |----------------------------------|
| **命令模式**   | 默认进入模式，用于移动光标、复制粘贴、删除等         | `dd` 删除行，`yy` 复制行，`p` 粘贴 |
| **插入模式**   | 用于实际输入文本内容                               | `i` 进入插入，`a` 追加，`o` 新开一行 |
| **末行模式**   | 输入命令（保存、退出、查找替换等）                  | `:w` 保存，`:q` 退出，`:wq` 保存退出，`:q!` 强退 |

* 模式切换图解（逻辑记忆）：
打开文件后 = 命令模式
按 i/a/o 等 = 进入插入模式
按 Esc     = 回到命令模式
按 :       = 进入末行模式

作为入门者，只学这6个点
1. 如何打开文件
vim 文件名
🔹 如果文件不存在，会新建一个
🔹 一打开就是“命令模式”

2. 如何输入文字（进入插入模式）
   在打开后的界面，按下：
   i → 在光标前插入文字
   a → 在光标后插入文字
   o → 新开一行输入
📌 按了上面任意一个，就能开始打字了（像写文本文档一样）

3. 如何退出输入（回到命令模式）
按下 Esc 键
屏幕右下角没反应，就是正常的

4. 如何保存和退出（末行模式）
从“命令模式”按下冒号 :，进入末行命令：
| 命令       | 含义             |
|------------|------------------|
| `:w`       | 保存（write）     |
| `:q`       | 退出（quit）      |
| `:wq`      | 保存并退出        |
| `:q!`      | 不保存强制退出    |

5. 如何删除、复制、粘贴（在命令模式下）
| 操作       | 快捷键           |
|------------|------------------|
| 删除一行   | `dd`             |
| 复制一行   | `yy`             |
| 粘贴一行   | `p`              |

6. 如何快速移动
| 快捷键       | 含义             |
|--------------|------------------|
| `gg`         | 跳到文件开头      |
| `G`          | 跳到文件结尾      |
| `/关键字`     | 查找文字          |
| `n`          | 查找下一个        |

# 第三章
## root用户（超级管理员）
root 是 Linux 系统中的超级管理员，权限最高，可以修改系统的任何部分。
类似 Windows 的「Administrator」，但更强大也更危险。
✅ 如何执行 root 权限操作（推荐用法）：
🔹 用 sudo 临时提权（推荐方式）：
sudo 命令
sudo mkdir /test01
需要输入当前用户的密码，不是 root 密码。

### su命令（switch user，切换用户 部建议用 ）
su 是切换到其他用户的身份（默认是切换到 root 用户）
su - [用户名]
用户名（可选）：要切换到的目标用户，不写默认是 root
-（可选）：表示切换后加载目标用户的完整环境变量（更安全，推荐使用）
切换用户后 可以通过exit命令退回上一个用户 快捷键是ctrl d

* su   切换为 root 用户，需输入 root 密码  
* su -  切换为 root 用户并加载 root 的环境（推荐）  
* su - cara  切换为 cara 用户并加载其环境  

### sudo命令（superuser do，以超级权限执行命令）
临时以 root 权限运行某个命令，而不需要切换用户身份。
sudo 命令
命令（必填）：你希望以 root 权限执行的实际命令
密码：第一次使用时会提示输入当前用户的登录密码（不是 root 密码）
例：
* sudo mkdir test 创建系统目录需要 root 权限  
* sudo apt update更新系统软件包列表  
* sudo rm -rf /var/log/temp.log 强制删除系统日志文件

## 用户 用户组
### 用户组管理
以下命令需要root用户执行
* 创建用户组
   groupadd 用户组名
* 删除用户组
   groupdel 用户组名

### 用户管理
以下命令需要root用户执行
* 创建用户
   useradd [-g 用户组] [-d 主目录] 用户名
   -g：指定用户的主用户组
   -d：指定用户的 home 目录路径
   
   useradd -g developers -d /home/zhangsan zhangsan
   创建一个用户名为 zhangsan 的用户，主组为 developers，home 目录为 /home/zhangsan

* 删除用户
   userdel[-r] 用户名
   -r：删除用户的同时，连同其 home 目录一并删除
   userdel -r zhangsan

* 查看用户所属的组
   id[用户名]
   不加用户名时，查看当前登录用户所属的 UID、GID、附属组等信息
   加用户名可查看指定用户的信息

   id   看当前用户所属的组  
   id zhangsan  查看 zhangsan 用户的组信息

* 修改用户所属的组
   usermod -aG用户组 用户名
   将指定用户加入指定的用户组
   
   -aG 表示追加附属组，a（append）是必须的，否则会覆盖现有组
   用于将某个用户加入指定组，但不更改主组 

   usermod -aG docker zhangsan
   把用户 zhangsan 添加到 docker 组中

   ✅ 常见用户管理命令实际例子
以下命令需要使用 sudo 提权执行。
🔹 创建一个新用户，指定主组和 home 目录，并设置密码
useradd -g developers -d /home/zhangsan zhangsan
passwd zhangsan
创建用户 zhangsan，主组为 developers，home 目录为 /home/zhangsan，然后为其设置登录密码。

🔹 把用户加入 sudo 权限组
usermod -aG sudo zhangsan
追加 zhangsan 用户到 sudo 组，使其具备管理员权限（需要重新登录生效）。

🔹 查看用户的组信息
id zhangsan
显示 zhangsan 用户的 UID、主组和附属组，确认是否在 sudo 或 docker 等组中。

🔹 删除用户及其 home 目录
userdel -r testuser
删除 testuser 用户，并一并删除其 /home/testuser 目录。

### getent命令（获取系统数据库信息）
🔹 用于查询用户信息：
getent passwd 用户名
从 /etc/passwd 或系统用户数据库中查询指定用户的信息（如果不加用户名，则列出所有用户）

getent passwd
列出所有本地系统用户（和 cat /etc/passwd 类似）

getent passwd zhangsan
查询 zhangsan 用户的详细信息，包括 UID、主组、home 目录、登录 shell 等

getent group 
查询当前系统有哪些组

## 认知权限信息
通过ls -1可以以列表形式查看内容 并显示权限信息
| 符号 | 含义         |
|------|--------------|
| `r`  | read（读）    |
| `w`  | write（写）   |
| `x`  | execute（执行） |
| `-`  | 无该权限      |

### chmod命令 修改文件文件夹的权限信息
chmod [-R] 权限设置 文件或目录
-R 对文件夹内的全部内容（文件夹内的各种文件）应用同样的操作
权限设置：可以使用数字法或符号法设置权限（初学推荐数字法）

### chown 修改文件文件夹的所属用户和用户组
chown [-R] 用户[:用户组] 文件或目录
-R（可选）：递归修改，作用于目录及其所有子文件/子目录
用户：新拥有者（必填）
用户组：新所属组（可选）
例子：
chown zhangsan file.txt
把 file.txt 的拥有者改为 zhangsan，组不变

chown zhangsan:developers file.txt
把 file.txt 的拥有者改为 zhangsan，用户组改为 developers

chown -R zhangsan /home/zhangsan
递归修改 /home/zhangsan 目录及其中所有内容的拥有者为 zhangsan










