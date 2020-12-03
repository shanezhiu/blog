Title: 死锁
Category: Programming
Tags: MySQL InnoDB，转载，操作系统
Authors: Wikipedia

### 什么是死锁
当两个以上的运算单元，双方都在等待对方停止运行，以获取系统资源，但是没有一方提前退出时，就称为死锁。在多任务操作系统中，操作系统为了协调不同行程，能否获取系统资源时，为了让系统正常运作，必须要解决这个问题。另一种相似的情况称为“活锁”。

### 死锁的必要条件

如果系统中只有一个进程，当然不会产生死锁。如果每个进程仅需求一种系统资源，也不会产生死锁。不过这只是理想状态，在现实中是可遇不可求的。

死锁的四个条件是：

+ 禁止抢占（no preemption）：系统资源不能被强制从一个进程中退出。
+ 持有和等待（hold and wait）：一个进程可以在等待时持有系统资源。
+ 互斥（mutual exclusion）：资源只能同时分配给一个行程，无法多个行程共享。
+ 循环等待（circular waiting）：一系列进程互相持有其他进程所需要的资源。

死锁只有在四个条件同时满足时发生，预防死锁必须至少破坏其中一项。

### 预防与消除

+ 监视进程
+ 出现死锁即杀死进程
+ 回滚进程

### 参考

[死锁-维基百科](https://zh.wikipedia.org/zh-cn/%E6%AD%BB%E9%94%81)