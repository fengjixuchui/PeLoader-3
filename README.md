# PeLoader
模仿操作系统，加载pe文件到内存中

该项目主要是为了检测pe的学习程度，是否都完全理解了。当然没有完全理解

该项目大部分都是用c写的，没有太接触过c，脑瓜子容易发蒙，只有一行是汇编。很容易理解的

首先按照文件对齐的方式，加载pe到内存中。

然后按照内存对齐的方式，先把pe头拷贝到内存中，其实拷贝不拷贝都不会影响程序的执行

然后将每个section加载到相应的位置。当然我为了省事，将内存的属性设置成可读可写可执行。大家注意

然后处理导入表，当然我为了省事，只通过IAT修复，INT这种加载方式我忽略了

随后处理程序的重定位表，方便程序迁移到其他内存位置

然后一个jmp，到entryofaddress。

By the way，如果待加载的程序调用了Exitprocess的话，最终程序控制流程还是会回到咱们的

因为我再修正导入表时候，hook了Exitprocess的地址

test.exe 是测试程序，test.c 是测试程序的代码

#### 目前已经发现的BUG
1. 不能加载诸如cmd.exe
2. 没有处理很多东西。没有处理资源表，延迟绑定等
运行截图



