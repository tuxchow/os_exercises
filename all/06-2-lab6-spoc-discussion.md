# lab6 spoc 思考题

- 有"spoc"标记的题是要求拿清华学分的同学要在实体课上完成，并按时提交到学生对应的ucore_code和os_exercises的git repo上。


## 个人思考题

### 总体介绍

 - ucore中的调度点在哪里，完成了啥事？
 - 进程控制块中与调度相关的字段有哪些？
 - ucore的就绪队列数据结构在哪定义？在哪进行修改？
 - ucore的等待队列数据结构在哪定义？在哪进行修改？

### 调度算法支撑框架

 - 调度算法支撑框架中的各个函数指针的功能是啥？会被谁在何种情况下调用？
 - 调度函数schedule()的调用函数分析，可以了解进程调度的原因。请分析ucore中所有可能的调度位置，并说明可能的调用原因。
  
### 时间片轮转调度算法

 - 时间片轮转调度算法是如何基于调度算法支撑框架实现的？
 - 时钟中断如何调用RR_proc_tick()的？

### stride调度算法

 - stride调度算法的思路？ 
 - stride算法的特征是什么？
 - stride调度算法是如何避免stride溢出问题的？
 - 无符号数的有符号比较会产生什么效果？
 - 什么是斜堆(skew heap)?

## 小组练习与思考题

### (1)(spoc) 理解调度算法支撑框架的执行过程

即在ucore运行过程中通过`cprintf`函数来完整地展现出来多个进程在调度算法和框架的支撑下，在相关调度点如何动态调度和执行的细节。(越全面细致越好)

请完成如下练习，完成代码填写，并形成spoc练习报告
> 需写练习报告和简单编码，完成后放到git server 对应的git repo中

### 练习用的[lab6 spoc exercise project source code](https://github.com/chyyuu/ucore_lab/tree/master/labcodes_answer/lab6_result)

```
输出结果如下：
the process 1 delete from the queue
the process 1 will run
the process 2 will wake up
the process 2 add to the queue
the process 1 will sleep
the process 2 delete from the queue
the process 2 will run
kernel_execve: pid = 2, name = "priority".
the process 3 will wake up
the process 3 add to the queue
the process 4 will wake up
the process 4 add to the queue
the process 5 will wake up
the process 5 add to the queue
the process 6 will wake up
the process 6 add to the queue
the process 7 will wake up
the process 7 add to the queue
main: fork ok,now need to wait pids.
the process 2 will sleep
the process 7 delete from the queue
the process 7 will run
child pid 7, acc 968000, time 1003
the process 7 will be Zombie
the process 2 will wake up
the process 2 add to the queue
the process 6 delete from the queue
the process 6 will run
child pid 6, acc 4000, time 1008
the process 6 will be Zombie
the process 5 delete from the queue
the process 5 will run
child pid 5, acc 4000, time 1012
the process 5 will be Zombie
the process 4 delete from the queue
the process 4 will run
child pid 4, acc 4000, time 1018
the process 4 will be Zombie
the process 3 delete from the queue
the process 3 will run
child pid 3, acc 4000, time 1023
the process 3 will be Zombie
the process 2 delete from the queue
the process 2 will run
main: pid 3, acc 4000, time 1024
main: pid 4, acc 4000, time 1025
main: pid 5, acc 4000, time 1025
main: pid 6, acc 4000, time 1026
main: pid 7, acc 968000, time 1026
main: wait pids over
stride sched correct result: 1 1 1 1 242
the process 2 will be Zombie
the process 1 will wake up
the process 1 add to the queue
the process 1 delete from the queue
the process 1 will run
the process 1 add to the queue
the process 1 delete from the queue
all user-mode processes have quit.
```


