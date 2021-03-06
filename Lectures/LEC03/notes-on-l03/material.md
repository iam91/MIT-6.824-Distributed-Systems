# 设计概览

## 假设
- 系统搭建在廉价商用计算机集群上，需要一定容错能力
- 主要支持大文件
  - 大部分文件100M或更大，提供优化
  - 几G文件常见，提供优化
  - 小文件不作优化
- 主要工作场景
  - 大量大文件流式读取，提供优化
  - 小文件随机读取，通常将多个小文件随机读取任务排序成批处理
  - 较大数据量连续追加；一旦写入，较少改动
- 良好支持并发读取与写入  
- 注重大吞吐量任务而非实时响应

## 元数据

### 元数据类型
master主要存储三种元数据：
- 1.文件和文件块命名空间
- 2.文件到文件块的映射
- 3.文件块位置

### 元数据存储
- master启动后所有元数据在内存中存储
- 1、2两类元数据在master本地硬盘中以operation log方式持久化
- 3类元数据在master启动时向chunkserver请求获取