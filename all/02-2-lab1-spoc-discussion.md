# lab1 SPOC思考题

## 个人思考题

---

请描述ucore OS配置和驱动外设时钟的准备工作包括哪些步骤？ (w2l2)
- [x]  

>  

lab1中完成了对哪些外设的访问？ (w2l2)
- [x]  

>  

lab1中的cprintf函数最终通过哪些外设完成了对字符串的输出？ (w2l2)
- [x]  

>  

---

## 小组思考题

---

lab1中printfmt函数用到了可变参，请参考写一个小的linux应用程序，实定义和调用一个可变参数的函数。(w2l2)
- [x]  



如果让你来一个阶段一个阶段地从零开始完整实现lab1（不是现在的填空考方式），你的实现步骤是什么？（比如先实现一个可显示字符串的bootloader（描述一下要实现的关键步骤和需要注意的事项），再实现一个可加载ELF格式文件的bootloader（再描述一下进一步要实现的关键步骤和需要注意的事项）...） (w2l2)
- [x]  

> 

如何裁减lab1, 实现一个可显示字符串"THU LAB1"且依然能够正确加载ucore OS的bootloader？如果不能完成实现，请说明理由。(w2l2)
- [x]  

> 


---

## 开放思考题

---

如何修改lab1, 实现在出现除零错误异常时显示一个字符串的异常服务例程的lab1？
- [x]  

> 


在lab1/bin目录下，通过`objcopy -O binary kernel kernel.bin`可以把elf格式的ucore kernel转变成体积更小巧的binary格式的ucore kernel。为此，需要如何修改lab1的bootloader, 能够实现正确加载binar格式的ucore OS？
- [x]  

>

GRUB是一个通用的bootloader，被用于加载多种操作系统。如果放弃lab1的bootloader，采用GRU来加载ucore OS，请问需要如何修改lab1, 能够实现此需求？
- [x]  

>


如果没有中断，操作系统设计会有哪些问题或困难？在这种情况下，能否完成对外设驱动和对进程的切换等操作系统核心功能？
- [x]  

>  

---
