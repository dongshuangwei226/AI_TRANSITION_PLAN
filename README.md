# Java → AI 应用工程师 转型计划

> 14 周全职学习路线 · 每日 8 小时 · 每周一至周五学新内容,周六综合实践,周日复盘休息

---

## 一、计划总览

| 阶段 | 周次 | 主题 | 核心产出 | 状态 |
|------|------|------|---------|------|
| 基础 | W01 | Python 速成 | Java↔Python 速查 + GitHub 仓库 | ⬜ |
| 基础 | W02 | 数学回顾 + ML 入门 | scikit-learn 完整流程 Demo | ⬜ |
| 基础 | W03 | PyTorch 基础 | MNIST/CIFAR 训练脚本 | ⬜ |
| 基础 | W04 | Transformer + HF | 微调 BERT 中文情感分析 | ⬜ |
| 核心 | W05 | Prompt + LLM API | 多 LLM API 封装 + Function Calling | ⬜ |
| 核心 | W06 | RAG 系统 | 完整 RAG Demo(切分/Embedding/检索/Rerank) | ⬜ |
| 核心 | W07 | Agent 与工具调用 | ReAct Agent + MCP 示例 | ⬜ |
| Java | W08 | Spring AI | Spring Boot + AI 智能问答模块 | ⬜ |
| Java | W09 | LangChain4j | AI Service 注解式开发示例 | ⬜ |
| 部署 | W10 | 本地模型部署 | Ollama + vLLM + FastAPI 服务 | ⬜ |
| 部署 | W11 | MLOps + LoRA | LangFuse 监控 + 7B 模型 LoRA 微调 | ⬜ |
| 项目 | W12 | 项目一:企业知识库 RAG | 完整可部署系统 + 博客 | ⬜ |
| 项目 | W13 | 项目二:Agent 代码审查助手 | 完整可部署系统 + 博客 | ⬜ |
| 项目 | W14 | 项目三 + 求职 | 第三个项目 + 简历 + 面试题 | ⬜ |

进度追踪方式:每完成一周,把 ⬜ 改成 ✅,并在对应 `week-XX-*.md` 文件末尾填写"本周复盘"。

---

## 二、三大里程碑项目

- [ ] **项目一**:企业知识库 RAG 系统(Spring AI + Milvus + Qwen)
- [ ] **项目二**:Agent 代码审查助手(LangChain + Function Calling + Git API)
- [ ] **项目三**:本地化部署的智能客服(Ollama + vLLM + FastAPI + Docker)

每个项目要求:GitHub 完整 README + 架构图 + 部署说明 + 至少 1 篇技术博客。

---

## 三、环境准备清单(一次性完成)

> 建议在 Week 1 Day 1 一次性完成以下安装与账号申请。

### 3.1 开发环境

| 类别 | 工具 | 版本 | 说明 |
|------|------|------|------|
| Python | Python 3.11 | 3.11.x | 不要装 3.12+,部分库兼容性问题 |
| 包管理 | Miniconda / Anaconda | 最新 | 推荐 Miniconda(轻量) |
| Java | JDK 17 / 21 | LTS | Spring AI 需要 JDK 17+ |
| 构建 | Maven 3.9+ / Gradle 8+ | 最新 | Java 项目构建 |
| IDE | VSCode + Python 插件 | 最新 | Python 主力 IDE |
| IDE | IntelliJ IDEA | 2024.1+ | Java 项目主力 IDE |
| 容器 | Docker Desktop | 最新 | 模型部署、向量库容器化 |
| 版本控制 | Git | 最新 | + GitHub 账号 |
| 终端 | Windows Terminal + PowerShell 7 | 最新 | 推荐 |

### 3.2 Python 关键库(到 Week 3 时分批安装,不必一次装齐)

```bash
# 基础三件套
pip install numpy pandas matplotlib scikit-learn jupyter

# 深度学习(Week 3)
pip install torch torchvision torchaudio
pip install transformers datasets tokenizers accelerate

# LLM 应用(Week 5-7)
pip install openai anthropic dashscope
pip install langchain langchain-community langchain-openai
pip install chromadb pymilvus
pip install fastapi uvicorn pydantic

# 监控与微调(Week 10-11)
pip install langfuse mlflow
pip install peft bitsandbytes
```

