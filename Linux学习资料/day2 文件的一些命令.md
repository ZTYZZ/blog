## 参考资料
### 文件的一些操作
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
	【注意】:可以同时复制多个文件.如`cp /root/install.log /root/install.log.syslog /tmp` 将两个文件都复制到tmp文件中去。
	

	