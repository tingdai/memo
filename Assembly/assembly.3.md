原文在这里: http://www.agner.org/optimize/

> # 3 The basics of assembly coding
> ## 3.1 Assemblers available

> There are several assemblers available for the x86 instruction set, but currently none of
them is good enough for universal recommendation. Assembly programmers are in the
unfortunate situation that there is no universally agreed syntax for x86 assembly. Different
assemblers use different syntax variants. The most common assemblers are listed below.

# 3 汇编编程基础

## 3.1 汇编器

x86指令集有几个汇编器, 但是没有一个好到推荐通用的. 汇编程序员面临着x86汇编没有通用语法的窘境. 不同的编译器使用不同的语法. 下面列出了常用的几个. 

> MASM
> The Microsoft assembler is included with Microsoft C++ compilers. Free versions can
sometimes be obtained by downloading the **Microsoft Windows driver kit** (WDK) or the
**platforms software development kit** (SDK) or as an add-on to the free Visual C++ Express
Edition. MASM has been a de-facto standard in the Windows world for many years, and the
assembly output of most Windows compilers uses MASM syntax. MASM has many
advanced language features. The syntax is somewhat messy and inconsistent due to a
heritage that dates back to the very first assemblers for the 8086 processor. Microsoft is still
maintaining MASM in order to provide a complete set of development tools for Windows, but
it is obviously not profitable and the maintenance of MASM is apparently kept at a minimum.
New instruction sets are still added regularly, but the 64-bit version has several deficiencies.
Newer versions can run only when the compiler is installed and only in Windows XP or later.
Version 6 and earlier can run in any system, including Linux with a Windows emulator. Such
versions are circulating on the web.

<u>MASM</u>
微软汇编器被包含在微软C++编译器里. 免费版本可以通过下载**微软Windows驱动工具包** (WDK) 或者**平台软件开发工具包** (SDK)得到, 也作为免费Visual C++ Express的插件.  MASM事实上充当了好多年的Windows标准, 而且大多数Windows编译器也是用MASM语法输出汇编. MASM具有很多高级语言特性. 由于衍生自8086处理器的最早的汇编器, 该语法某种程度上有点混乱和不一致. 微软至今仍在维护MASM以期为Windows提供一套完备的开发工具, 但这显然已经无利可图了, 对MASM的维护也只是勉力为之. 新指令会定期加进来, 但是64位版本有些缺陷. 新版本只能在Windows XP和之后的操作系统上运行, 还得是在安装了编译器的情况下. 第6版之前(含)可以在任何系统上运行, 包括安装了Windows 仿真器的Linux. 这些版本散落在网上. 

> GAS

> The Gnu assembler is part of the Gnu **Binutils** package that is included with most
distributions of Linux, BSD and Mac OS X. The Gnu compilers produce assembly output
that goes through the Gnu assembler before it is linked. The Gnu assembler traditionally
uses the AT&T syntax that works well for machine-generated code, but it is very
inconvenient for human-generated assembly code. The AT&T syntax has the operands in
an order that differs from all other x86 assemblers and from the instruction documentation
published by Intel and AMD. It uses various prefixes like % and $ for specifying operand
types. The Gnu assembler is available for all x86 platforms.
Fortunately, newer versions of the Gnu assembler has an option for using Intel syntax
instead. The Gnu-Intel syntax is almost identical to MASM syntax. The Gnu-Intel syntax
defines only the syntax for instruction codes, not for **directives**, functions, macros, etc. The
directives still use the old Gnu-AT&T syntax. Specify .intel_syntax noprefix to use the
Intel syntax. Specify .att_syntax prefix to return to the AT&T syntax before leaving
inline assembly in C or C++ code.

<u>GAS</u>

Gnu汇编器是Gnu **Binutils** 包的一部分, 这个包随着大多数Linux, BSD 和 Mac OS X 一起安装.  Gnu编译器使用Gnu 汇编器生成汇编输出再做链接. Gnu 汇编器通常使用AT&T语法, 这种语法在机器生成代码时表现很好, 但是在人工生成的汇编代码使用上有诸多不便. AT&T语法在操作数的顺序上和其他所有x86的汇编器都不一样, 跟Intel与AMD发布的指令文档也不一样. 它使用不一样的前缀例如%和$来指定操作数的类型. Gnu汇编器在所有x86平台上都可以用. 
好事是, 新一点的Gnu汇编器可以选择用Intel语法. Gnu-Intel语法和MASM语法几乎一样. Gnu-Intel语法值定义了指令码的语法, 没有**指令**, 函数, 宏等. 指令仍然使用老式的Gnu-AT&T语法. 通过指定`.intel_syntax noprefix`来使用Intel语法. 在离开C或C++代码中的内联汇编之前通过`.att_syntax prefix`回到AT&T语法. 

> NASM

> NASM is a free open source assembler with support for several platforms and object file
formats. The syntax is more clear and consistent than MASM syntax. NASM has fewer highlevel
features than MASM, but it is sufficient for most purposes. NASM would be my best
recommendation for a free multi-platform assembler if you don't need MASM syntax.

<u>NASM</u>

NASM是免费的开源汇编器, 支持几个平台, 也支持Object文件类型. 它的语法比MASM更清楚和统一. NASM比MASM的高级特性少, 但是多数情况下足够高效. 如果不需要MASM语法的话, NASM是我最推荐的多平台下的汇编器. 

> YASM

> YASM is very similar to NASM and uses exactly the same syntax. YASM was previously
more reliable than NASM, but is no longer updated regularly.

<u>YASM</u>
YASM和NASM很相似并且使用同样的语法. 之前YASM比NASM更可靠但是现在没有人定期更新它了. 


> FASM

> The Flat assembler is another open source assembler for multiple platforms. The syntax is
not compatible with other assemblers. FASM is itself written in assembly language - an
enticing idea, but unfortunately this makes the development and maintenance of it less
efficient.

<u>FASM</u>

Flat汇编器是另一款多平台开源汇编器. 语法和其他汇编器不兼容. FASM本身是用汇编语言实现的 - 听起来不错, 不幸的是这令它的开发和维护都没那么及时. 

> WASM

> The WASM assembler is included with the Open Watcom C++ compiler. The syntax
resembles MASM but is somewhat different. Not fully up to date.

<u>WASM</u>

WASM汇编器包含在Open Watcom C++编译器中. 语法类似MSASM, 某种程度上不同. 不是很跟得上时代. 

> JWASM

> JWASM is a further development of WASM. It is fully compatible with MASM syntax,
including advanced macro and high level directives. JWASM is a good choice if MASM
syntax is desired.

<u>JWASM</u>

JWASM是WASM的进阶版. 它和MASM语法完全兼容, 包括更高级的宏和高级指令. 如果需要使用MASM语法的话, JWASM不错. 

> TASM
> Borland Turbo Assembler is included with CodeGear C++ Builder. It is compatible with
MASM syntax except for some newer syntax additions. TASM is no longer maintained but is
still available. It is obsolete and does not support current instruction sets.

<u>TASM</u>

CodeGear C++ Builder带有Borland Turbo 汇编器. 除了几处新的语法之外它和MASM完全兼容. TASM不再继续维护, 但还是可用的. TASM已经被淘汰了, 而且不支持现在的指令集了. 

> GOASM

> GoAsm is a free assembler for 32- and 64-bits Windows including resource compiler, linker
and debugger. The syntax is similar to MASM but not fully compatible. It is currently not up
to date with the latest instruction sets. An integrated development environment (IDE) named
Easy Code is also available.

<u>GOASM</u>

GoAsm是32位64位Windows都可用的免费汇编器, 还包括源代码编译器, 链接器和调试器. 语法和MASM类似但不完全兼容. 它没有跟上最新的指令集. 一个叫做Easy Code的IDE可以使用. 

> HLA

> High Level Assembler is actually a high level language compiler that allows assembly-like
statements and produces assembly output. This was probably a good idea at the time it was
invented, but today where the best C++ compilers support intrinsic functions, I believe that
HLA is no longer needed.

<u>HLA</u>

高级汇编器(High Level Assembler)实际上是一个高级语言编译器, 它允许使用类汇编语言的语句并且声称汇编输出. 在发明HLA的时候这主意不错, 但是现在最好的C++编译器已经支持伪指令函数了, 我觉得没必要用HLA了. 

