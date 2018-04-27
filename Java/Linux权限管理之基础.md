# linux中用户的分类
无论在windows还是linux，管理员权限都是最高的权限，它对文件的修改可以说是随便的，你就是老大。对于linux而言，管理员权限就是所谓的root权限。

对于linux，用户分为3类，1. 普通用户 （系统用户、普通用户）2.管理员用户

可以想象成每一个用户都有一个账号。其中管理员用户就是root账号，用他的密码就可以登录到管理员用户。

使用`cat /etc/passwd`就可以查看当前的计算机中用户列表。
以下是我的计算机中的列表
```
//方便我就在这里面直接注释了
//格式为：
//用户名:密码：用户id：用户所在组id：备注：用户家目录：shell命令所在目录
root:x:0:0:root:/root:/bin/bash
//第一个是root用户管理员用户，UID为0
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/bin/false
systemd-network:x:101:103:systemd Network Management,,,:/run/systemd/netif:/bin/false
systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd/resolve:/bin/false
systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false
syslog:x:104:108::/home/syslog:/bin/false
_apt:x:105:65534::/nonexistent:/bin/false
messagebus:x:106:110::/var/run/dbus:/bin/false
uuidd:x:107:111::/run/uuidd:/bin/false
lightdm:x:108:114:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:109:117::/nonexistent:/bin/false
avahi-autoipd:x:110:119:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:111:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
dnsmasq:x:112:65534:dnsmasq,,,:/var/lib/misc:/bin/false
colord:x:113:123:colord colour management daemon,,,:/var/lib/colord:/bin/false
speech-dispatcher:x:114:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
hplip:x:115:7:HPLIP system user,,,:/var/run/hplip:/bin/false
kernoops:x:116:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:117:124:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:118:126:RealtimeKit,,,:/proc:/bin/false
saned:x:119:127::/var/lib/saned:/bin/false
usbmux:x:120:46:usbmux daemon,,,:/var/lib/usbmux:/bin/false
//以上为系统用户，linux为满足系统要求所内建的账号，自动创建，不能用来登录操作系统。UID为1-499
dreamer:x:1000:1000:dreamer,,,:/home/dreamer:/bin/bash
guest-iedh0z:x:999:999:访客:/tmp/guest-iedh0z:/bin/bash
//以上是普通用户，也就是我们平常使用linux所处的级别。UID在500以上。
```
在服务器上，为了安全，就不能所有的用户都拥有管理员权限！

# 基本权限的使用
## 基本权限的说明
使用`ls -l`命令，就可以查看当前目录下文件的权限详细内容。
![](https://upload-images.jianshu.io/upload_images/271046-e37dd2dd48c87d50.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所有者权限用u来表示 ，所属组权限用g来表示，其他用户权限用o来表示。

####【知识点】`ls `命令的详细意思。
Linux ls命令用于显示指定工作目录下之内容（列出目前工作目录所含之文件及子目录)。是list的缩写。
语法：` ls [-alrtAFR] [name...]`
参数 :

-a 显示所有文件及目录 (列出本目录下的所有文件，包括本级目录`.`和上级目录`..`目录名称开头为"."的视为隐藏档，也会列出)
-l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
-r 将文件以相反次序显示(原定依英文字母次序)
-t 将文件依建立时间之先后次序列出
-A 同 -a ，但不列出 "." (目前目录) 及 ".." (父目录)
-F 在列出的文件名称后加一符号；例如可执行文档则加 "*", 目录则加 "/"
如：
![](https://upload-images.jianshu.io/upload_images/271046-53a56aeab494cc6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-R 若目录下有文件，则以下的文件也按序列出


name参数：指定目录名

## 基本权限的修改
使用命令`chmod [-cfvR] [--help] [--version] mode file... `
选项参数：
    -c : 若该档案权限确实已经更改，才显示其更改动作 
    -f : 若该档案权限无法被更改也不要显示错误讯息 
    -v : 显示权限变更的详细资料 
    -R : 对目前目录下的所有档案与子目录进行相同的权限变更(即以递回的方式逐个变更) 
    --help : 显示辅助说明 
    --version : 显示版本 

mode : 权限设定字串，格式如下 :` [ugoa...][[+-=][rwxX]...][,...]`
其中u 表示该档案的拥有者，g 表示与该档案的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。 
+ 表示增加权限、- 表示取消权限、= 表示唯一设定权限。 


如：
```
chmod u+x cangls.av //为自己增加可执行的权限。
chmod g+w,o+w furong.av //为用户组和其他人
chmod a=rwx fengjie.av //给所有的都给三个权限。
```

同时mode还有另一个表达方式，其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。 

r=4，w=2，x=1 
若要rwx属性则4+2+1=7； 
若要rw-属性则4+2=6； 
若要r-x属性则4+1=5。 

常用的权限就有777代表最高权限，644普通文件权限，755执行权限。递增的这种权限是正常的，如果是递减是不可能出现的。

【疑】如何理解用户组的概念？

自问自答：解决权限管理问题。Linux是多用户操作系统，即使是个人使用，也致少有root用户和平时使用的普通用户。既然是多用户系统，就得规定哪些资源对哪些用户开放，开放多少（读、写、执行）。如果一一指定到具体用户，这样的管理也太麻烦了，所以有了组的慨念。这样，一个组对应一系列的权限，如果希望某用户拥有这样的权限，就把这个用户加入到这个组里。

# 权限的作用
我们说r是可读，w是可写，x是可执行，但是这只是浅层含义，要更进一步的区分各个权限的具体作用
##权限对文件的作用
r：读取文件的内容（cat more head tail）
w：编辑、新增、修改文件的内容（vi echo）**不包括删除文件！**
x: 可执行

## 权限对目录的作用
r:可以查询目录下的文件名（ls)
w:具有修改目录结构的权限。新建文件和目录，删除此目录下的文件和目录，重命名此目录下的文件和目录，剪切（touch rm mv cp)
x:可以进入目录（cd)