### 3.3 账号与 API Key 申请

| 服务 | 用途 | 申请地址 | 备注 |
|------|------|---------|------|
| OpenAI | GPT-4 / Embedding | https://platform.openai.com | 需国外信用卡,可用代理 |
| Anthropic | Claude API | https://console.anthropic.com | 需国外信用卡 |
| 通义千问 DashScope | 国内主力 LLM | https://dashscope.aliyun.com | 推荐,有免费额度 |
| DeepSeek | 性价比高 | https://platform.deepseek.com | 国内可用,推荐 |
| 智谱 GLM | 备选 | https://open.bigmodel.cn | 国内可用 |
| Hugging Face | 模型与数据集 | https://huggingface.co | 必备 |
| 魔搭 ModelScope | 国内模型镜像 | https://modelscope.cn | 国内备用 |
| LangSmith / LangFuse | LLM 应用监控 | https://langfuse.com | 自托管或云端 |
| GitHub | 代码托管 | https://github.com | 必备 |

### 3.4 向量数据库(Docker 镜像,Week 6 用)

```bash
# Chroma(轻量,本地开发推荐)
docker run -p 8000:8000 chromadb/chroma

# Milvus(生产级)
# 参考官方 docker-compose
# https://milvus.io/docs/install_standalone-docker.md

# Qdrant(Rust 实现,性能好)
docker run -p 6333:6333 qdrant/qdrant
```

### 3.5 本地模型工具(Week 10 用)

- **Ollama**: https://ollama.com  下载 Windows 安装包
- **LM Studio**: https://lmstudio.ai  图形化本地模型管理
- **vLLM**: 仅 Linux/WSL2 支持,需 GPU

### 3.6 推荐硬件

- 最低:16GB 内存,无 GPU 也可(用云端 API + Colab)
- 推荐:32GB 内存 + NVIDIA RTX 3060 12GB 及以上(可跑 7B 模型)
- 替代:Google Colab Pro / Kaggle / 阿里云 PAI-DSW(有免费 GPU)

---

## 四、使用说明

1. **每天开始前**:打开当周 `week-XX-*.md`,查看 Day N 清单
2. **学习过程中**:勾选已完成的 checkbox
3. **每天结束前**:
   - 复制 `daily-summary-template.md` 内容
   - 粘贴到 `daily-logs/YYYY-MM-DD.md` (建议自己建 `daily-logs/` 子目录)
   - 填写当日总结
4. **每周日**:在当周文件末尾填写"本周复盘"
5. **遇到卡点**:不要超过 2 小时,直接跳过或简化,周末再补

---

## 五、关键学习原则

1. **重应用,轻数学**:你是要做 AI 应用工程师,不是算法科学家
2. **代码先行**:任何概念都要落到一段可运行的代码上
3. **GitHub 即作品集**:每天都要有 commit
4. **不追新论文**:Transformer / RAG / Agent 三块吃透足够
5. **发挥 Java 优势**:Spring AI / LangChain4j 是你区别于纯 Python 转型者的护城河
6. **每周一总结**:把 Java 经验与 AI 知识对照(如 Spring Bean ↔ LangChain Runnable)

---

## 六、目录结构

```
ai-transition-plan/
├── README.md                          # 本文件
├── 00-overview.md                     # 整体路线图与核心策略
├── daily-summary-template.md          # 每日总结模板
├── week-01-python-basics.md
├── week-02-math-ml-intro.md
├── week-03-pytorch.md
├── week-04-transformer-hf.md
├── week-05-prompt-llm-api.md
├── week-06-rag.md
├── week-07-agent.md
├── week-08-spring-ai.md
├── week-09-langchain4j.md
├── week-10-model-deploy.md
├── week-11-mlops.md
├── week-12-project-rag.md
├── week-13-project-agent.md
├── week-14-project-deploy-job.md
└── daily-logs/                        # 建议自建,存放每日总结
    └── YYYY-MM-DD.md
```

---

**开始日期**:____________
**预计完成日期**:____________
**当前进度**:Week __ / 14