> Inline assembly
Microsoft and Intel C++ compilers support inline assembly using a subset of the MASM
syntax. It is possible to access C++ variables, functions and **labels** simply by inserting their
names in the assembly code. This is easy, but does not support C++ register variables. See
page 36.
The Gnu compiler supports inline assembly with access to the full range of **instructions** and
**directives** of the Gnu assembler in both Intel and AT&T syntax. The access to C++ variables
from assembly uses a quite complicated method.
The Intel compilers for Linux and Mac systems support both the Microsoft style and the Gnu
style of inline assembly.

<u>内联汇编</u>
微软和英特尔的C++编译器支持使用MASM的语法子集进行内联汇编. 可以访问C++变量, 方法和**标签**, 插入到汇编代码里就行了. 这很容易, 但是它不支持C++寄存器变量. 见36页. 

Gnu编译器支持内联汇编, 可以访问Gnu汇编器在Intel和AT&T语法下的所有**指令(instructions)**和**命令(directives)**. 在汇编中访问C++变量则挺复杂的. 

Linux和Mac系统下的Intel编译器支持微软风格和Gnu风格的内联汇编. 

<注> 关于instructions和directives: directive用来指导编译器去工作，如像 org .0x000. 其中的org是 directive,指导编译器将接下来的代码放在地址为0x000的空间。 还有如 db 0xff, DW 0x36等等. 而instruction 是指令，编译器将其转化成对应的机器码，然后CPU可以识别并执行这些机器码，如 mov P1,0xff. ADD R3,56等地址0000h~FFFFh是用十六进制表示的，计算机中的1K=2的10次方。0xffff行于 64个2的10次方。


> **Intrinsic functions** in C++
This is the newest and most convenient way of combining low-level and high-level code.
Intrinsic functions are high-level language representatives of machine instructions. For
example, you can do a vector addition in C++ by calling the intrinsic function that is
equivalent to an assembly instruction for vector addition. Furthermore, it is possible to
define a **vector class** with an overloaded + operator so that a vector addition is obtained
simply by writing +. Intrinsic functions are supported by Microsoft, Intel and Gnu compilers.
See page 34 and manual 1: "Optimizing software in C++".

<u>C++的**伪指令函数**</u>

这是最新的也是最便利的结合底层代码和高级语言的方式. **伪指令函数**是以高级语言面貌出现的机器指令. 比如你可以在C++中调用伪指令函数来做向量加法, 这和使用向量相加的汇编指令是等价的. 更进一步, 可以定义**向量类** 的重载运算符+, 这样向量的加法就可以简单第写成+. 微软, 英特尔和Gnu的编译器都支持为伪指令函数. 见34页和手册1: "优化C++软件". 

> Which assembler to choose?
In most cases, the easiest solution is to use intrinsic functions in C++ code. The compiler
can take care of most of the optimization so that the programmer can concentrate on
choosing the best algorithm and organizing the data into vectors. System programmers can
access system instructions by using intrinsic functions without having to use assembly
language.

<u>选择哪一个汇编器?</u>

多数情况下最简单的解决方案是在C++代码里使用伪指令函数. 编译器会做大部分优化, 程序员只需专心选择最好的算法并组织向量中的数据就好了. 系统程序员可以使用伪指令函数访问系统指令, 不需要使用汇编语言. 

> Where real low-level programming is needed, such as in highly optimized function libraries
or device drivers, you may use an assembler.
It may be preferred to use an assembler that is compatible with the C++ compiler you are
using. This allows you to use the compiler for translating C++ to assembly, optimize the
assembly code further, and then assemble it. If the assembler is not compatible with the
syntax generated by the compiler then you may generate an object file with the compiler
and disassemble the object file to the assembly syntax you need. The objconv disassembler
supports several different syntax dialects.

真正需要底层开发时, 例如高度优化的函数库或者设备驱动, 你可能需要用到汇编器. 

可能选择跟你在用的C++编译器兼容的汇编器好一些. 这样你就可以先用编译器把C++翻译成汇编代码, 进一步优化汇编代码, 然后使用汇编器. 如果汇编器和编译器生成的汇编代码不兼容的话, 你就得用编译器生成对象文件(*.obj), 再反汇编成你需要的汇编语法. objconv反汇编器支持集中不同的语法方言. 

> The NASM assembler is a good choice for many purposes because it supports many
platforms and object file formats, it is well maintained, and usually up to date with the latest
instruction sets.
The examples in this manual use MASM syntax, unless otherwise noted. The MASM syntax
is described in Microsoft Macro Assembler Reference at msdn.microsoft.com.
See www.agner.org/optimize for links to various syntax manuals, coding manuals and
discussion forums.

很多情况下NASM汇编器是一个合适的选择, 它支持多平台和对象文件格式, 维护的不错, 通常跟的上最新的指令集. 

除非特别说明, 这本手册的例子使用MASM语法. MASM语法在 msdn.microsoft.com 的微软Macro汇编器文档中有讲. 

www.agner.org/optimize 有各种语法手册, 编码手册和论坛的链接. 

> ## 3.2 Register set and basic instructions
> Registers in 16 bit mode
> General purpose and integer registers

> | Full register | Partial register |   Partial register |
|:-----------|:------------|:------------|
|bit 0 - 15 |bit 8 - 15 |bit 0 - 7
|AX |AH |AL
|BX |BH |BL
|CX |CH |CL
|DX |DH |DL
|SI
|DI
|BP
|SP
|Flags
|IP

> |Table 3.1. General purpose registers in 16 bit mode.|
|:-----------|

## 3.2 寄存器集和基本指令

<u>16位模式寄存器</u>

**通用寄存器(General Purpose)和整形寄存器**

| 全寄存器(Full Register) | 部分寄存器(Partial register) | 部分寄存器(Partial register)|
|:-----------|:------------|:------------|
|bit 0 - 15 |bit 8 - 15 |bit 0 - 7
|AX |AH |AL
|BX |BH |BL
|CX |CH |CL
|DX |DH |DL
|SI
|DI
|BP
|SP
|Flags
|IP

|表 3.1. 16位模式下的通用寄存器.|
|:----------:|

> The 32-bit registers are also available in 16-bit mode if supported by the microprocessor
and operating system. The high word of ESP should not be used because it is not saved
during interrupts.

微处理器和操作系统支持的话, 32位寄存器在16位模式下也可用. `ESP`的高位字不要用, 在跳转时它不会被保存. 

> Floating point registers

> |Full register|
|:-----------|
|bit 0 - 79
|ST(0)
|ST(1)
|ST(2)
|ST(3)
|ST(4)
|ST(5)
|ST(6)
|ST(7)

>|Table 3.2. Floating point stack registers|
|:--------|

> MMX registers may be available if supported by the microprocessor. XMM registers may be
available if supported by microprocessor and operating system.

**浮点寄存器(Floating Point Registers)**

|全寄存器|
|:-----------|
|bit 0 - 79
|ST(0)
|ST(1)
|ST(2)
|ST(3)
|ST(4)
|ST(5)
|ST(6)
|ST(7)

|表 3.2. 浮点栈寄存器|
|:--------|

微处理器支持的话MMX寄存器也可以用. 微处理器和操作系统支持的话XMM寄存器可以使用. 

> **Segment registers**

>|Full register|
|:---------:|
|bit 0 - 15
|CS
|DS
|ES
|SS

>|Table 3.3. Segment registers in 16 bit mode|
|:--------:|

> Register FS and GS may be available.

**段寄存器**

|全寄存器|
|:---------:|
|0-15位
|CS
|DS
|ES
|SS

|表 3.3. 16位模式下的段寄存器|
|:--------:|

FS和GS寄存器可能可用. 

> Registers in 32 bit mode
> General purpose and integer registers

> |Full register bit 0 - 31|Partial register bit 0 - 15|Partial register bit 8 - 15|Partial register bit 0 - 7|
|:--------:|:--------:|:--------:|:--------:|
|EAX |AX |AH |AL
|EBX |BX |BH |BL
|ECX |CX |CH |CL
|EDX |DX |DH |DL
|ESI |SI
|EDI |DI
|EBP |BP
|ESP |SP
|EFlags |Flags
|EIP |IP

>|Table 3.4. General purpose registers in 32 bit mode|
|:--------:|

**32位模式下的寄存器**

<u>通用寄存器和整形寄存器</u>

