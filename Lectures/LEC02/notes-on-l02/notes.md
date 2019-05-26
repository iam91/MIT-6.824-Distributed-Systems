- [linux线程间通信及同步机制总结](https://blog.csdn.net/a987073381/article/details/52029070)
- [RPC](https://www.ibm.com/support/knowledgecenter/en/ssw_aix_71/com.ibm.aix.progcomc/ch8_rpc.htm)

## 线程

### 基础
- 共享内存空间
- 线程独立的状态
  - 程序计数器
  - 寄存器
  - 栈

### 线程数量选择
- 程序架构驱动
  - 每个client一个线程
  - 每个后台任务一个线程
- 由多核并行需求驱动
  - Go运行时每个核一个活跃线程
- 由IO并发驱动
  - 由延迟和容量决定，线程数达到总吞吐量不再提升

### 多线程挑战
- 共享数据
- 线程间协作
- 并发粒度
  - 粗粒度：简单，并发度小
  - 细力度：并发度高，更多竞争和更大死锁可能性

## RPC

### rpc与http的区别与关系
- 如果把一个http servlet容器上封装一层服务发现和函数代理调用，那它就已经可以做一个rpc框架了
- 良好的rpc调用是面向服务的封装，针对服务的可用性和效率等都做了优化。单纯使用http调用则缺少了这些特性
- http可作为rpc的通信协议
- restful可以看作一种rpc