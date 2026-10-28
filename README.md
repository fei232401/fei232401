# 黄亚飞 · fei232401

重庆理工大学电气工程及其自动化本科，2027 届。正在学习和实践机器学习系统的调度与编排：Kubernetes 上训练与推理工作负载的协调，以及 LLM 推理服务的请求调度。

## 代表项目

### [训推工作负载弹性编排：elastic-workload-operator](https://github.com/fei232401/elastic-workload-operator)

Go / controller-runtime / PyTorch。根据推理 TTFT 调整训练与推理副本，持久化目标并协调 checkpoint、释放和就绪。端到端交接验证基于单节点 Kind、CPU 训练与模拟推理负载，不代表 GPU 或多节点性能。

### [LLM 推理服务平台：inference-platform](https://github.com/fei232401/inference-platform)

Python / FastAPI / PostgreSQL / React。实现后端选路、请求准入、超时、审计和前缀亲和路由。亲和实验基于单卡双 vLLM 实例和限定 KV 容量；详细条件和结果见仓库。

## 技术栈

Python、Go、Shell；Kubernetes、controller-runtime、Kind、Kueue、Docker；PyTorch DDP / torchrun、vLLM；FastAPI、PostgreSQL、Prometheus；React、TypeScript。