|全寄存器 0-31位|部分寄存器 0-15位|部分寄存器 8-15位|部分寄存器 0-7位
|:--------:|:--------:|:--------:|:--------:|
|EAX |AX |AH |AL
|EBX |BX |BH |BL
|ECX |CX |CH |CL
|EDX |DX |DH |DL
|ESI |SI
|EDI |DI
|EBP |BP
|ESP |SP
|EFlags |Flags
|EIP |IP

|表 3.4. 32位模式下的通用寄存器|
|:--------:|

>Floating point and 64-bit vector registers

> |Full register bit 0 - 79 |Partial register bit 0 - 63|
|:--------:|:--------:|
|ST(0) |MM0
|ST(1) |MM1
|ST(2) |MM2
|ST(3) |MM3
|ST(4) |MM4
|ST(5) |MM5
|ST(6) |MM6
|ST(7) |MM7

>|Table 3.5. Floating point and MMX registers|
|:-----:|

>The MMX registers are only available if supported by the microprocessor. The ST and MMX
registers cannot be used in the same part of the code. A section of code using MMX
registers must be separated from any subsequent section using ST registers by executing
an EMMS instruction.

**浮点和64位向量寄存器**

|全寄存器0-79位|部分寄存器0-63位|
|:--------:|:--------:|
|ST(0) |MM0
|ST(1) |MM1
|ST(2) |MM2
|ST(3) |MM3
|ST(4) |MM4
|ST(5) |MM5
|ST(6) |MM6
|ST(7) |MM7

|表 3.5. 浮点和MMX寄存器|
|:-----:|

MMX寄存器只在微处理器支持的情况下可用. ST和MMX寄存器在同一块代码里不可混用. 使用MMX寄存器的代码要调用`EMMS`指令来和后续的使用ST寄存器部分划清界限. 

>128- and 256-bit integer and floating point vector registers

> |Full register bit 0 - 255 |Full or partial register bit 0 - 127|
|:----:|:----:|
|YMM0 |XMM0
|YMM1 |XMM1
|YMM2 |XMM2
|YMM3 |XMM3
|YMM4 |XMM4
|YMM5 |XMM5
|YMM6 |XMM6
|YMM7 |XMM7

>|Table 3.6. XMM and YMM registers in 32 bit mode|
|:----:|

>The XMM registers are only available if supported both by the microprocessor and the
operating system. Scalar floating point instructions use only 32 or 64 bits of the XMM
registers for single or double precision, respectively. The YMM registers are available only if
the processor and the operating system supports the AVX instruction set.

**128和256位整形向量和浮点向量寄存器**

|全寄存器0-255位 |全寄存器或部分寄存器0-127位|
|:----:|:----:|
|YMM0 |XMM0
|YMM1 |XMM1
|YMM2 |XMM2
|YMM3 |XMM3
|YMM4 |XMM4
|YMM5 |XMM5
|YMM6 |XMM6
|YMM7 |XMM7

|表 3.6. 32位模式下的XMM寄存器和YMM寄存器|
|:----:|

只有在微处理器和操作系统都支持的情况下XMM寄存器可用. 浮点标量的指令在单精度和双精度下分别只使用32位或64位的XMM寄存器. **(Scalar floating point instructions use only 32 or 64 bits of the XMM registers for single or double precision, respectively) 这句话是说XMM寄存器还分32位和64位的, 还是说只有寄存器中的一部分被使用了?** YMM寄存器只在处理器和操作系统都支持AVX指令集的情况下可用. 

>Segment registers

> |Full register bit 0 - 15|
|:----:|
|CS
|DS
|ES
|FS
|GS
|SS

> |Table 3.7. Segment registers in 32 bit mode|
|:----:|

**段寄存器**

|全寄存器0-15位|
|:----:|
|CS
|DS
|ES
|FS
|GS
|SS

|表 3.7. 32位模式下的段寄存器|
|:----:|

> Registers in 64 bit mode
> General purpose and integer registers

> |Full register bit 0 - 63|Partial register bit 0 - 31|Partial register bit 0 - 15|Partial register bit 8 - 15|Partial register bit 0 - 7|
|:----:|----:|----:|----:|----:|
|RAX |EAX |AX |AH AL
|RBX |EBX |BX |BH BL
|RCX |ECX |CX |CH CL
|RDX |EDX |DX |DH DL
|RSI |ESI |SI |    |SIL
|RDI |EDI |DI |    |DIL
|RBP |EBP |BP |    |BPL
|RSP |ESP |SP |    |SPL
|R8 |R8D |R8W |    |R8B
|R9 |R9D |R9W |    |R9B
|R10 |R10D |R10W |    |R10B
|R11 |R11D |R11W |    |R11B
|R12 |R12D |R12W |    |R12B
|R13 |R13D |R13W |    |R13B
|R14 |R14D |R14W |    |R14B
|R15 |R15D |R15W |    |R15B
|RFlags |    |Flags
|RIP

>|Table 3.8. Registers in 64 bit mode|
|:----:|

<u>64位模式下的寄存器</u>

**通用寄存器和整形寄存器**

|全寄存器0-63位|Partial register bit 0 - 31|Partial register bit 0 - 15|Partial register bit 8 - 15|Partial register bit 0 - 7|
|:----:|----:|----:|----:|----:|
|RAX |EAX |AX |AH AL
|RBX |EBX |BX |BH BL
|RCX |ECX |CX |CH CL
|RDX |EDX |DX |DH DL
|RSI |ESI |SI |    |SIL
|RDI |EDI |DI |    |DIL
|RBP |EBP |BP |    |BPL
|RSP |ESP |SP |    |SPL
|R8 |R8D |R8W |    |R8B
|R9 |R9D |R9W |    |R9B
|R10 |R10D |R10W |    |R10B
|R11 |R11D |R11W |    |R11B
|R12 |R12D |R12W |    |R12B
|R13 |R13D |R13W |    |R13B
|R14 |R14D |R14W |    |R14B
|R15 |R15D |R15W |    |R15B
|RFlags |    |Flags
|RIP

|表 3.8. 64位模式下的寄存器|
|:----:|

>The high 8-bit registers AH, BH, CH, DH can only be used in instructions that have no REX
prefix.

>Note that modifying a 32-bit partial register will set the rest of the register (bit 32-63) to zero,
but modifying an 8-bit or 16-bit partial register does not affect the rest of the register. This
can be illustrated by the following sequence:

> <pre><code>
; Example 3.1. 8, 16, 32 and 64 bit registers
mov rax, 1111111111111111H ; rax = 1111111111111111H
mov eax, 22222222H ; rax = 0000000022222222H
mov ax, 3333H ; rax = 0000000022223333H
mov al, 44H ; rax = 0000000022223344H
</code></pre>

> There is a good reason for this inconsistency. Setting the unused part of a register to zero is
more efficient than leaving it unchanged because this removes a false dependence on
previous values. But the principle of resetting the unused part of a register cannot be
extended to 16 bit and 8 bit partial registers because this would break the backwards
compatibility with 32-bit and 16-bit modes.

> The only instruction that can have a 64-bit immediate data operand is MOV. Other integer
instructions can only have a 32-bit sign extended operand. Examples:

> <pre><code>
; Example 3.2. Immediate operands, full and sign extended
mov rax, 1111111111111111H ; Full 64 bit immediate operand
mov rax, -1 ; 32 bit sign-extended operand
mov eax, 0ffffffffH ; 32 bit zero-extended operand
add rax, 1 ; 8 bit sign-extended operand
add rax, 100H ; 32 bit sign-extended operand
add eax, 100H ; 32 bit operand. result is zero-extended
mov rbx, 100000000H ; 64 bit immediate operand
add rax, rbx ; Use an extra register if big operand
</code></pre>

> It is not possible to use a 16-bit sign-extended operand. If you need to add an immediate
value to a 64 bit register then it is necessary to first move the value into another register if
the value is too big for fitting into a 32 bit sign-extended operand.

高8位寄存器`AH`, `BH`, `CH`, `DH`只能在没有REX前缀的指令中使用. 

注意修改32位部分寄存器会把寄存器的其余32位(32-64位)置为0, 但是修改8位或16位部分寄存器对其他位没有影响. 从下面可以看出: 