【总结】
对文件来讲：最高权限是x
对目录来讲：最高权限是w ，可以赋的权限 0 5 7 ，4 1 6 无意义。

# 其他权限命令
##　修改文件的所有者
`chown 用户名 文件名`
从实例4中可以看出，我们为了给普通用户user1赋权限，给了它7权限，但是这样的话，除了user1对他有7权限，其他所有用户都有7权限，这是非常不安全的。所以我们可以更改所有组。
`chown 用户名:组名 文件名`
## 修改文件的所属组
`chgrp 组名 文件名`
重点是组名是什么呢？是不是说我创建一个user1用户，就存在一个user1组呢？答案是肯定的。默认每建立一个用户，就创建一个和它同名的组。

# 默认权限
## 文件的默认权限
在windows中，创建一个文件，他的默认权限是从上层文件夹继承来的。
而linux不一样。它是通过umask的东西，来定义默认权限。
在系统上，`umask`命令可以查看。
会出现`0022`四位数字。
- 第一位0：文件的特殊权限。
- 022：文件的默认权限。
## 022 具体指的是什么？
文件默认不能创建为可执行文件，必须手工赋予执行权限
所以文件默认权限最大为666
默认权限需要换算为字母再相减
建立文件之后的默认权限，为666-umask值。

## 目录的默认权限
目录默认权限最大是77
默认权限需要换算成字母再相减
建立文件之后的默认权限，为777减去umask值

## 修改umask值
临时修改：`umask 0002`
永久修改：`vi /etc/profile`
这个是环境变量配置文件。
#实例
##【实例1】
1. 创建cangls.av文件，观察默认权限是那些？
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch cangls.av
```
![](https://upload-images.jianshu.io/upload_images/271046-9c065fc9199d488b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 试图打开文件。
可以打开，不可执行
3. 为自己增加可执行权限，再尝试打开。
```
chmod u+x cangls.av
```
![](https://upload-images.jianshu.io/upload_images/271046-e72322b6efe1d1d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 思考touch命令 和执行命令。

```
用法：touch [选项]... 文件...
Update the access and modification times of each FILE to the current time.

A FILE argument that does not exist is created empty, unless -c or -h
is supplied.

A FILE argument string of - is handled specially and causes touch to
change the times of the file associated with standard output.

必选参数对长短选项同时适用。
  -a			只更改访问时间（更改当前时间，即使加了字符串也还是修改为当前时间）
  -c, --no-create	不创建任何文件
  -d, --date=字符串	使用指定字符串表示时间而非当前时间
  -f			(忽略)
  -h, --no-dereference		会影响符号链接本身，而非符号链接所指示的目的地
				(当系统支持更改符号链接的所有者时，此选项才有用)
  -m			只更改修改时间
  -r, --reference=FILE   use this file's times instead of current time
  -t STAMP               use [[CC]YY]MMDDhhmm[.ss] instead of current time
      --time=WORD        change the specified time:
                           WORD is access, atime, or use: equivalent to -a
                           WORD is modify or mtime: equivalent to -m
      --help		显示此帮助信息并退出
      --version		显示版本信息并退出

请注意，-d 和-t 选项可接受不同的时间/日期格式。
         time规定为如下形式的十进制数:[[CC]YY]MMDDhhmm[.SS]
