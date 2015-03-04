# lab0 SPOC思考题

## 个人思考题

---

能否读懂ucore中的AT&T格式的X86-32汇编语言？请列出你不理解的汇编语言。
- [x]  

>   可以。
    http://www.imada.sdu.dk/Courses/DM18/Litteratur/IntelnATT.htm

虽然学过计算机原理和x86汇编（根据THU-CS的课程设置），但对ucore中涉及的哪些硬件设计或功能细节不够了解？
- [x]  

>   对于汇编到硬件的接口不太清楚，尤其是内存管理和文件管理的细节方面不太了解。


哪些困难（请分优先级）会阻碍你自主完成lab实验？
- [x]  

>   1、不理解实验架构代码。
    2、实验所用软件工具的错误，如连接、编译错误等。
    3、实验代码量太大，导致无法按时完成。

如何把一个在gdb中或执行过程中出现的物理/线性地址与你写的代码源码位置对应起来？
- [x]  

>   找到基准地址计算偏移量。

了解函数调用栈对lab实验有何帮助？
- [x]  

>   可以清楚的掌握函数在内存中的地址，明确当前执行到那一条指令，方便调试与开发。

你希望从lab中学到什么知识？
- [x]  

>   操作系统的基本运作方式，以及为其增加各种高级功能的实现方法。

---

## 小组讨论题

---

搭建好实验环境，请描述碰到的困难和解决的过程。
- [x]  

> 之前已有ubuntu环境，通过apt安装各个工具包，未遇到困难。

熟悉基本的git命令行操作命令，从github上的[ucore git repo](http://www.github.com/chyyuu/ucore_lab)下载ucore lab实验
- [x] 

> 已完成。

尝试用qemu+gdb（or ECLIPSE-CDT）调试lab1
- [x] 

> 已完成。

对于如下的代码段，请说明”：“后面的数字是什么含义
```
/* Gate descriptors for interrupts and traps */
struct gatedesc {
    unsigned gd_off_15_0 : 16;        // low 16 bits of offset in segment
    unsigned gd_ss : 16;            // segment selector
    unsigned gd_args : 5;            // # args, 0 for interrupt/trap gates
    unsigned gd_rsv1 : 3;            // reserved(should be zero I guess)
    unsigned gd_type : 4;            // type(STS_{TG,IG32,TG32})
    unsigned gd_s : 1;                // must be 0 (system)
    unsigned gd_dpl : 2;            // descriptor(meaning new) privilege level
    unsigned gd_p : 1;                // Present
    unsigned gd_off_31_16 : 16;        // high bits of offset in segment
};
```

- [x]  

> 表示位域，如“unsigned gd_off_15_0 : 16;”中的16表示gd_off_15_0占16个bit。

对于如下的代码段，
```
#define SETGATE(gate, istrap, sel, off, dpl) {            \
    (gate).gd_off_15_0 = (uint32_t)(off) & 0xffff;        \
    (gate).gd_ss = (sel);                                \
    (gate).gd_args = 0;                                    \
    (gate).gd_rsv1 = 0;                                    \
    (gate).gd_type = (istrap) ? STS_TG32 : STS_IG32;    \
    (gate).gd_s = 0;                                    \
    (gate).gd_dpl = (dpl);                                \
    (gate).gd_p = 1;                                    \
    (gate).gd_off_31_16 = (uint32_t)(off) >> 16;        \
}
```

如果在其他代码段中有如下语句，
```
unsigned intr;
intr=8;
SETGATE(intr, 0,1,2,3);
```
请问执行上述指令后， intr的值是多少？

- [x]  

> 编译错误。修改后得10002。

请分析 [list.h](https://github.com/chyyuu/ucore_lab/blob/master/labcodes/lab2/libs/list.h)内容中大致的含义，并能include这个文件，利用其结构和功能编写一个数据结构链表操作的小C程序
- [x]  

> 
```
#include "stdio.h"
#include "list.h"


struct myList{
	int idx;
	list_entry_t link;
};

int main()
{
    struct myList mylist1, mylist0;
    mylist1.idx = 1;
    mylist0.idx = 0;
    list_init(&mylist0.link);
    list_add(&mylist0.link, &mylist1.link);
    printf("mylist0.idx = %d\nmylist0.link.next.idx = %d\nmylist0.link.next.link.prev.idx = %d", mylist0.idx, to_struct(mylist0.link.next, struct myList, link)->idx, to_struct(mylist0.link.next->prev, struct myList, link)->idx);
	return 0;
}

```

---

## 开放思考题

---

是否愿意挑战大实验（大实验内容来源于你的想法或老师列好的题目，需要与老师协商确定，需完成基本lab，但可不参加闭卷考试），如果有，可直接给老师email或课后面谈。
- [x]  

>  

---