<pre><code>
; 例 3.1. 8, 16, 32和64位寄存器
mov rax, 1111111111111111H ; rax = 1111111111111111H (64位)
mov eax, 22222222H ; rax = 0000000022222222H	(32位)
mov ax, 3333H ; rax = 0000000022223333H	(16位)
mov al, 44H ; rax = 0000000022223344H	(8位)
</code></pre>

这种不一致是有理由的. 把寄存器中不用的位置为0, 就不用依赖之前的值, 这样更有效率. 但是在使用8位和16位部分寄存器时这样做会破坏对32位和16位模式的兼容性(**How?**), 所以不能这样做. 

唯一能操作64位直接操作数的指令是`MOV`. 其他整形指令只能操作32位符号扩展操作数. 例如: 
<pre><code>
; 例 3.2. 直接操作数, 全64位, 和符号扩展的64位操作数
mov rax, 1111111111111111H ;					全64位的直接操作数
mov rax, -1 ;											32位符号扩展操作数
mov eax, 0ffffffffH ;							32位0扩展操作数
add rax, 1 ;											8位符号扩展操作数
add rax, 100H ;									32位符号扩展操作数
add eax, 100H ;									32位操作数. 结果是0扩展	(注: 这一行和上一行, 不明白为什么一个是符号扩展一个是0扩展)
mov rbx, 100000000H ;						64位直接操作数, (注, 100000000H这个直接数对32位寄存器来说太大了, add指令不能操作64位直接操作数, 所以要先放在一个64位寄存器上)
add rax, rbx ; 如果操作数很大, 再用一个寄存器. 
</code></pre>

16位符号扩展操作数不可用. 如果你需要往一个64位寄存器上加一个比32位符号扩展操作数还大的直接数的话, 就得先把这个数值放在另一个寄存器上. 

> Floating point and 64-bit vector registers

> |Full register bit 0 - 79|Partial register bit 0 - 63|
|:----:|:----:|
|ST(0) |MM0
|ST(1) |MM1
|ST(2) |MM2
|ST(3) |MM3
|ST(4) |MM4
|ST(5) |MM5
|ST(6) |MM6
|ST(7) |MM7

>|Table 3.9. Floating point and MMX registers|
|:----:|:----:|

>The ST and MMX registers cannot be used in the same part of the code. A section of code
using MMX registers must be separated from any subsequent section using ST registers by
executing an EMMS instruction. The ST and MMX registers cannot be used in device drivers
for 64-bit Windows.

**浮点和64位向量寄存器**

|全寄存器0-79位|部分寄存器0-63位|
|:----:|:----:|
|ST(0) |MM0
|ST(1) |MM1
|ST(2) |MM2
|ST(3) |MM3
|ST(4) |MM4
|ST(5) |MM5
|ST(6) |MM6
|ST(7) |MM7

|表 3.9. 浮点和MMX寄存器|
|:----:|:----:|

ST和MMX寄存器不能在代码中的同一部分使用. 使用MMX寄存器的代码要调用`EMMS`指令清除寄存器来和后续的使用ST寄存器的部分划清界限. ST和MMX寄存器不能用于64位Windows的系统驱动开发. 

>128- and 256-bit integer and floating point vector registers

> |Full register bit 0 - 255|Full or partial register bit 0 - 127|
|:----:|:----:|
|YMM0 |XMM0
|YMM1 |XMM1
|YMM2 |XMM2
|YMM3 |XMM3
|YMM4 |XMM4
|YMM5 |XMM5
|YMM6 |XMM6
|YMM7 |XMM7
|YMM8 |XMM8
|YMM9 |XMM9
|YMM10 |XMM10
|YMM11 |XMM11
|YMM12 |XMM12
|YMM13 |XMM13
|YMM14 |XMM14
|YMM15 |XMM15

>|Table 3.10. XMM and YMM registers in 64 bit mode|
|:----:|

> Scalar floating point instructions use only 32 or 64 bits of the XMM registers for single or
double precision, respectively. The YMM registers are available only if the processor and
the operating system supports the AVX instruction set.

**128位和256位整形向量和浮点向量寄存器**

|全寄存器0-255位|全寄存器或部分寄存器0-127位|
|:----:|:----:|
|YMM0 |XMM0
|YMM1 |XMM1
|YMM2 |XMM2
|YMM3 |XMM3
|YMM4 |XMM4
|YMM5 |XMM5
|YMM6 |XMM6
|YMM7 |XMM7
|YMM8 |XMM8
|YMM9 |XMM9
|YMM10 |XMM10
|YMM11 |XMM11
|YMM12 |XMM12
|YMM13 |XMM13
|YMM14 |XMM14
|YMM15 |XMM15

|表 3.10. 64位模式下的XMM和YMM寄存器|
|:----:|

浮点标量的指令在单精度和双精度下分别只使用XMM寄存器的32位和64位. YMM寄存器只在处理器和操作系统支持AVX指令集时可用. 

> Segment registers

> |Full register bit 0 - 15|
|:----:|
|CS
|FS
|GS

> |Table 3.11. Segment registers in 64 bit mode|
|:----:|

> Segment registers are only used for special purposes.

**段寄存器**

|全寄存器0-15位|
|:----:|
|CS
|FS
|GS

|表 3.11. 64位模式下的段寄存器|
|:----:|

段寄存器只用于特殊目的. 

> ## 3.3 Addressing modes

> Addressing in 16-bit mode

> 16-bit code uses a segmented memory model. A memory operand can have any of these
components:

## 3.3 取址模式

<u>16位取址模式</u>

16位代码使用分段内存模式. 内存操作数可含有以下模块: 

> A segment specification. This can be any segment register or a segment or group
name associated with a segment register. (The default segment is DS, except if BP is
used as base register). The segment can be implied from a label defined inside a
segment.

> A label defining a relocatable offset. The offset relative to the start of the segment is
calculated by the linker.

> An immediate offset. This is a constant. If there is also a relocatable offset then the
values are added.

> A base register. This can only be BX or BP.

> An index register. This can only be SI or DI. There can be no scale factor.

> A memory operand can have all of these components. An operand containing only an
immediate offset is not interpreted as a memory operand by the MASM assembler, even if it
has a []. Examples:

> <pre><code>
; Example 3.3. Memory operands in 16-bit mode
MOV AX, DS:[100H] ; Address has segment and immediate offset
ADD AX, MEM[SI]+4 ; Has relocatable offset and index and immediate
</code></pre>

> Data structures bigger than 64 kb are handled in the following ways. In real mode and
virtual mode (DOS): Adding 1 to the segment register corresponds to adding 10H to the
offset. In protected mode (Windows 3.x): Adding 8 to the segment register corresponds to
adding 10000H to the offset. The value added to the segment must be a multiple of 8.

* 段. 可能是任何段寄存器或者段或者和段寄存器相关的组名. (除非BP被用作基址寄存器(base register), 默认段是DS). 段内定义的标签也可作推算出段. 

* 定义可重新分配偏移的标签(a lable defining a relocatable offset). 链接器会计算相对于段的位移. 

* 直接偏移. 常数. 如果有重新分配的偏移的话这两个偏移会相加. 

* 基址寄存器. (base register). 只能是BX或BP. 

* 索引寄存器. 只能是SI或DI. 没有缩放系数(scale factor, 还是标量因素?). 


内存寻址操作数(memory operand)可能有以上所有组成部分. 只有一个直接偏移的操作数不被MASM编译器当做内存寻址操作数处理, 即使用[]括起来. 例如: 

<pre><code>
; 例 3.3. 16位模式的内存寻址操作数
MOV AX, DS:[100H] ; 地址有段DS加直接偏移量100H
ADD AX, MEM[SI]+4 ; 地址由可重新分配偏移(MEM[SI]), 索引(+4)和直接偏移量 ([100H])构成
</code></pre>

> Addressing in 32-bit mode
> 32-bit code uses a flat memory model in most cases. Segmentation is possible but only
used for special purposes (e.g. thread environment block in FS).

> A memory operand can have any of these components:
> A segment specification. Not used in flat mode.
A label defining a relocatable offset. The offset relative to the FLAT segment group is
calculated by the linker.
An immediate offset. This is a constant. If there is also a relocatable offset then the
values are added.
A base register. This can be any 32 bit register.
An index register. This can be any 32 bit register except ESP.
A scale factor applied to the index register. Allowed values are 1, 2, 4, 8.

<u>32位寻址</u>