```
可以混合使用。

5. 将此文件的用户权限、所有组权限、其他用户权限都修改为可读可写，分析a的含义是什么？
```
chmod a=rw cangls.av
```
![](https://upload-images.jianshu.io/upload_images/271046-aadd06ba59eb69a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
a的含义是all，所有的，指的是用户权限、所有组权限、其他用户权限这些统一设置。


##【实例2】
1. 创建一个文件
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2018-04-17 11:07:14.417937534 +0800
最近更改：2018-04-17 11:07:14.417937534 +0800
最近改动：2018-04-17 11:07:14.417937534 +0800
创建时间：-
```
2. 修改访问时间为当前时间
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch -a learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2018-04-17 11:08:42.359322077 +0800
最近更改：2018-04-17 11:07:14.417937534 +0800
最近改动：2018-04-17 11:08:42.359322077 +0800
创建时间：-
```
3. 修改访问时间和更改时间为指定时间
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch -t 02032040 learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2018-02-03 20:40:00.000000000 +0800
最近更改：2018-02-03 20:40:00.000000000 +0800
最近改动：2018-04-17 11:14:29.008663946 +0800
创建时间：-
```
4.尝试使用-a修改为指定时间，可不可以？-a 所代表的是什么？-t呢？
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch -a 201102302040 learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2018-04-17 11:15:33.925649499 +0800
最近更改：2018-02-03 20:40:00.000000000 +0800
最近改动：2018-04-17 11:15:33.925649499 +0800
创建时间：-
```
5.混合使用，单独修改访问指定时间和单独修改更改时间。
```
dreamer@dreamer-Aspire-VN7-591G:~$ touch -at 201103030303 learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2011-03-03 03:03:00.000000000 +0800
最近更改：2018-02-03 20:40:00.000000000 +0800
最近改动：2018-04-17 11:17:57.339815374 +0800
创建时间：-
dreamer@dreamer-Aspire-VN7-591G:~$ touch -mt 11112222 learn
dreamer@dreamer-Aspire-VN7-591G:~$ stat learn
  文件：'learn'
  大小：0         	块：0          IO 块：4096   普通空文件
设备：802h/2050d	Inode：7340430     硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/ dreamer)   Gid：( 1000/ dreamer)
最近访问：2018-04-17 11:19:12.424944120 +0800
最近更改：2018-11-11 22:22:00.000000000 +0800
最近改动：2018-04-17 11:20:56.866509365 +0800
创建时间：-
```

##【实例3】
1.创建一个hello的文件夹，并加他的写权限清除掉。
```
dreamer@dreamer-Aspire-VN7-591G:~$ mkdir hello
dreamer@dreamer-Aspire-VN7-591G:~$ chmod 555 hello
```
![](https://upload-images.jianshu.io/upload_images/271046-9632e39d3498143b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


2.创建一个hello的文件。将其写权限打开。执行之中遇到了什么情况？如何解决的？
```
dreamer@dreamer-Aspire-VN7-591G:~$ cd hello
dreamer@dreamer-Aspire-VN7-591G:~/hello$ touch hello
touch: 无法创建'hello': 权限不够
dreamer@dreamer-Aspire-VN7-591G:~/hello$ sudo touch hello
```
提示权限不够。用sudo提升权限。
![](https://upload-images.jianshu.io/upload_images/271046-6f018d3fb7fb9060.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.试图删除hello文件，试描述现象并分析原因。
```
dreamer@dreamer-Aspire-VN7-591G:~/hello$ rm hello
rm：是否删除有写保护的普通空文件 'hello'？ Y
rm: 无法删除'hello': 权限不够 
```
它提示是否删除，发现权限不够。
其实文件夹其实也是一个文件，它里面的文件就是他的内容，所以删除一个文件夹内的文件或者新建一个文件，都属于在文件夹中写入内容，需要写权限。当写权限关闭后，就不能够在里面修改了。

## 【实例4】
1. 用root用户新建一个普通用户。
```
useradd user1
passwd user1
修改用户user1的密码。
新的密码：
```
2. 通过xshell4来新建会话连接。登录普通用户user1，这时候就可以通过root用户来设置，而普通用户来验证了。
3.思考可以在root的当前目录下创建123文件，再拿user1来验证？
不能，因为在root的家里面，普通用户无法到达。
4. 使用root用户，转到user1的家里，创建123目录和abc文件。
```
cd /home/user1
mkdir 123
touch 123/abc
```
```
查询权限发现：123目录权限如下：
drwxr-xr-x. 2 root root 4096 7月 1 06:24 123
```
【注：】很重要的一点是，看当前用户，和用户组，用root用户创建的文件，他的主用户就是root 用户组也是root，而我们创建的user1就变成了其他用户。所以面三个的权限才是对它的控制。

5.用root账户，将123目录及其目录下的abc文件的其他用户权限改为0。
```
chmod 750 123
chomod 640 123/abc
```
6. 思考，在user1目录下，使用`ls`命令，会有内容吗？
会，因为虽然对123和abc没有权限，但是我对user1的文件夹有权限，所以是可以看到的。但是如果我想要`ls 123/` 或`cd 123/`，则会报权限不够。
7.在root端，将文件夹123，改为有读权限。思考user1中有权限使用`ls 123/`吗？
```
chmod 754 123
```
理论上有权限列出文件，但是还是会报权限不足：
```
ls:无法访问123/abc:权限不够
abc
```
如只赋读权限是没有用的。

## 【实例5】
如何让用户对文件及目录拥有一定的权限？
要求：
1. 计算机中有一个study目录
2. 让老师拥有所有的权限。
3. 让本课程学员有查看的权限。
4. 其他所有人不允许查看这个目录

```
mkdir study
useradd teacher
passwd teacher
groupadd student
gpasswd -a student1 student
gpasswd -a student2 student
...
chown teacher:student study
chmod 750 study
```

