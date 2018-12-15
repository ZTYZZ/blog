## 参考资料
### 文件的一些操作
快捷键:
`ctrl + L` ：清屏操作。`clear`命令 也可以清屏


`ls `
	代表list，罗列出目录的文件，默认是家目录，如果是root目录则是/root目录下的文件。
	`-a` 选项：表示能够显示全部的文件，包括隐藏的。
	`-l` 选项：是long的意思，表示完整的显示一个文件的信息。
	`-h`选项：是human的意思，用人类习惯的方式显示文件信息。
	`-d`选项：查看目录属性，试想一下以下场景，假设你想要查看root目录的信息，而不是下面的文件，在使用`ls`命令的时候，你会发现显示的是一系列的文件，这时候你就需要用d选项。

	[注意]：这些选项都可以合并，比如 `-ld -lh `等等

`mkdir`命令
	代表make directory。

	`-p` 递归创建，在想要创建多个文件夹的时候，需要用到此选项。如`mkdir /tmp/Japan/longze`(假设Japan之前没有创建)也比如`mkdir /tmp/Japan/cangjing /tmp/Japan/boduo` 可以这样的创建多个文件。

`cd` 命令。
`pwd` 命令
	代表print working directory
	命令所在路径 /bin/pwd
	显示当前所在目录的绝对路径。

	这里面`.`：代表当前目录 `..`：代表上一级目录

`rmdir` 命令
	代表：remove empty directory
	删除空目录

`cp`命令
	代表：copy
	复制文件或目录
	复制文件的时候，可以直接目录`cp /tmp/Japan/cangjing /root`即可
	

	`-r`：复制目录
	`-p`：保留文件属性,在复制的时候，会有所变化，比如文件的时间，会变成最后修改的时间。所以如果不想变化的话，就需要加这个选项`-p`
	【注意】:
	1. 可以同时复制多个文件.如`cp /root/install.log /root/install.log.syslog /tmp` 将两个文件都复制到tmp文件中去。
	2. 可以更名操作。

`mv`命令
	代表：move
	可以剪切和更名操作。
	
	【注意】：怎么在本目录下做改名的操作？
		将当前文件夹 移动到当前文件夹并换个名字。


	

`rm`
	rm -rf [文件或者目录]
		-r 删除目录
		-f 强制执行

		功能描述：删除文件


文件处理命令：
`touch`
	touch [文件名]
	执行权限：所有用户
	功能描述 ：创建空文件

	例子：`touch Japanlovestory.list`


`cat`
	cat [文件名]
	功能描述： 显示文件内容
			-n 显示行号

	 例子： `cat /etc/issue`
	 		`cat -n /etc/services`

	 cat 命令不适合浏览长的命令。

`tac` 
	反向列式

`more`
	语法： more [文件名]
	（空格）或 f  翻页
	（Enter）    换行
	 q 或 Q		退出

	 功能描述：分页显示文件内容
	 【注意】 不能向上分页

`less`
	语法：less [文件名]
	功能描述：分页显示文件内容 （可向上翻页）
	
	按/ 可以搜索关键词；比如：`/service (表示搜索sevice关键词)`按 n 可以将查找到的关键词下翻页（next）

`head`
	语法：head [文件名]

	功能描述： 显示文件前面几行
				-n 指定行数



`tail` 查看末尾几行
		-n 指定行数
		-f 动态显示文件末尾内容
		上述两个命令 ，如果没有指定行数 ，默认是10行。


`ln` 是链接命令
	分为硬链接和软连接

	软连接则相当于windows的看快捷方式。-s
		特征：	1. lrwxrwxrwx
			    2. 文件大小 只是符号链接
			    3. /tmp/issue.soft -> /etc/issue

		例子：`ln -s /etc/issue /tmp/issue.soft`

	硬链接是相当于将文件拷贝一份，并且有同步功能

		特征	：	1. 信息完全一样。
				2. 通过i节点识别。
				3. 不能跨分区。
				4. 不能针对目录使用。

	当源文件删除时，软连接显示错误，而硬链接的文件依旧存在。


权限管理命令：

`chmod`
	语法：	`chmod [{ugoa} {+-=} {rwx}] [文件或目录]
			`[mode=421] [文件或目录]`
			`-R` 递归修改

			r -- 4
			w -- 2
			x -- 1

			rwxrw-r-- 764
	功能描述：更改文件或目录的权限。

	例子： `chmod g+w,o-r Japanlovestory.list`


深入理解文件权限：
	权限		功能				文件						目录
	r		读权限		可以查看文件内容		可以列出目录中的内容
	w		写权限		可以修改文件内容		可以在目录中创建、删除文件
	x		执行权限		可以执行文件			可以进入目录

	对文件 	r：cat/more/head/tail/less
			w: vim
			x: script 	command

	对目录	r: ls
			w: touch/mkdir/rmdir/rm
			x: cd(有r权限一般都有x权限)


	改变文件的所有者：chown 语法：`chown [用户] [文件或目录]`	
				【注意】:只有管理员root可以执行操作。



	改变所属组：`chgrp` 
				语法：`chgrp [用户组] [文件或目录]

				【注意】	 useradd是添加用户
						 groupadd 添加用户组
	`umask`命令
			功能描述：显示、设置文件的缺省权限。
			语法：	`umask [-S]`
					-S  以rwx形式显示新建文件缺省权限
			例子： `umask -S`

			【注意】 如果直接输入`umask` 命令 会显示 0022，这是什么意思呢？
				   0 代表的是特殊权限
				   022 三种用户的分类 --- -w- -w-

				   777 rwx rwx rwx
				   022 --- -w- -w-
				   ----------------
				       rwx r-x r-x 目录   （异或关系）、
				       rw- r-- r-- 文件

				   当要修改缺省权限的时候，需要做逆运算。

				  	比如：要创建rwx 欧赔 --- --- 的缺省权限
				  		需要输入命令`umask 077`

