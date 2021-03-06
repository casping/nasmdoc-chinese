7.3 产生`.SYS`文件
======

MS-DOS 设备驱动-`SYS`文件-是一些纯二进制文件，跟.com 文件相似，但有一点，它们的起始地址是 0，而不是`100h`。

因此，如果你用`bin`格式写一个设备程序，你不必使用`ORG`操作符，因为`bin`的缺省起始地址就是零。

相似的，如果你使用`obj`，你不必在代码段的起始处使用`RESB 100h``.SYS`文件拥有一个文件头，包含一些指针，这些指针指向设备中完成实际工作的不同的子过程。

这个结构必须在代码段的起始处被定义，尽管它并不是实际的代码。

要得到关于`.SYS`文件的更多信息，头结构中必须包含的数据，有一本以 FAQ 列表的形式给出的书可以在`comp.os.msdos.programmer`得到。