32位代码多数情况下使用平坦内存模式(flat memory model). 有可能会分段但是只用于特殊目的(例如线程环境中的FS块, thread environment block in FS, 不理解). 

内存操作数可能有以下组成部分: 
* 段指定. 在平坦内存模式下不用. 
* 可重置偏移标签(a label defining a relocatable offset). 链接器会计算相对FLAT段组的偏移(offset relative to the FLAT segment group). 
* 立即数偏移. 常量. 如果也有可重置偏移的话就加上. 
* 基址寄存器(base register). 可能是任何32位寄存器. 
* 索引寄存器(index register). 除了ESP任何32位寄存器都可以. 
* 用在索引寄存器上的缩放系数. 允许1, 2, 4, 8. 

> A memory operand can have all of these components. Examples:

> <pre><code>
; Example 3.4. Memory operands in 32-bit mode
mov eax, fs:[10H] ; Address has segment and immediate offset
add eax, mem[esi] ; Has relocatable offset and index
add eax, [esp+ecx*4+8] ; Base, index, scale and immediate offset
</code></pre>

内存操作数可以包含以上所有组成部分. 例如: 

<pre><code>
; 例 3.4. 32位模式的内存操作数
mov eax, fs:[10H] ; 地址包含一个段和一个立即数偏移; Address has segment and immediate offset
add eax, mem[esi] ; (地址)包含一个可重定向偏移和一个索引; (索引写错了吧....) (**Has relocatable offset and index**)
add eax, [esp+ecx*4+8] ; (地址包含)基址(esp), 索引(ecx), 缩放(*4)和立即数(+8)偏移; Base, index, scale and immediate offset
</code></pre>


> Position-independent code in 32-bit mode

> Position-independent code is required for making shared objects (*.so) in 32-bit Unix-like
systems. The method commonly used for making position-independent code in 32-bit Linux
and BSD is to use a global offset table (GOT) containing the addresses of all static objects.
The GOT method is quite inefficient because the code has to fetch an address from the
GOT every time it reads or writes data in the data segment. A faster method is to use an
arbitrary reference point, as shown in the following example:

> <pre><code>
; Example 3.5a. Position-independent code, 32 bit, YASM syntax
SECTION .data
alpha: dd 1
beta: dd 2
SECTION .text
funca: ; This function returns alpha + beta
call get_thunk_ecx ; get ecx = eip
refpoint: ; ecx points here
mov eax, [ecx+alpha-refpoint] ; relative address
add eax, [ecx+beta -refpoint] ; relative address
ret
get_thunk_ecx: ; Function for reading instruction pointer
mov ecx, [esp]
ret
</code></pre>

<u>位置无关的32位代码</u>

位置无关代码在32位类Unix系统的共享对象(shared objects) ( \* .so )中有用到. 该方法在32位Linux和BSD中常用, 它使用包含所有静态对象地址的全局偏移表(global offset table, GOT). GOT方法效率很低, 因为代码每次在数据段中读写数据时都要从GOT中取地址. 更快的方法是使用 **arbitrary reference point** 强引用点, 例子如下: 

