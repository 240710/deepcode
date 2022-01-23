# day6

## Linux

###常见发行版

Linux 的发行版说简单点就是将 Linux 内核与应用软件做一个打包。

![img](https://www.runoob.com/wp-content/uploads/2014/06/1511849829609658.jpg)

目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS 等

Linux是一个开源的内核，而发行版其实就是对内核进行不一样的改变和打包，就像chrome的内核

###Linux系统操作

#### 帮助命令

在 Linux 环境中，如果遇到困难，可以使用帮助命令来取得帮助。

常见的帮助命令有：man 命令、help 命令、info 命令

+ **man**

man 命令是 Linux 系统中在线软件文档的一种普遍的形式，其内容包括计算机程序（包括库和系统调用）、正式的标准和惯例，抽象的概念等。**man 工具是显示系统手册页中的内容，也就是一本电子版的字典，这些内容大多数都是对命令的解释信息，还有一些相关的描述，通过查看系统文档中的 man 还可以得到程序的更多相关信息和 Linux 的更多特性。**

**用来获得某个命令的说明和使用方式的详细介绍。**

**man 命令名**为其使用时的格式

man 手册的内容很多，涉及了 Linux 使用过程中的方方面面，为了便于查找，man 手册被进行了分册（分区段）处理，手册通常被分为以下9个区段：

1	Standard commands （标准命令）
2	System calls （系统调用）
3	Library functions （库函数）
4	Special devices （设备说明）
5	File formats （文件格式）
6	Games and toys （游戏和娱乐）
7	Miscellaneous （杂项）
8	Administrative Commands （系统管理命令和守护进程）
9	other（其他，用来存放内核例行程序的文档）如要查看相应区段的内容，就在 man 后面加上相应区段的数字即可。

例：![img](https://img-blog.csdn.net/2018070316114148?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTE4MTU0MDQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

+ **help**

**help 命令是用于显示 shell 内建命令的简要帮助信息，帮助信息中显示有该命令的简要说明以及一些参数的使用以及说明。**

![img](https://img-blog.csdn.net/20180703162920311?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTE4MTU0MDQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

+ **info**

如果觉得 man 显示的信息都还不够，满足不了需求，那么可使用 info 命令来获取帮助。

**man 和 info 就像两个集合，它们有一个交集部分，但与 man 相比，info 工具可显示更完整的信息。**

#### 文件与目录的操作

| 命令    | 含义                                                      |
| ------- | --------------------------------------------------------- |
| cd      | 变换目录（change directory）                              |
| pwd     | 显示当前目录                                              |
| mkdir   | 建立一个新的目录                                          |
| rmdir   | 删除一个空的目录                                          |
| rm  -rf | 删除，-r代表递归，比如删除文件夹下所有文件，-f ，强制删除 |

其他一些必备知识：

| 符号  | 含义                                           |
| ----- | ---------------------------------------------- |
| .     | 代表当前目录                                   |
| ..    | 代表上一层目录                                 |
| ~     | 代表目前用户身份的家目录                       |
| ~yuan | 代表yuan这个用户的家目录（yuan是一个账户名称） |

##### **复制，删除移动命令（cp,rm,mv）**

cp命令用来将一个或多个源文件或者源目录复制到指定的文件或目录中。

语法：

1.cp [OPTION]… [-T] SOURCE DEST

2.cp [OPTION]… SOURCE… DIRECTORY

3.cp [OPTION]… -t DIRECTORY SOURCE… 

常用选项

选项（OPTION）							含义
-r,-R				-recursive，递归复制目录及内部的所有内容
-a					-archive,归档，类似 -dR -perserve=all
-v					-verbose,显示拷贝的详情信息（进度）
-u					-update,只有源文件（source）比目的(dest)						或者目的文件不存在才会进行复制。
-f						-force强制拷贝
-p					连同属性一起拷贝
-s						复制成为符号链接文件 (symbolic link)，亦						（快捷方式）档案；
-i						若目标文件(destination)已经存在时，在覆							盖时会先询问动作的进行(常用)

-d							若来源文件为链接文件的属性(link file)，								则复制链接文件属性而非档案本身。

**复制整个文件夹到指定目录：**

把整个 /etc/文件夹复制到 /mnt目录下，发现用cp命令是不可以直接复制目录的，得使用递归参数（-r）复制目录以及目录下的所有文件。

> 使用命令：cp -rf /etc/  /mnt 

![img](https://img-blog.csdn.net/20180921151850983?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2MjQzOTQy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 注意：当新复制一个文件就是相当于是新建一个文件，从创建时间可以看的出来，做个实验：

先将,/mnt的东西清空。

![img](https://img-blog.csdn.net/2018092210131977?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2MjQzOTQy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

然后把，/etc/services文件夹复制到 ，/mnt

![img](https://img-blog.csdn.net/20180922101744690?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2MjQzOTQy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

如果你想拷贝的时候连同属性信息一同拷贝，怎么做呢？（注意，先删除,/mnt/services再下一步）

（也可以使用，-a选项）

![img](https://img-blog.csdn.net/2018092210242193?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2MjQzOTQy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

---

 mv (移动档案与目录，或更名)：将源文件重命名为目标文件， 或将源文件移动至指定目录 。

语法：mv [OPTION ]     SOURCE  DEST

常用选项：

| 选项（OPTION） | 含义                                                         |
| -------------- | ------------------------------------------------------------ |
| -f             | --force : 覆盖前不询问                                       |
| -i             | --interactive : 覆盖前询问                                   |
| -u             | --update : 只在源文件文件比目标文件新，或目标文件不存在时才进行移动 |
| -v             | --verbose : 详细显示进行的步骤                               |
|                |                                                              |
|                |                                                              |

例子：mv  [选项]    /PATH1/aa     /PATH2/bb  把PATH1的aa文件夹剪切到PATH2的bb下，如果没有bb文件夹，则创建一个bb文件夹。

---



删除：rm命令用于删除[Linux](https://so.csdn.net/so/search?q=Linux&spm=1001.2101.3001.7020)系统中的文件或目录。

语法

rm  [OPTION] .... FILE

常用选项

| 选项（OPTION） | 含义                                               |
| -------------- | -------------------------------------------------- |
| -f             | --force 强制删除，忽略不存在的文件（不提示）       |
| -i             | --interactive 交互模式删除文件，删除文件前给出提示 |
| -r,-R          | 递归的删除目录下面文件以及子目录下文件             |
| -v             | --verbose 显示运行时详细信息                       |
|                |                                                    |

 例子：

![img](https://img-blog.csdn.net/201809221053025?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2MjQzOTQy/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

---

##### 查看文件内容(cat,tac,more,less,head,tail,od)

命令							含义

 cat                      由第一行开始显示档案内容
 tac                      从最后一行开始显示，可以看出 tac 是 cat 							倒着写！
  nl                      显示的时候，顺道输出行号！
  more                一页一页的显示档案内容
  head                只看头几行
  tail                    只看尾几行
  od                      以二进制的方式读取档案内容！

 less 与 more 类似，但是比 more 更好的是，他可以往前翻页！

**使用方式与特征：**

1. cat 和 tac使用方法：cat  [选项] + 文件名 ,tac  [选项] + 文件名

2. more的用法：more + 文件名 ，特点：可以向阅览电子书一样，一页一页显示。缺点：只能往后翻，不能往前。

3. .less，的用法：less + 文件名，继承了more的特点之外，还可以往前翻，使用更多的快捷键。

   比如查看/etc/services文件，这个篇幅很长，使用less试一下

4. head和tail命令用法：heda  -数字 文件名，或者 tail -数字 文件名
5. .od命令的使用：od + [选项] + 文件名

---

##### 新建文档（touch）

语法：touch   [选项]...  文件....

常用选项：

| 选项（OPTION） | 含义                                                         |
| -------------- | ------------------------------------------------------------ |
| -a             | 仅修订access time                                            |
| -c             | 仅修改档案时间                                               |
| -d             | 直接加上想要修订的日期，而不是使用当前系统时间，也可以使用 --date ==日期或时间 |
| -m             | 仅修改mtine                                                  |
| -t             | 后面可以直接想要修订的时间，格式为~[YYMMDDhhmm](年，月，日，时，分)~ |

---

#### 打包和压缩

打包是指将多个文件或者目录放在一起，形成一个总的包，这样便于保存和传输，但是大小是没有变化的，压缩是指将一个或者多个大文件或者目录通过压缩算法使文件的体积变小以达到压缩的目的，可以节省存储空间，在压缩的时候通常是先打包再压缩；

##### tar命令

tar命令参数前面加”-"与不加“-”的区别：

tar命令参数前面加不加“-”执行命令的结果是没有区别的，区别只要是在于linux风格方面，加“-”属于System V风格，不加“-”属于BSD风格，所以在使用tar命令的时候它的参数加不加“-”结果是一样的，看个人的使用方式；

常用参数：
-z	                 是否同时具有gz属性
-j	                  是否同时具有bz2属性
-J	                  是否同时具有xz属性
-x	                 解压缩、提取打包的内容
-t	                  查看压缩包内容
-c	                  建立一个压缩，打包文档
-C	                切换到指定目录，表示指定解压缩包的内容和  						打包的内容存放的目录
-v	                 显示压缩或者打包的内容
-f	                  使用文件名，在f后面要接压缩后的文件的名						字，只要用到tar命令，-f选项是必须要用						的，-f参数在使用的时候一定排在其他参数的						后面，在最右边
-p					保留备份数据的原本权限与属性，常用于备份					（-c）重要的配置文件
-P					保留绝对路径

一、打包
实例：

a.将/root/下的ceshi.txt文件和anaconda-ks.cfg文件和time.sh文件打包为一个文件，名称为“jihe.tar”：

![img](https://img-blog.csdnimg.cn/20190816180609377.png)

b.查看jihe.tar文件的内容：

![img](https://img-blog.csdnimg.cn/20190816180639407.png)

c.提取jihe.tar文件的内容到/opt目录下：

![img](https://img-blog.csdnimg.cn/20190816180651949.png)

如果不用“-C”指定目录则会提取内容到当前目录
二、压缩
linux主要有三种压缩方式：
1.gzip：是公认的压缩这速度最快，压缩大文件的时候与其他的压缩方式相比更加明显，历史最久，应用最广泛的压缩方式
2.bzip：压缩形成的文件小，但是可用性不如gzip
3.xz：是最新的压缩方式，可以自动提供最佳的压缩率

建议的压缩的时候标明后缀：

| 参数 | 作用              | 命名方式       |
| ---- | ----------------- | -------------- |
| -z   | 用于gzip压缩方式  | 文件名.tar.gz  |
| -j   | 用于bzip2压缩方式 | 文件名.tar.bz2 |
| -J   | 用于xz压缩方式    | 文件名.tar.xz  |


实例：用不同的压缩方式压缩/root/目录下的Golden.apk文件

先查看Golden.apk文件的大小：

![img](https://img-blog.csdnimg.cn/20190816181224608.png)

可以看到Golden.apk文件的大小为187M

a.用gzip压缩方式将Golden.apk文件压缩为Golden.apk.tar.gz文件：

![img](https://img-blog.csdnimg.cn/20190816181246647.png)

b.用bzip2的压缩方式将Golden.apk文件压缩为Golden.apk.tar.bz2文件：

![img](https://img-blog.csdnimg.cn/20190816181310718.png)

从上图可以看出红色方框内有报错，这个报错的原因是缺少bzip2的包，需要安装一个bzip2软件包

![img](https://img-blog.csdnimg.cn/20190816181329465.png)

安装完成之后再重新压缩：

![img](https://img-blog.csdnimg.cn/20190816181345828.png)

在压缩的过程中，我们可以发现：

压缩速度：gz > bz2 > xz
压缩率：xz > bz2 > gz


![img](https://img-blog.csdnimg.cn/20190816181433698.png)

三、解压
先删除/root/目录下的Golden.apk文件：

![img](https://img-blog.csdnimg.cn/20190816181508837.png)

tar命令式一个很聪明的命令，我们在解压的时候不需要指明自己压缩的方式它会自己选择跟压缩方式对应的方式去解压，例：

a.将Golden.apk.tar.gz解压到当前目录：

![img](https://img-blog.csdnimg.cn/20190816181636162.png)

在解压gz压缩方式压缩文件的时候并不需要加上-z，直接用参数-xf即可，另外两种压缩方式在解压的时候一样，因为tar命令会自动选择，解压之后压缩文件还在，如果不指定解压出来的文件保存在哪里，那么会直接解压在当前目录

b.指定解压出来的文件保存的目录，将Golden.apk.tar.bz2文件解压在/opt/目录下：

![img](https://img-blog.csdnimg.cn/20190816181700951.png)

---

#### vim编辑器的用法

**vim编辑器有三种模式**
**命令模式**：对文本进行复制、粘贴、删除、撤销等【默认进入命令模式】
**输入模式**：输入文本内容
**末行模式**：保存、退出文档，以及设置编辑环境
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222104523147.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNjUyMjA5OQ==,size_16,color_FFFFFF,t_70)

一、命令模式的使用
模式切换：从输入模式或者末行模式可以通过Esc键回到命令模式。

| 命令 | 作用                      |
| ---- | ------------------------- |
| dd   | 删除(剪切)所在行          |
| ndd  | 删除(剪切)所在行开始的n行 |
| yy   | 复制所在行                |
| nyy  | 复制所在行开始的n行       |
| p    | 粘贴到光标所在行的下一行  |

二、输入模式的使用
模式切换：在命令模式下可以使用a、i、o进入输入模式

| 按键 | 初始输入位置                   |
| ---- | ------------------------------ |
| `a`  | 在光标的右边进行输入           |
| `i`  | 在光标位置进行输入             |
| `o`  | 在光标所在行的下一行头进行输入 |

其实无论哪种方式，都差不多的，可以通过使用上下左右键进行调整。
模式切换：在命令模式下，可以使用:进入末行模式

命令					作用
:w						保存
:q						退出
:w!					强制保存
:q!					强制退出，不保存
:wq!				强制保存退出
:set nu				显示行号
:set nonu			不显示行号
:nohl				去除文本中的高亮
:n							跳转到第n行
:s/str1/str2/		将所在行的第一个str1换成str2
:s/str1/str2/g		将所在行的所有str1换成str2
:%s/str1/str1/g	将全文的所有的str1换成str2
/str						在全文中从上到下找str
?str								在全文中从下到上找str
**在这些命令里，最常用的就是:wq!，当编辑完一个文本后，使用该命令即可强制保存退出。**

四、多窗口多文件的切换
同时打开多个文件
vim file1.txt file2.txt file3.txt

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200223181552214.png)

先打开一个文件，再打开另一个文件
vim file1.txt
:e file2.txt

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200223183040484.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNjUyMjA5OQ==,size_16,color_FFFFFF,t_70)

查看当前打开哪些文件,第一列是文件的序号
:ls

![在这里插入图片描述](https://img-blog.csdnimg.cn/202002231817582.png)

文件切换

| 命令  | 作用             |
| ----- | ---------------- |
| `:bx` | 切换到第x个文件  |
| `:bn` | 切换到下一个文件 |
| `:bp` | 切换到上一个文件 |

切分窗口
命令					作用
:sp				水平切分窗口
:vsplit				垂直切分窗口

窗口关闭和切换


| 命令       | 作用                           |
| ---------- | ------------------------------ |
| `:close`   | 关闭当前窗口，建议先保存再关闭 |
| `:only`    | 仅保留当前窗口，其他窗口关闭   |
| `Ctrl+ww`  | 切换到下一个窗口               |
| `Ctrl+w h` | 切换到**左**边的窗口           |
| `Ctrl+w j` | 切换到**下**面的窗口           |
| `Ctrl+w k` | 切换到**上**面的窗口           |
| `Ctrl+w l` | 切换到**右**边的窗口           |

---

#### 用户权限管理

Linux系统是一个多用户多任务的分时操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。

每个用户账号都拥有一个唯一的用户名和各自的口令。

用户在登录时键入正确的用户名和口令后，就能够进入系统和自己的主目录。

实现用户账号的管理，要完成的工作主要有如下几个方面：

+ 用户账号的添加、删除与修改。
+ 用户口令的管理。
+ 用户组的管理。

##### root用户和普通用户

**root用户可以在Linux系统上做任何操作，权限没有收到任何限制**。一般需要root权限的任务包括：移动文件或者文件夹in或者out of 系统目录，复制文件到系统目录，赋予或者收回用户权限，系统维护和安装一些应用程序，例如：安装RPM格式的软件通常需要root权限，因为需要写一些信息到系统目录。还有一个需要注意的就是，对于小于1024端口的知名端口，只有root用户才可以有权限侦听，如果应用程序需要侦听小于1024的端口，可以采用临时提权，侦听端口之后，再收回权限的方式进行。但是**如果一直使用root运行应用程序，将会很危险，**

普通用户是根据他所在的组的权限指定的一些操作，但是，一般来说，会拒绝使用一些会影响他的home目录之外的命令

**用户可以被允许使用sudo命令，临时赋予root权限。Unix系列的系统默认是组织一般用户访问系统的关键部分和其他用户的文件和文件夹。**

关于sudo之后可以执行哪些命令，可以通过编辑 /etc/sudoers文件：

要为某个用户提供特权，使其可以使用sudo执行所有命令，在配置文件中加入：

**用户名   ALL=(ALL) ALL**

**只为用户启用部分特权：**

用户名 主机名=/sbin/halt,/sbin/poweroff,/sbin/reboot

还可以通过/etc/sudoers设置超时机制等。

/etc/sudoers文件默认是只有root用户才可以修改和访问的，如果不小心修改了/etc/sudoers的访问权限，要记住立刻恢复。

---



#####**用户账号的管理**

添加新的用户账号使用useradd命令，其语法如下：

~~~
useradd 选项 用户名
~~~

参数说明：

+ 选项:

  -c comment 指定一段注释性描述。

  -d 目录 指定用户主目录，如果此目录不存在，则同时使用-m选项，可以创建主目录。

  -g 用户组 指定用户所属的用户组。

  -G 用户组，用户组 指定用户所属的附加组。

  -s Shell文件 指定用户的登录Shell。

  -u 用户号 指定用户的用户号，如果同时有-o选项，则可以重复使用其他用户的标识号。

+ 用户名:

  指定新账号的登录名。

**实例1**

```
# useradd –d  /home/sam -m sam
```

此命令创建了一个用户sam，其中-d和-m选项用来为登录名sam产生一个主目录 /home/sam（/home为默认的用户主目录所在的父目录）。

**删除帐号**

如果一个用户的账号不再使用，可以从系统中删除。删除用户账号就是要将/etc/passwd等系统文件中的该用户记录删除，必要时还删除用户的主目录。

删除一个已有的用户账号使用`userdel`命令，其格式如下：

```
userdel 选项 用户名
```

常用的选项是 **-r**，它的作用是把用户的主目录一起删除。

例如：

```
# userdel -r sam
```

**修改帐号**

修改用户账号就是根据实际情况更改用户的有关属性，如用户号、主目录、用户组、登录Shell等。

修改已有用户的信息使用`usermod`命令，其格式如下：

```
usermod 选项 用户名
```

常用的选项包括`-c, -d, -m, -g, -G, -s, -u以及-o等`，这些选项的意义与`useradd`命令中的选项一样，可以为用户指定新的资源值。

另外，有些系统可以使用选项：-l 新用户名

这个选项指定一个新的账号，即将原来的用户名改为新的用户名。

例如：

```
# usermod -s /bin/ksh -d /home/z –g developer sam
```

此命令将用户sam的登录Shell修改为ksh，主目录改为/home/z，用户组改为developer。****

**用户口令的管理**

用户管理的一项重要内容是用户口令的管理。用户账号刚创建时没有口令，但是被系统锁定，无法使用，必须为其指定口令后才可以使用，即使是指定空口令。

指定和修改用户口令的Shell命令是`passwd`。超级用户可以为自己和其他用户指定口令，普通用户只能用它修改自己的口令。命令的格式为：

```
passwd 选项 用户名
```

可使用的选项：

+ -l 锁定口令，即禁用账号。
+ -u 口令解锁。
+ -d 使账号无口令。
+ -f 强迫用户下次登录时修改口令。

如果默认用户名，则修改当前用户的口令。

例如，假设当前用户是sam，则下面的命令修改该用户自己的口令：

```
$ passwd 
Old password:****** 
New password:******* 
Re-enter new password:*******
```

```
# passwd -d sam
```

此命令将用户 sam 的口令删除，这样用户 sam 下一次登录时，系统就不再允许该用户登录了。

passwd 命令还可以用 -l(lock) 选项锁定某一用户，使其不能登录，例如：

```
# passwd -l sam
```

##### 用户组的管理

每个用户都有一个用户组，系统可以对一个用户组中的所有用户进行集中管理。不同Linux 系统对用户组的规定有所不同，如Linux下的用户属于与它同名的用户组，这个用户组在创建用户时同时创建。

用户组的管理涉及用户组的添加、删除和修改。组的增加、删除和修改实际上就是对/etc/group文件的更新。

**增加一个新的用户组使用groupadd命令。其格式如下：**

```
groupadd 选项 用户组
```

可以使用的选项有：

+ -g GID 指定新用户组的组标识号（GID）。
+ -o 一般与-g选项同时使用，表示新用户组的GID可以与系统已有用户组的GID相同。

**实例1：**

```
# groupadd group1
```

此命令向系统中增加了一个新组group1，新组的组标识号是在当前已有的最大组标识号的基础上加1。

**如果要删除一个已有的用户组，使用groupdel命令，其格式如下：**

```
groupdel 用户组
```

**例如：**

```
# groupdel group1
```

**修改用户组的属性使用groupmod命令。其语法如下：**

```
groupmod 选项 用户组
```

常用的选项有：

+ -g GID 为用户组指定新的组标识号。
+ -o 与-g选项同时使用，用户组的新GID可以与系统已有用户组的GID相同。
+ -n新用户组 将用户组的名字改为新名字

**实例1：**

```
# groupmod -g 102 group2
```

此命令将组group2的组标识号修改为102。

**如果一个用户同时属于多个用户组，那么用户可以在用户组之间切换，以便具有其他用户组的权限。**

用户可以在登录后，使用命令newgrp切换到其他用户组，这个命令的参数就是目的用户组。例如：

```
$ newgrp root
```

##### 和用户有关的系统文件

完成用户管理的工作有许多种方法，但是每一种方法实际上都是对有关的系统文件进行修改。

与用户和用户组相关的信息都存放在一些系统文件中，这些文件包括/etc/passwd, /etc/shadow, /etc/group等。

**/etc/passwd文件是用户管理工作涉及的最重要的一个文件。**

```
＃ cat /etc/passwd

root:x:0:0:Superuser:/:
daemon:x:1:1:System daemons:/etc:
bin:x:2:2:Owner of system commands:/bin:
sys:x:3:3:Owner of system files:/usr/sys:
adm:x:4:4:System accounting:/usr/adm:
uucp:x:5:5:UUCP administrator:/usr/lib/uucp:
auth:x:7:21:Authentication administrator:/tcb/files/auth:
cron:x:9:16:Cron daemon:/usr/spool/cron:
listen:x:37:4:Network daemon:/usr/net/nls:
lp:x:71:18:Printer administrator:/usr/spool/lp:
sam:x:200:50:Sam san:/home/sam:/bin/sh
```

从上面的例子我们可以看到，/etc/passwd中一行记录对应着一个用户，每行记录又被冒号(:)分隔为7个字段，其格式和具体含义如下：

```
用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录Shell
```

+ "用户名"是代表用户账号的字符串。
+ “口令”一些系统中，存放着加密后的用户口令字。
+ “用户标识号”是一个整数，系统内部用它来标识用户。
+ “组标识号”字段记录的是用户所属的用户组。
+ “注释性描述”字段记录着用户的一些个人情况。
+ “主目录”，也就是用户的起始工作目录。
+ )用户登录后，要启动一个进程，负责将用户的操作传给内核，这个进程是用户登录到系统后运行的命令解释器或某个特定的程序，即Shell。





---



### 系统管理

####软件安装与更新

 **一、在线安装**

**软件管理中心安装。（ubuntu）**1）更新源sudo apt-get update2）打开软件中心，搜索你要安装的软件，双击安装即可。

**命令行安装方式**

​    1）更新命令：apt-get update

​    2）查找你要安装的软件，apt-cache search “软件名”

​    3）apt-get install 软件名

   **二、线下安装**

​    线下安装就是要把软件下载到本地去安装。一般我们下载的文件后缀名都是zip、tar.gz等压缩包，解压后会看到rpm、bin、deb、run之类扩展名文件。很多软件都会提供不同LINUX版本的安装格式，可以根据自己的系统下载不同扩展名的软件。

   **1、rpm安装包：**这时一款老牌的安装格式,是红帽创建的安装格式，现在已成为一种标准，常用在opensuse/turbo/redhat版本），安装方法**rpm -ivh 软件名.rpm** （如果只是安装一个i参数就够了，如果还要看安装进度和软件信息就加个vh)

  **2.yum安装包**

(1).下载yum安装包并解压

wget http://yum.baseurl.org/download/3.2/yum-3.2.28.tar.gz
tar xvf yum-3.2.28.tar.gz

(2).进入yum-3.2.28文件夹中进行安装，执行安装指令

cd yum-3.2.28
sudo apt install yum

(3).更新版本

yum check-update
yum update
yum clean all
**3.源码安装**

（1）获取源码
将软件的源码下载至/usr/local/，并解压。
（2）查看INSTALL与README文件
解压后查看INSTALL与README文件，这两个文件中详细介绍了本软件的安装方法和注意事项。
（3）创建Makefile文件
执行configure命令，生成Makefile文件。
（4）编译
执行make clean;make命令将源码编译成二进制文件。
make clean命令用来清除上一次编译生成的目标文件。这个步骤可有可无，但为了确保编译的成功，还是加上为好。防止由于软件中含有残留的目标文件导致编译失败。
（5）安装
执行make install命令将上一步编译好的二进制文件安装到指定的目录中去。

#### 磁盘管理

inux 磁盘管理好坏直接关系到整个系统的性能问题。

Linux 磁盘管理常用三个命令为 **df**、**du** 和 **fdisk**。

+ **df**（英文全称：disk full）：列出文件系统的整体磁盘使用量

  语法：

  ```
  df [-ahikHTm] [目录或文件名]
  ```

  选项与参数：

  -a ：列出所有的文件系统，包括系统特有的 /proc 等文件系统；

  -k ：以 KBytes 的容量显示各文件系统；

  -m ：以 MBytes 的容量显示各文件系统；

  -h ：以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示；

  -H ：以 M=1000K 取代 M=1024K 的进位方式；

  -T ：显示文件系统类型, 连同该 partition 的 filesystem 名称 (例如 ext3) 也列出；

  -i ：不用硬盘容量，而以 inode 的数量来显示

  **实例 1**

  将系统内所有的文件系统列出来！

  ```
  [root@www ~]# df
  Filesystem      1K-blocks      Used Available Use% Mounted on
  /dev/hdc2         9920624   3823112   5585444  41% /
  /dev/hdc3         4956316    141376   4559108   4% /home
  /dev/hdc1          101086     11126     84741  12% /boot
  tmpfs              371332         0    371332   0% /dev/shm
  ```

  在 Linux 底下如果 df 没有加任何选项，那么默认会将系统内所有的 (不含特殊内存内的文件系统与 swap) 都以 1 Kbytes 的容量来列出来！

**实例 2**

将容量结果以易读的容量格式显示出来

```
[root@www ~]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc2             9.5G  3.7G  5.4G  41% /
/dev/hdc3             4.8G  139M  4.4G   4% /home
/dev/hdc1              99M   11M   83M  12% /boot
tmpfs                 363M     0  363M   0% /dev/shm
```

**实例 3**

将系统内的所有特殊文件格式及名称都列出来

```
[root@www ~]# df -aT
Filesystem    Type 1K-blocks    Used Available Use% Mounted on
/dev/hdc2     ext3   9920624 3823112   5585444  41% /
proc          proc         0       0         0   -  /proc
sysfs        sysfs         0       0         0   -  /sys
devpts      devpts         0       0         0   -  /dev/pts
/dev/hdc3     ext3   4956316  141376   4559108   4% /home
/dev/hdc1     ext3    101086   11126     84741  12% /boot
tmpfs        tmpfs    371332       0    371332   0% /dev/shm
none   binfmt_misc         0       0         0   -  /proc/sys/fs/binfmt_misc
sunrpc  rpc_pipefs         0       0         0   -  /var/lib/nfs/rpc_pipefs
```

**实例 4**

将 /etc 底下的可用的磁盘容量以易读的容量格式显示

```
[root@www ~]# df -h /etc
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc2             9.5G  3.7G  5.4G  41% /
```

+ **du**（英文全称：disk used）：检查磁盘空间使用量

语法：

```
du [-ahskm] 文件或目录名称
```

选项与参数：

+ -a ：列出所有的文件与目录容量，因为默认仅统计目录底下的文件量而已。
+ -h ：以人们较易读的容量格式 (G/M) 显示；
+ -s ：列出总量而已，而不列出每个各别的目录占用容量；
+ -S ：不包括子目录下的总计，与 -s 有点差别。
+ -k ：以 KBytes 列出容量显示；
+ -m ：以 MBytes 列出容量显示；

**实例 1**

只列出当前目录下的所有文件夹容量（包括隐藏文件夹）:

```
[root@www ~]# du
8       ./test4     <==每个目录都会列出来
8       ./test2
....中间省略....
12      ./.gconfd   <==包括隐藏文件的目录
220     .           <==这个目录(.)所占用的总量
```

直接输入 du 没有加任何选项时，则 du 会分析当前所在目录里的子目录所占用的硬盘空间。

**实例 2**

将文件的容量也列出来

```
[root@www ~]# du -a
12      ./install.log.syslog   <==有文件的列表了
8       ./.bash_logout
8       ./test4
8       ./test2
....中间省略....
12      ./.gconfd
220     .
```

**实例 3**

检查根目录底下每个目录所占用的容量

```
[root@www ~]# du -sm /*
7       /bin
6       /boot
.....中间省略....
0       /proc
.....中间省略....
1       /tmp
3859    /usr     <==系统初期最大就是他了啦！
77      /var
```

通配符 * 来代表每个目录。

与 df 不一样的是，du 这个命令其实会直接到文件系统内去搜寻所有的文件数据。

+ **fdisk**：用于磁盘分区

语法：

```
fdisk [-l] 装置名称
```

选项与参数：

+ -l ：输出后面接的装置所有的分区内容。若仅有 fdisk -l 时， 则系统将会把整个系统内能够搜寻到的装置的分区均列出来。

**实例 1**

列出所有分区信息

```
[root@AY120919111755c246621 tmp]# fdisk -l

Disk /dev/xvda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/xvda1   *           1        2550    20480000   83  Linux
/dev/xvda2            2550        2611      490496   82  Linux swap / Solaris

Disk /dev/xvdb: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56f40944

    Device Boot      Start         End      Blocks   Id  System
/dev/xvdb2               1        2610    20964793+  83  Linux
```

**实例 2**

找出你系统中的根目录所在磁盘，并查阅该硬盘内的相关信息

```
[root@www ~]# df /            <==注意：重点在找出磁盘文件名而已
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc2              9920624   3823168   5585388  41% /

[root@www ~]# fdisk /dev/hdc  <==仔细看，不要加上数字喔！
The number of cylinders for this disk is set to 5005.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):     <==等待你的输入！
```

输入 m 后，就会看到底下这些命令介绍

```
Command (m for help): m   <== 输入 m 后，就会看到底下这些命令介绍
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition            <==删除一个partition
   l   list known partition types
   m   print this menu
   n   add a new partition           <==新增一个partition
   o   create a new empty DOS partition table
   p   print the partition table     <==在屏幕上显示分割表
   q   quit without saving changes   <==不储存离开fdisk程序
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit  <==将刚刚的动作写入分割表
   x   extra functionality (experts only)
```

离开 fdisk 时按下 `q`，那么所有的动作都不会生效！相反的， 按下`w`就是动作生效的意思。

```
Command (m for help): p  <== 这里可以输出目前磁盘的状态

Disk /dev/hdc: 41.1 GB, 41174138880 bytes        <==这个磁盘的文件名与容量
255 heads, 63 sectors/track, 5005 cylinders      <==磁头、扇区与磁柱大小
Units = cylinders of 16065 * 512 = 8225280 bytes <==每个磁柱的大小

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          13      104391   83  Linux
/dev/hdc2              14        1288    10241437+  83  Linux
/dev/hdc3            1289        1925     5116702+  83  Linux
/dev/hdc4            1926        5005    24740100    5  Extended
/dev/hdc5            1926        2052     1020096   82  Linux swap / Solaris
# 装置文件名 启动区否 开始磁柱    结束磁柱  1K大小容量 磁盘分区槽内的系统

Command (m for help): q
```

想要不储存离开吗？按下 q 就对了！不要随便按 w 啊！

使用 `p` 可以列出目前这颗磁盘的分割表信息，这个信息的上半部在显示整体磁盘的状态。

**磁盘格式化**

格式化的命令非常的简单，使用 `mkfs`（make filesystem） 命令。

语法：

```
mkfs [-t 文件系统格式] 装置文件名
```

选项与参数：

+ -t ：可以接文件系统格式，例如 ext3, ext2, vfat 等(系统有支持才会生效)

**实例 1**

查看 mkfs 支持的文件格式

```
[root@www ~]# mkfs[tab][tab]
mkfs         mkfs.cramfs  mkfs.ext2    mkfs.ext3    mkfs.msdos   mkfs.vfat
```

按下两个[tab]，会发现 mkfs 支持的文件格式如上所示。

然后就可以根据需要对所支持的文件格式进行格式化。