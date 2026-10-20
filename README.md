# 黄亚飞 · fei232401

重庆理工大学电气工程及其自动化本科，2027 届。正在学习和实践机器学习系统的调度与编排：Kubernetes 上训练与推理工作负载的协调，以及 LLM 推理服务的请求调度。

## 代表项目

> 两个代表项目目前为私有仓库，求职投递前再按需要公开。

### [elastic-workload-operator](https://github.com/fei232401/elastic-workload-operator)

Go / controller-runtime / PyTorch / Kueue。用 CRD + Operator 根据推理 TTFT 在训练和推理之间调整副本：目标先持久化再幂等收敛；训练侧使用 StatefulSet + torchrun 弹性训练，副本变化前执行“存盘 → 释放 → 扩容”握手。

验证范围是 Kind 单节点、CPU 小模型训练和 busybox 推理占位负载，证明的是编排协议与恢复语义，不代表 GPU、NCCL 或多节点存储性能。

### [inference-platform](https://github.com/fei232401/inference-platform)

Python / FastAPI / PostgreSQL / React / vLLM。单机 LLM 推理服务平台，Router 负责后端选择、并发准入、超时预算、审计、短 TTL 控制面缓存和前缀亲和路由。

在 RTX 4070 Laptop、两个 vLLM 实例并人为限制 KV 容量的实验中，3B 模型的前缀亲和策略提高了缓存命中并降低 TTFT；结果只适用于该硬件、模型和负载条件。

## 研究原型

- [elastic-scheduler-v2](https://github.com/fei232401/elastic-scheduler-v2)：训练与推理资源分配策略仿真。
- [kv-inference-scheduler](https://github.com/fei232401/kv-inference-scheduler)：KV Cache 感知路由实验。
- [elastic-topo-scheduler](https://github.com/fei232401/elastic-topo-scheduler)：拓扑放置插件原型。

这些仓库保留早期研究过程，结论边界写在各自 README 顶部。

## 技术栈

Python、Go、Shell；Kubernetes、controller-runtime、Kind、Kueue、Docker；PyTorch DDP / torchrun、vLLM；FastAPI、PostgreSQL、Prometheus；React、TypeScript。