(注: 可以看下这个 http://yuxu9710108.blog.163.com/blog/static/2375153420082421213370/)

<pre><code>
; 例 3.5a. 位置无关代码, 32 位, YASM 语法
SECTION .data
alpha: dd 1
beta: dd 2
SECTION .text
funca: ; 这个方法返回 alpha + beta
call get_thunk_ecx ; get ecx = eip
refpoint: ; ecx points here
mov eax, [ecx+alpha-refpoint] ; 相对地址; relative address
add eax, [ecx+beta -refpoint] ; 相对地址; relative address
ret
get_thunk_ecx: ; 读指令指针的方法; Function for reading instruction pointer
mov ecx, [esp]
ret
</code></pre>

> The only instruction that can read the instruction pointer in 32-bit mode is the call
instruction. In example 3.5 we are using call get_thunk_ecx for reading the instruction
pointer (eip) into ecx. ecx will then point to the first instruction after the call. This is our
reference point, named refpoint.
The Gnu compiler for 32-bit Mac OS X uses a slightly different version of this method:

> <pre><code>
Example 3.5b. Bad method!
funca: ; This function returns alpha + beta
call refpoint ; get eip on stack
refpoint:
pop ecx ; pop eip from stack
mov eax, [ecx+alpha-refpoint] ; relative address
add eax, [ecx+beta -refpoint] ; relative address
ret
</code></pre>

能在32位模式下读取指令指针的指令只有call指令一个. 在例3.5中我们使用`call get_thunk_ecx`把指令指针(`eip`)读到`ecx`中. `ecx`就指向了`call`后面的一条指令. 这就是我们得到的引用指针(reference point), 叫`refpoint`. 

32位Mac OS X的Gnu编译器的用法有点不一样: 

<pre><code>
例 3.5b. 不好的方法!
funca:	 ; 该方法返回alpha + beta; This function returns alpha + beta
	call refpoint ; 在栈上得到eip; get eip on stack
refpoint:
	pop ecx ; (真的没写错吗)pop eip from stack
	mov eax, [ecx+alpha-refpoint] ; relative address
	add eax, [ecx+beta -refpoint] ; relative address
	ret
</code></pre>

> The method used in example 3.5b is bad because it has a call instruction that is not
matched by a return. This will cause subsequent returns to be mispredicted. (See manual 3:
"The microarchitecture of Intel, AMD and VIA CPUs" for an explanation of return prediction).
This method is commonly used in Mac systems, where the mach-o file format supports
references relative to an arbitrary point. Other file formats don't support this kind of
reference, but it is possible to use a self-relative reference with an offset. The YASM and
Gnu assemblers will do this automatically, while most other assemblers are unable to
handle this situation. It is therefore necessary to use a YASM or Gnu assembler if you want
to generate position-independent code in 32-bit mode with this method. The code may look
strange in a debugger or disassembler, but it executes without any problems in 32-bit Linux,
BSD and Windows systems. In 32-bit Mac systems, the loader may not identify the section
of the target correctly unless you are using an assembler that supports the reference point
method (I am not aware of any other assembler than the Gnu assembler that can do this
correctly).
The GOT method would use the same reference point method as in example 3.5a for
addressing the GOT, and then use the GOT to read the addresses of alpha and beta into
other pointer registers. This is an unnecessary waste of time and registers because if we
can access the GOT relative to the reference point, then we can just as well access alpha
and beta relative to the reference point.

例3.5b之所以不好使因为它的call指令没有配对的return. 这样导致返回和预期不一样. (解释和返回预期见手册3: "Intel, AMD和VIA CPU的微架构" ). 这种方法在Mac系统中常用, mach-o文件格式支持强点(**arbitrary point**)的相对引用. 其他文件格式不支持这种引用, 但是可能使用带有偏移量的自相对引用. YASM和Gnu汇编器会自动这样做, 其他的编译器大多无法处理. 所以如果你像在32位模式下使用这种发发生成位置无关代码的话就有必要使用YASM或者Gnu汇编器了. 在调试器和反汇编器里看起来代码可能有点奇怪, 但在32位Linux, BSD和Windows系统下运行起来没有问题. 在32位Mac系统下, 加载器(the loader?)可能不能正确地识别目标段, 除非你用支持引用指针方法的汇编器(我不知道除了Gnu汇编器还有别的能干这个). 

GOT方法会用例子3.5a中的引用指针方法来寻找GOT的地址, 然后使用GOT把alpha和beta的地址读到其他指针寄存器中. 这是对时间和寄存器无谓的浪费, 如果我们可以访问相对引用指针的GOT, 就可以访问相对于引用指针的alpha和beta了. 

> The pointer tables used in switch/case statements can use the same reference point for
the table and for the pointers in the table:

> <pre><code>
; Example 3.6. Position-independent switch, 32 bit, YASM syntax
SECTION .data
jumptable: dd case1-refpoint, case2-refpoint, case3-refpoint
SECTION .text
funcb: ; This function implements a switch statement
mov eax, [esp+4] ; function parameter
call get_thunk_ecx ; get ecx = eip
refpoint: ; ecx points here
cmp eax, 3
jnb case_default ; index out of range
mov eax, [ecx+eax*4+jumptable-refpoint] ; read table entry
; The jump addresses are relative to refpoint, get absolute address:
add eax, ecx
jmp eax ; jump to desired case
case1: ...
ret
case2: ...
ret
case3: ...
ret
case_default:
...
ret
get_thunk_ecx: ; Function for reading instruction pointer
mov ecx, [esp]
ret
</code></pre>

在`switch/case`代码中使用的指针表可以对指针表和指针表中的指针使用一样的引用指针: 

<pre><code>
; 例 3.6. 位置无关switch, 32位, YASM语法; Position-independent switch, 32 bit, YASM syntax
SECTION .data
jumptable: dd case1-refpoint, case2-refpoint, case3-refpoint
SECTION .text
funcb: ; 该方法实现switch; This function implements a switch statement
mov eax, [esp+4] ; 函数参数;  function parameter
call get_thunk_ecx ; get ecx = eip
refpoint: ; ecx points here
cmp eax, 3
jnb case_default ; index out of range
mov eax, [ecx+eax*4+jumptable-refpoint] ; read table entry
; The jump addresses are relative to refpoint, get absolute address:
add eax, ecx; (注: 上一行读到case1-refpoint, case2-refpoint或case3-refpoint的相对ecx/refpoint的地址, 需加上ecx/refpoint来指向绝对地址case1, 2, 3..)
jmp eax ; jump to desired case
case1: ...
ret
case2: ...
ret
case3: ...
ret
case_default:
...
ret
get_thunk_ecx: ; Function for reading instruction pointer
mov ecx, [esp]
ret
</code></pre>

> Addressing in 64-bit mode

> 64-bit code always uses a flat memory model. Segmentation is impossible except for FS and
GS which are used for special purposes only (thread environment block, etc.).
There are several different addressing modes in 64-bit mode: RIP-relative, 32-bit absolute,
64-bit absolute, and relative to a base register.

<u> 64位取址 </u>

64位代码始终使用平坦内存模型. 除了用于特殊目的的FS和GS不会使用段(例如线程环境块, thread environment block). 

64位模式下有几种不同的取址模式: 相对RIP(RIP-relative), 绝对32位取址(32-bit absolute), 绝对64位取址(64-bit absolute)及相对基址寄存器取址(relative to a base register). 

> RIP-relative addressing

> This is the preferred addressing mode for static data. The address contains a 32-bit sign-extended
offset relative to the instruction pointer. The address cannot contain any segment
register or index register, and no base register other than RIP, which is implicit. Example:

> <pre><code>
; Example 3.7a. RIP-relative memory operand, MASM syntax
mov eax, [mem]
; Example 3.7b. RIP-relative memory operand, NASM/YASM syntax
default rel
mov eax, [mem]
; Example 3.7c. RIP-relative memory operand, Gas/Intel syntax
mov eax, [mem+rip]
</code></pre>

> The MASM assembler always generates RIP-relative addresses for static data when no
explicit base or index register is specified. On other assemblers you must remember to
specify relative addressing.

<u>RIP相对取址模式</u>

静态数据多用这种取址. 地址包含一个相对于指令指针的32位符号扩展的偏移. 地址不包含段寄存器, 索引寄存器, 或者隐式RIP之外的基址寄存器. 

<pre><code>
; 例 3.7a. RIP相对内存操作数, MASM语法;  RIP-relative memory operand, MASM syntax
mov eax, [mem]
; 例 3.7b. RIP相对内存操作数, NASM/YASM语法; RIP-relative memory operand, NASM/YASM syntax
default rel
mov eax, [mem]
; Example 3.7c. RIP相对内存操作数, Gas/Intel语法; RIP-relative memory operand, Gas/Intel syntax
mov eax, [mem+rip]
</code></pre>

没有指定具体的基址寄存器或者索引寄存器的时候, MASM汇编器会位静态数据生成RIP相对地址. 其他汇编器就需要程序员指定相对地址了. 

> 32-bit absolute addressing in 64 bit mode

> A 32-bit constant address is sign-extended to 64 bits. This addressing mode works only if it
is certain that all addresses are below 231 (or above -231 for system code).

> It is safe to use 32-bit absolute addressing in Linux and BSD main executables, where all
addresses are below 231 by default, but it cannot be used in shared objects. 32-bit absolute
addresses will normally work in Windows main executables as well (but not DLLs), but no
Windows compiler is using this possibility.

> 32-bit absolute addresses cannot be used in Mac OS X, where addresses are above 232 by
default.

> Note that NASM, YASM and Gnu assemblers can make 32-bit absolute addresses when
you do not explicitly specify rip-relative addresses. You have to specify default rel in
NASM/YASM or [mem+rip] in Gas to avoid 32-bit absolute addresses.

> There is absolutely no reason to use absolute addresses for simple memory operands. Riprelative
addresses make instructions shorter, they eliminate the need for relocation at load
time, and they are safe to use in all systems.

<u>64位模式下的32位绝对取址</u>

32位常数地址会符号扩展到64位. 取址模式只在所有地址都小于231(或者大于231的系统代码)时才有效. 

在Linux和BSD的主程序文件中, 所有地址默认都小于231, 这种情况下使用32位绝对取址模式是安全的, 但是不能用于共享对象. 32位绝对取址模式在Windows主程序文件中通常可用(除了DLLs), 但是可能没有Windows编译器使用这种取址模式. 

32位绝对取值不能用于Mac OS X, 地址默认大于232. 

注意, 不特别指定rip-相对地址的话, NASM, YASM和Gnu汇编器可以使用32位绝对取址. 可以在NASM/YASM指定`default rel`或者在Gas中指定`[mem+rip]`来避免32位绝对取址. 

简单内存操作数绝对不要使用绝对取址. Rip相对取址在加载时不用重新定位, 使指令更短, 并且在所有系统下都是安全的 

> Absolute addresses are needed only for accessing arrays where there is an index register,
e.g.

> <pre><code>
; Example 3.8. 32 bit absolute addresses in 64-bit mode
mov al, [chararray + rsi]
mov ebx, [intarray + rsi*4]
</code></pre>

> This method can be used only if the address is guaranteed to be < 231, as explained above.
See below for alternative methods of addressing static arrays.

> The MASM assembler generates absolute addresses only when a base or index register is
specified together with a memory label as in example 3.8 above.

> The index register should preferably be a 64-bit register, not a 32-bit register. Segmentation
is possible only with FS or GS.

绝对取址只在访问数据的时候用的上, 这时有一个索引寄存器. 例如: 

<pre><code>
; 例 3.8. 64位模式下的32位绝对取址; 32 bit absolute addresses in 64-bit mode
mov al, [chararray + rsi]
mov ebx, [intarray + rsi*4]
</code></pre>

像前面说的只有在保证地址小于231的时候才能使用这种方法. 见下面静态数组取址的变通方法: 

MASM编译器只有在基址寄存器或索引寄存器和内存标签一同指定的时候才使用绝对取址, 见里3.8. 

索引寄存器尽量使用64位寄存器而不是32位的. 分段只在FS或GS中可用. 

> 64-bit absolute addressing

> This uses a 64-bit absolute virtual address. The address cannot contain any segment
register, base or index register. 64-bit absolute addresses can only be used with the MOV
instruction, and only with AL, AX, EAX or RAX as source or destination.

> <pre><code>
; Example 3.9. 64 bit absolute address, YASM/NASM syntax
mov eax, dword [qword a]
</code></pre>

> This addressing mode is not supported by the MASM assembler, but it is supported by
other assemblers.

<u>64位绝对取址</u>

使用64位绝对虚拟地址. 地址簿包含段寄存器基址寄存器或索引寄存器. 64位绝对地址只能以AL, AX, EAX 或RAX作为源和目标使用`mov`指令. 

<pre><code>
; 例 3.9. 64位绝对地址, YASM/NASM 语法; 64 bit absolute address, YASM/NASM syntax
mov eax, dword [qword a]
</code></pre>

MASM编译器不支持这种取址模式, 其他的支持. 

> Addressing relative to 64-bit base register

> A memory operand in this mode can have any of these components:
 - A base register. This can be any 64 bit integer register.
 - An index register. This can be any 64 bit integer register except RSP.
 - A scale factor applied to the index register. The only possible values are 1, 2, 4, 8.
 - An immediate offset. This is a constant offset relative to the base register.
A base register is always needed for this addressing mode. The other components are
optional. Examples:

> <pre><code>
; Example 3.10. Base register addressing in 64 bit mode
mov eax, [rsi]
add eax, [rsp + 4*rcx + 8]
</code></pre>

> This addressing mode is used for data on the stack, for structure and class members and
for arrays.

<u>64位基址寄存器相对取值</u>

这种模式下的内存操作数可以有以下组成: 
 * 基址寄存器. 可以是任何64位整形寄存器. 
 * 索引寄存器. 可以是除了RSP之外的任何64位整形寄存器. 
 * 作用于索引寄存器的缩放系数. 取值于1, 2, 4, 8之间. 
 * 直接位移. 相对于基址寄存器的常量偏移. 
 
基址寄存器是必需的. 其他部分可选. 例子: 

<pre><code>
; 例 3.10. 64位模式下的基址寄存器; Base register addressing in 64 bit mode
mov eax, [rsi]
add eax, [rsp + 4*rcx + 8]
</code></pre>

这种取址方式用来访问栈上的数据, 数据结构, 类成员变量以及数组. 

> Addressing static arrays in 64 bit mode

> It is not possible to access static arrays with RIP-relative addressing and an index register.

> There are several possible alternatives.

> The following examples address static arrays. The C++ code for this example is:

> <pre><code>
// Example 3.11a. Static arrays in 64 bit mode
// C++ code:
static int a[100], b[100];
for (int i = 0; i < 100; i++) {
b[i] = -a[i];
}
</code></pre>

<u> 64位模式下静态数组的取址</u>

使用RIP相对取址和索引寄存器来访问静态数据是不行的. 

有以下几种方法: 

下面的例子获取静态数组的地址. 等价C++代码是: 

<pre><code>
// 例 3.11a. 64位模式下的静态数组
// C++ code:
static int a[100], b[100];
for (int i = 0; i < 100; i++) {
b[i] = -a[i];
}
</code></pre>

> The simplest solution is to use 32-bit absolute addresses. This is possible as long as the
addresses are below 231.

> <pre><code>
; Example 3.11b. Use 32-bit absolute addresses
; (64 bit Linux)
; Assumes that image base < 80000000H
.data
A DD 100 dup (?) ; Define static array A
B DD 100 dup (?) ; Define static array B
.code
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
mov eax, [A+rcx*4] ; 32-bit address + scaled index
neg eax
mov [B+rcx*4], eax ; 32-bit address + scaled index
add ecx, 1
cmp ecx, 100 ; i < 100
jb TOPOFLOOP ; Loop
</code></pre>

> The assembler will generate a 32-bit relocatable address for A and B in example 3.11b
because it cannot combine a RIP-relative address with an index register.

> This method is used by Gnu and Intel compilers in 64-bit Linux to access static arrays. It is
not used by any compiler for 64-bit Windows, I have seen, but it works in Windows as well if
the address is less than 231. The image base is typically 222 for application programs and
between 228 and 229 for DLL's, so this method will work in most cases, but not all. This
method cannot normally be used in 64-bit Mac systems because all addresses are above
232 by default.

最简单的方法是使用32位绝对取址. 只要地址小于231就可以. 

<pre><code>
; 例 3.11b. 使用32位绝对地址; Use 32-bit absolute addresses
; (64 bit Linux)
; Assumes that image base < 80000000H
.data
A DD 100 dup (?) ; Define static array A
B DD 100 dup (?) ; Define static array B
.code
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
mov eax, [A+rcx*4] ; 32-bit address + scaled index (**rcx是ecx的一部分吗?我觉得作者写错了**)
neg eax
mov [B+rcx*4], eax ; 32-bit address + scaled index
add ecx, 1
cmp ecx, 100 ; i < 100
jb TOPOFLOOP ; Loop
</code></pre>

例3.11b中, 汇编器会位A和B生成32位可重分配地址, 因为它不能把RIP相对地址和索引寄存器结合起来. 

这种方法在64位Linux的Gnu和Intel汇编器中用来访问静态数组. 我没有见到过64位Windows汇编器使用这种方法的, 但是只要地址小于231, 在Windows下是可以用的. 应用程序的映射基址(image base)大多是222, DLL则在228和229之间, 所以多数但非所有情况下这种方法奏效. 64位Mac系统下所有地址都默认大于232, 所以通常不能用这种方法. 

> The second method is to use image-relative addressing. The following solution loads the
image base into register RBX by using a LEA instruction with a RIP-relative address:

> <pre><code>
; Example 3.11c. Address relative to image base
; 64 bit, Windows only, MASM assembler
.data
A DD 100 dup (?)
B DD 100 dup (?)
extern __ImageBase:byte
.code
lea rbx, __ImageBase ; Use RIP-relative address of image base
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
; imagerel(A) = address of A relative to image base:
mov eax, [(imagerel A) + rbx + rcx*4]
neg eax
mov [(imagerel B) + rbx + rcx*4], eax
add ecx, 1
cmp ecx, 100
jb TOPOFLOOP
</code></pre>

> This method is used in 64 bit Windows only. In Linux, the image base is available as
__executable_start, but image-relative addresses are not supported in the ELF file
format. The Mach-O format allows addresses relative to an arbitrary reference point,
including the image base, which is available as __mh_execute_header.

第二种方法是使用映射相对取址. 下面的方法使用`lea`指令和rip相对地址把映射基址载入`RBX`寄存器中: 

<pre><code>
; 例 3.11c. 相对映射基址地址; Address relative to image base
; 64 bit, Windows only, MASM assembler
; 64位, 限于Windows, MASM编译器
.data
A DD 100 dup (?)
B DD 100 dup (?)
extern __ImageBase:byte
.code
lea rbx, __ImageBase ; Use RIP-relative address of image base
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
; imagerel(A) = address of A relative to image base:
mov eax, [(imagerel A) + rbx + rcx*4]
neg eax
mov [(imagerel B) + rbx + rcx*4], eax
add ecx, 1
cmp ecx, 100
jb TOPOFLOOP
</code></pre>

此方法仅用于64位Windows. Linux下映射基址可从`__executable_start`得到, 但是映射相对取址在ELF文件格式中不支持. Mach-o格式允许强引用点的相对地址, 包括映射基址, 用`__mh_execute_header`得到.  

> The third solution loads the address of array A into register RBX by using a LEA instruction
with a RIP-relative address. The address of B is calculated relative to A.

> <pre><code>
; Example 3.11d.
; Load address of array into base register
; (All 64-bit systems)
.data
A DD 100 dup (?)
B DD 100 dup (?)
.code
lea rbx, [A] ; Load RIP-relative address of A
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
mov eax, [rbx + 4*rcx] ; A[i]
neg eax
mov [(B-A) + rbx + 4*rcx], eax ; Use offset of B relative to A
add ecx, 1
cmp ecx, 100
jb TOPOFLOOP
</code></pre>

> Note that we can use a 32-bit instruction for incrementing the index (ADD ECX,1), even
though we are using the 64-bit register for index (RCX). This works because we are sure that
the index is non-negative and less than 232. This method can use any address in the data
segment as a reference point and calculate other addresses relative to this reference point.
If an array is more than 231 bytes away from the instruction pointer then we have to load the
full 64 bit address into a base register. For example, we can replace LEA RBX,[A] with
MOV RBX,OFFSET A in example 3.11d.

第三种方法通过`LEA`指令作用于RIP相对地址将数组A的地址载入`RBX`寄存器. B的地址通过A来计算. 

<pre><code>
; 例 3.11d.
; Load address of array into base register
; 数组地址载入基址寄存器
; (All 64-bit systems)
.data
A DD 100 dup (?)
B DD 100 dup (?)
.code
lea rbx, [A] ; Load RIP-relative address of A
xor ecx, ecx ; i = 0
TOPOFLOOP: ; Top of loop
mov eax, [rbx + 4*rcx] ; A[i]
neg eax
mov [(B-A) + rbx + 4*rcx], eax ; Use offset of B relative to A
add ecx, 1
cmp ecx, 100
jb TOPOFLOOP
</code></pre>

注意到虽然使用64位索引寄存器(`rcx`), 却用32位指令来递增索引(`add ecx, 1). 这样不会出问题是因为我们确定索引非负且小于232. 这种方法可以使用数据段的地址作为引用点来计算其他地址的相对地址. 如果数组地址与指令指针地址间距大于231字节我们需要加载全64位地址到极致寄存器中. 例如可以例3.11d中的`LEA RBX, [A]`换成`MOV RBX, OFFSET A`. 

> Position-independent code in 64-bit mode

> Position-independent code is easy to make in 64-bit mode. Static data can be accessed
with rip-relative addressing. Static arrays can be accessed as in example 3.11d.

> The pointer tables of switch statements can be made relative to an arbitrary reference point.
It is convenient to use the table itself as the reference point:

> <pre><code>
; Example 3.12. switch with relative pointers, 64 bit, YASM syntax
SECTION .data
jumptable: dd case1-jumptable, case2-jumptable, case3-jumptable
SECTION .text
default rel ; use relative addresses
funcb: ; This function implements a switch statement
mov eax, [rsp+8] ; function parameter
cmp eax, 3
jnb case_default ; index out of range
lea rdx, [jumptable] ; address of table
movsxd rax, dword [rdx+rax*4] ; read table entry
; The jump addresses are relative to jumptable, get absolute address:
add rax, rdx
jmp rax ; jump to desired case
case1: ...
ret
case2: ...
ret
case3: ...
ret
case_default:
...
ret
</code></pre>

> This method can be useful for reducing the size of long pointer tables because it uses 32-bit
relative pointers rather than 64-bit absolute pointers.

> The MASM assembler cannot generate the relative tables in example 3.12 unless the jump
table is placed in the code segment. It is preferred to place the jump table in the data
segment for optimal caching and code prefetching, and this can be done with the YASM or
Gnu assembler.

<u>64位模式下的位置无关代码</u>

64位模式下很容易写位置无关代码. 静态数据通过rip相对地址访问. 静态数组如同例3.11d中一样访问. 

switch语句的指针表可以相对于强引用表得到. 使用表自身作为引用点比较方便: 

<pre><code>
; 例3.12. 相对指针的switch, 64位, YASM语法; switch with relative pointers, 64 bit, YASM syntax
SECTION .data
jumptable: dd case1-jumptable, case2-jumptable, case3-jumptable
SECTION .text
default rel ; use relative addresses
funcb: ; This function implements a switch statement
mov eax, [rsp+8] ; function parameter
cmp eax, 3
jnb case_default ; index out of range
lea rdx, [jumptable] ; address of table
movsxd rax, dword [rdx+rax*4] ; read table entry
; The jump addresses are relative to jumptable, get absolute address:
add rax, rdx
jmp rax ; jump to desired case
case1: ...
ret
case2: ...
ret
case3: ...
ret
case_default:
...
ret
</code></pre>

这种方法使用32位相对指针而非64位绝对指针, 所以可以用来缩减长指针表的空间. 

MASM汇编器不能像例3.12中那样生成相对指针表, 除非跳转表至于代码段中. 为优化缓存和代码预取, 最好将跳转表放在数据段中, YASM或者Gnu汇编器都可以做到这一点. 

> ## 3.4 Instruction code format

> The format for instruction codes is described in detail in manuals from Intel and AMD. The
basic principles of instruction encoding are explained here because of its relevance to
microprocessor performance. In general, you can rely on the assembler for generating the
smallest possible encoding of an instruction.

> Each instruction can consist of the following elements, in the order mentioned:

## 3.4 指令码格式

指令码格式在Intel和AMD的手册中均有详述. 这里讲的指令编码原则是为了解释和微处理器性能的关系. 通常可以依赖汇编器来生成最小编码. 

每个指令可以由以下元素构成, 

> 1. Prefixes (0-5 bytes)
These are prefixes that modify the meaning of the opcode that follows. There are
several different kinds of prefixes as described in table 3.12 below.

1. 前缀(0-5字节)

前缀会改变后面操作码的含义. 有如表3.12中几种不同的前缀. 

> 2. Opcode (1-3 bytes)
This is the instruction code. The first byte is 0Fh if there are two or three bytes. The
second byte is 38h - 3Ah if there are three bytes.

2. 操作码(1-3字节)

指令码. 多余一个字节的话第一个字节是0Fh. 多余两个字节的话第二个字节是38h`3Ah. 

> 3. mod-reg-r/m byte (0-1 byte)
This byte specifies the operands. It consists of three fields. The mod field is two bits
specifying the addressing mode, the reg field is three bits specifying a register for the
first operand (most often the destination operand), the r/m field is three bits
specifying the second operand (most often the source operand), which can be a
register or a memory operand. The reg field can be part of the opcode if there is only
one operand.

3. mod-reg-r/m 字节(0-1字节)

这个字节指定操作数. 有三个域. mod域是两个bit指定取址模式, reg域有三个bit指定第一个操作数的寄存器(通常是目标操作数), r/m域是三个bit指定第二个操作数(通常位源操作数), 可能是寄存器也可能是内存. 如果只有一个操作数的话reg域可能是操作码的一部分. 

> 4. SIB byte (0-1 byte)
This byte is used for memory operands with complex addressing modes, and only if
there is a mod-reg-r/m byte. It has two bits for a scale factor, three bits specifying a
scaled index register, and three bits specifying a base pointer register. A SIB byte is
needed in the following cases:
a. If a memory operand has two pointer or index registers,
b. If a memory operand has a scaled index register,
c. If a memory operand has the stack pointer (ESP or RSP) as base pointer,
d. If a memory operand in 64-bit mode uses a 32-bit sign-extended direct memory
address rather than a RIP-relative address.
A SIB byte cannot be used in 16-bit addressing mode.

4. SIB字节(0-1字节)

这个字节用于复杂取址模式的内存操作数, 只在mod-reg-r/m字节存在的时候才存在. 它有2个bit的缩放系数, 3个bit指定缩放索引寄存器, 还有3个bit指定基址寄存器. 在下面这些情况中需要SIB字节: 

a. 内存操作数有两个指针或索引寄存器
b. 内存操作数有缩放索引寄存器
c. 内存操作数用栈指针作为基址指针(ESP/RSP)
d. 64位模式内存操作数使用32位符号扩展直接内存地址, 而不是RIP相对地址

SIB字节不能用于16位取址模式. 

> 5. Displacement (0, 1, 2, 4 or 8 bytes)
This is part of the address of a memory operand. It is added to the value of the
pointer registers (base or index or both), if any.
A 1-byte sign-extended displacement is possible in all addressing modes if a pointer
register is specified.
A 2-byte displacement is possible only in 16-bit addressing mode.
A 4-byte displacement is possible in 32-bit addressing mode.
A 4-byte sign-extended displacement is possible in 64-bit addressing mode. If there
are any pointer registers specified then the displacement is added to these. If there
is no pointer register specified and no SIB byte then the displacement is added to
RIP. If there is a SIB byte and no pointer register then the sign-extended value is an
absolute direct address.
An 8-byte absolute direct address is possible in 64-bit addressing mode for a few
MOV instructions that have no mod-reg-r/m byte.

5. 占位符(0,1,2,4,8字节)

只是内存操作数地址的一部分. 如果内存操作数地址有指针寄存器(基址或索引或二者皆有)的话, 这个字节被加在它们的值上. 

1-字节符号扩展占位符在任何指定指针寄存器的取址模式下都有可能出现. 

2-字节占位符只在16位取址模式下可用

4-字节占位符在32位取址模式下可用

4-字节符号扩展占位符在64位取址模式下可能出现. 如果指定了指针寄存器的话这个占位符就会被加上. 如果没有指定指针寄存器, 也没有SIB字节的话, 占位符会被加到RIP上. 如果有SIB字节没有指针寄存器的话那么符号扩展值是一个绝对直接地址. 

8-字节绝对直接地址在64位取址模式下可能出现, 在几个没有mod-reg-r/m字节的MOV指令时可能出现. 

> 6. Immediate operand (0, 1, 2, 4 or 8 bytes)
This is a data constant which in most cases is a source operand for the operation.
A 1-byte sign-extended immediate operand is possible in all modes for all
instructions that can have immediate operands, except MOV, CALL and RET.
A 2-byte immediate operand is possible for instructions with 16-bit operand size.
A 4-byte immediate operand is possible for instructions with 32-bit operand size.
A 4-byte sign-extended immediate operand is possible for instructions with 64-bit
operand size.
An 8-byte immediate operand is possible only for moves into a 64-bit register.

6. 直接操作数(0,1,2,4,8字节)

一个多数情况下作源操作数的数字常量. 

1-字节符号扩展直接操作数可能在所有模式所有可以作用于直接操作数的指令中出现, 除了MOV, CALl和RET. 

2-字节 