文件搜索操作
	`find`命令
		语法：find [搜索范围] [匹配条件]
		常见命令
		```
		 find /etc -name init // 只能精准搜索，需要通配符 如 *init* init*(开头) 正则表达式。
		 find / -size +204800 // +n 大于 -n小于  n 等于 （这个是数据块的 1数据块 512字节 0.5k）

		 find /home -user shenchao // -group 根据所属组查找

		 find /etc -cmin -5 //根据时间属性来查找（在/etc目录下查找5分钟内容被修改过属性的文件和目录）-amin 访问时间access -cmin 文件属性change -mmin 文件内容 modify
		```

		find命令的高级操作
		```
		find /etc -size +163840 -a size -204800//在/etc下查找大于80MB小于100MB的文件

		-a 代表两个条件同时满足
		-o 代表两个条件满足一个即可

		`find /etc -name inittab -exec ls -l {} \;
		-exec/-ok 命令{}\;对搜索结果执行操作。（-ok 是要一个一个确认可以自己尝试一下）
		```
		其他选项：	-type 根据文件类型查找 f文件 d目录 l软连接文件
					-inum 根据i节点查找。

		如：`find /etc init* -a -type -d//查找 etc目录下以init开头的目录`
		

其他搜索命令
		
		`locate`命令
		语法：locate 文件名
		选项：-i 查找时不区分大小写
		功能描述：在文件资料库中查找文件

		【注意】
		1. locate查找是在文件资料库中查找，所以在创建一个文件的时候，资料库可能没有更新，查找这个文件的时候，就不会查找成功，所以需要更新资料库。`updatedb//手动更新资料库`

		2. /tmp 临时文件 不在资料库搜集之中，所以这个目录下的 文件都不能搜索到。

		
		`which`命令
		语法：which 命令
		功能描述：搜索命令所在目录及别名信息

		例子：`which ls`


		`whereis` 命令
		语法：whereis 命令
		功能描述：搜索命令所在目录及帮助文档路径。

		例子：`whereis ls`


		`grep`命令

		语法：grep -iv[指定字串][文件]

		功能描述：在文件中搜索字串匹配的行并输出。
				-i 不区分大小写
				-v 排除指定字串

		例子：`grep mysql /root/install.logu

帮助命令：
		
		man命令
		英文原意：manual
		语法： `man [命令或配置文件]
		功能描述：获得帮助信息

		例子： 	`man ls查看ls命令的帮助信息`
				`man services 查看配置文件services的帮助信息`
	
		whatis 命令
		只读取到就简短的介绍信息。

		apropos services
		查看配置文件的简短信息。


		touch --help（能把一些选项列出来）

		help命令
		功能描述：查看shell内置命令的帮助信息
		例子：`help umask`查看 umask

		【注意】什么是内置命令？是找不到的 内置在shell中的，所以用`which cd`就找不到相关文件，系统将会给出提示： no cd in (/usr/lib/qt-3.3/bin:/usr.....)


用户管理命令：
		
		useradd
		功能描述：添加新用户
		语法： useradd 用户名
		例子：`useradd yangmi`

		passwd
		功能描述：设置用户密码
		语法：passwd 用户名
		例子：`passwd yangmi`

		who

		语法：who
		功能描述：查看登录用户信息
		
		返回的格式：登录用户名	登录终端（tty为本地终端：本例中则是虚拟机中登录的 pts：远程终端）	登录时间

		w
		功能描述：查看登录用户详细信息
		例子：`w`

压缩解压命令：
		
		第一种压缩文件 .gz

		`gzip`压缩成.gz格式
			只能压缩文件。 并且不保留原文件


		gunzip / gzip -d
			功能描述：解压缩.gz的压缩文件

		
		tar 
			功能描述：打包目录
			语法：	tar 选项[-zcf] [压缩后文件名] [目录]
					-c 打包
					-v 显示详细信息
					-f 指定文件名
					-z 打包同时压缩(放在最前面)
			压缩后文件格式：.tar.gz

		tar 
			选项：	-x 解包
					-v 显示详细信息
					-f 指定压缩文件
					-z 解压缩