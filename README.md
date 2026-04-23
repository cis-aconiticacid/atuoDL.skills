
# AutoDL API 技能 (Skill)

## 项目简介 (Introduction)
本项目提供了一个专门用于与 AutoDL GPU 云平台交互的自动化技能 (Skill)。它能够理解用户的自然语言指令，并自动生成可直接运行的 Python 代码，帮助用户通过官方的 [REST API](https://api.autodl.com) 轻松管理云端 GPU 资源。

当用户在对话中提及“AutoDL”、“GPU 租赁 (GPU Rental)”、“开/关机”、“释放实例 (Releasing Instances)”或“弹性部署 (Elastic Deployments)”等相关词汇时，该技能便会被激活，充当用户与 AutoDL 后端服务之间的桥梁。

## 主要功能 (Key Features)

该技能集成了对 AutoDL 三大核心资源模块的操作支持：

* **常规账户与存储管理 (Common Management)：** 支持查询账户余额以及切换专属 NFS 或文件存储。
* **Pro 容器实例管理 (Container Instance Pro Management)：** 专为持久化实例 (Persistent Instances) 设计，支持从创建、状态查询到开机、关机及最终释放的完整生命周期管理。
* **弹性部署管理 (Elastic Deployment Management)：** 适用于需要自动扩缩容 (Auto-scaling) 和批量任务 (Batch Jobs) 的企业级场景。支持创建/停止部署、动态调整副本数 (Replica Count) 以及配置调度黑名单 (Scheduling Blacklists)。

## 工作原理 (How It Works)

该技能内置了 AutoDL API 的各项技术规范与业务逻辑，确保生成的代码准确且安全：

1.  **智能参数匹配：** 技能掌握平台专属的规格代码（如 GPU 型号 `h800`、地域代码 `westDC2`）、单位约定（价格以“毫”计，内存以字节计）以及 CUDA 版本 (CUDA Version) 编码。
2.  **安全的操作流：** 强制遵循平台的依赖逻辑，例如在释放实例前会先引导执行关机代码；在未提供 UUID 时会先调用列表接口进行确认。
3.  **标准化代码生成：** 生成的 Python 代码会自动包含必要的 HTTP 方法（如 `requests.post` 等）、响应打印逻辑以及 `Authorization` 头部占位符，用户只需填入自己的 Developer Token 即可运行。

## 项目结构 (Repository Structure)

* `SKILL.md`: 核心技能提示词 (Prompt) 与行为约束，定义了 AI 在处理 AutoDL 相关请求时的默认动作、端点 (Endpoints) 和工作流。
* `references/`: 存放各模块详细的 API 参考文档，包含完整的请求/响应模式 (Response Schemas) 和参数表，作为代码生成的底层依赖库。
