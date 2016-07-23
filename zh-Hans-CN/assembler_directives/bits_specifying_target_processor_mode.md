5.1 `BITS`: 指定目标处理器模式。
======

`BITS`指令指定 NASM 产生的代码是被设计运行在 16 位模式的处理器上还是运行在 32 位模式的处理器上。

语法是`BITS 16`或`BITS 32`大多数情况下，你可能不需要显式地指定`BITS`。

`aout`，`coff`，`elf`和`win32`目标文件格式都是被设计用在 32 位操作系统上的，它们会让 NASM 缺省选择 32 位模式。

而`obj`目标文件格式允许你为每一个段指定`USE16`或`USE32`，然后 NASM 就会按你的指定设定操作模式，所以多次使用`BITS`是没有必要的。

最有可能使用`BITS`的场合是在一个纯二进制文件中使用 32 位代码;

这是因为`bin`输出格式在作为 DOS 的`.COM`程序，DOS 的`.SYS`设备驱动程序，或引导程序时，默认都是 16 位模式。

如果你仅仅是为了在 16 位的 DOS 程序中使用 32 位指令，你不必指定`BITS 32`，如果你这样做了，汇编器反而会产生错误的代码，因为这样它会产生运行在16 位模式下，却以 32 位平台为目标的代码。

当 NASM 在`BITS 16`状态下时，使用 32 位数据的指令可以加一个字节的前缀0x66，要使用 32 位的地址，可以加上 0x67 前缀。

在`BITS 32`状态下，相反的情况成立，32 位指令不需要前缀，而使用 16 位数据的指令需要 0x66 前缀，使用 16 位地址的指令需要 0x67 前缀。

`BITS`指令拥有一个等效的原始形式:[BITS 16]和[BITS 32]。

而用户级的形式只是一个仅仅调用原始形式的宏。

## 5.1.1 `USE16` & `USE32`: BITS 的别名。

`USE16`和`USE32`指令可以用来取代`BITS 16`和`BITS 32`，这是为了和其他汇编器保持兼容性。