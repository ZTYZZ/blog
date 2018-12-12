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