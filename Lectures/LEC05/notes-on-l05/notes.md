# 基于复制状态机（RSM）实现容错服务

## 策略
- 每个服务器按相同顺序执行相同命令
- 一个服务器失败，切换为另一个