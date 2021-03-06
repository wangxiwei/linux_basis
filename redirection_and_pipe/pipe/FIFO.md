# 命名管道

命名管道(``FIFO``, 也称``named pipe``)，是另一种进程的通信方式。与匿名管道不同，
该管道将具象化为一个具体的文件，而且可以在不相关的进程间建立通信关系，效果就如同匿名管道的那样。

在Linux中，使用``mkfifo``命令或``mkfifo``函数(``C``函数)将创建一个命名管道。

简单演示:

```bash
$ mkfifo myfifo    # 创建一个名为myfifo的FIFO
$ cat > myfifo <<EOF
first line
last line
EOF                # 向这个myfifo这个命名管道写入一些内容

# 打开一个新终端
$ cat myfifo       # 读取命名管道，将获取到之前写入的内容
$ rm myfifo        # 删除命名管道，就像删除一个普通文件一样
```

命名管道比匿名管道罕见的多。

> Linux进程间的通信机制除了``管道``之外，还有很多种: ``信号``，``消息队列``，``信号量``，``共享内存``等等
