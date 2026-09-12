# 黄亚飞 · fei232401

> **算力集群调度与编排** ｜ 云原生 · AI Infra
> 2027 届本科 · 重庆理工大学 电气工程及其自动化

关注共享 GPU 集群上的资源调度：**训练与推理如何共存、让渡与归还如何收敛、网络与算力如何不互相踩踏**。

---

## 代表项目

### 1 · 训推弹性调度系统 —— 四层合一的 GPU 弹性调度

一个从算法决策到 K8s 落地的完整闭环，四层各司其职：

| 层 | 仓库 | 解决什么 |
|---|---|---|
| 算法（决策：让几张卡） | [elastic-scheduler-v2](https://github.com/fei232401/elastic-scheduler-v2) | 潮汐流量下训练逐档让渡 GPU 给推理、保护 SLO、回落归还 |
| 平台（执行：副本数） | [elastic-workload-operator](https://github.com/fei232401/elastic-workload-operator) | 单 CRD 声明训练+推理，声明式目标收敛消除非原子丢卡 |
| 内核（placement：摆哪张卡） | [elastic-topo-scheduler](https://github.com/fei232401/elastic-topo-scheduler) | kube-scheduler 拓扑感知打分 + 损失最小抢占 |
| 数据面（请求路由） | [kv-inference-scheduler](https://github.com/fei232401/kv-inference-scheduler) | KV 亲和 × 负载 × 内存压力三因子路由 + 三级 KV 分层 |

### 2 · [tidal-fabric](https://github.com/fei232401/tidal-fabric) —— 训推混部的网络让渡

"让卡不等于让路"：量化训练 NCCL 大象流对推理 KV 搬运的挤压，并提出**让渡前的静态 PFC 死锁预检**
（`O(V+E)` 环检测，单次 **12.5 µs**，从事后 watchdog 恢复变为**事前规避**）。

---

## 技术栈

**语言** Go · Python（确定性离散事件仿真）
**容器与调度** Kubernetes · kube-scheduler Scheduling Framework · Kueue · Volcano · KWOK · Helm · controller-runtime
**AI 推理** vLLM · KV Cache / Prefix Caching · 模型量化 · GPU 性能压测
**可观测** Prometheus · Grafana · Loki · AlertManager · PromQL
**CI/CD** Jenkins · ArgoCD · Argo Rollouts · Docker
**网络** RDMA / RoCE · NCCL · PFC / ECN

---

## 方法

- **确定性优先**：核心结论跑在可复现的确定性仿真上，再用真机常数校准；
- **证据分级**：每个数字标注它是**实测 / 仿真 / 估算**，不把估算写成实测；
- **暴露 Reality Gap**：主动报告"离线最优、现场反噬"这类反直觉结果，而不是只留好看的数。

---

📫 `599512147@qq.com`
