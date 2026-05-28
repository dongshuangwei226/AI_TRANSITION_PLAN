# 整体路线图与核心策略

## 一、为什么是这条路线

### 1.1 你的起点
- Java 后端工程师
- 全职学习,每周 40+ 小时
- Python 能看懂代码但没写过项目
- 数学(线代/概率/微积分)基本忘光

### 1.2 你的目标
- **AI 应用工程师**(不是算法科学家)
- 用 LLM/RAG/Agent 构建业务应用
- 周期:14 周(约 3.5 个月)

### 1.3 核心策略
> **不必从零变成算法科学家,走"AI 应用工程师"路线**
> 用 Spring AI / LangChain4j 把 LLM 能力接入现有 Java 业务,性价比最高。

---

## 二、14 周路线图

```
┌─────────────────────────────────────────────────────────────┐
│  基础铺垫 (4 周)                                              │
│  W01 Python → W02 数学+ML → W03 PyTorch → W04 Transformer    │
├─────────────────────────────────────────────────────────────┤
│  LLM 核心 (3 周) ⭐ 主战场                                    │
│  W05 Prompt+API → W06 RAG → W07 Agent                        │
├─────────────────────────────────────────────────────────────┤
│  Java + AI 融合 (2 周) ⭐ 护城河                              │
│  W08 Spring AI → W09 LangChain4j                             │
├─────────────────────────────────────────────────────────────┤
│  部署与运维 (2 周)                                            │
│  W10 模型部署 → W11 MLOps + 微调                             │
├─────────────────────────────────────────────────────────────┤
│  项目作品集 + 求职 (3 周)                                     │
│  W12 RAG 项目 → W13 Agent 项目 → W14 部署项目 + 求职          │
└─────────────────────────────────────────────────────────────┘
```

---

## 三、各阶段精力分配

| 阶段 | 周数 | 占比 | 目的 |
|------|------|------|------|
| 基础铺垫 | 4 | 29% | 看懂代码、补基础工具 |
| LLM 核心 | 3 | 21% | 主战场,产出最多 Demo |
| Java+AI 融合 | 2 | 14% | 护城河,简历核心亮点 |
| 部署运维 | 2 | 14% | 后端工程师天然优势 |
| 项目+求职 | 3 | 21% | 落地产出 + 求职 |

---

## 四、Java 开发者的独特优势

| 优势 | 如何利用 | 应用周次 |
|------|---------|---------|
| 工程化思维 | MLOps、AI 中台、模型服务化 | W10-11 |
| Spring 生态 | Spring AI 直接上手 LLM 应用 | W08 |
| 分布式经验 | 分布式训练、向量数据库集群 | W06, W10 |
| 企业级开发 | AI 应用集成到现有业务系统 | W08-09, W12 |
| 接口设计 | LLM API 封装、Function Calling | W05, W07 |
| 性能调优 | 推理加速、缓存策略 | W10 |

---

## 五、Java vs Python 概念对照表

| Java | Python | 备注 |
|------|--------|------|
| Maven / Gradle | pip / poetry / conda | 包管理 |
| `null` | `None` | 空值 |
| `List<String>` | `list[str]` 或 `List[str]` | 类型注解 |
| `Map<K, V>` | `dict` | 字典 |
| Stream API | 列表推导式 + map/filter | 函数式 |
| `Optional<T>` | `Optional[T]` (typing) | 可空 |
| Spring Bean | 全局对象 + 依赖注入(可选 FastAPI Depends) | 依赖注入 |
| Spring AOP | 装饰器 `@decorator` | 切面 |
| Lombok | `dataclass` / `pydantic.BaseModel` | 样板代码 |
| JUnit | pytest / unittest | 测试 |
| SLF4J + Logback | `logging` 模块 / `loguru` | 日志 |
| JPA / MyBatis | SQLAlchemy / Tortoise ORM | ORM |
| Spring Boot | FastAPI / Flask | Web 框架 |
| `interface` | `Protocol` / `ABC` | 接口 |
| `try-with-resources` | `with` 语句 | 资源管理 |

---

## 六、Spring AI vs LangChain 概念对照

| Spring AI | LangChain (Python) | LangChain4j (Java) |
|-----------|-------------------|-------------------|
| `ChatClient` | `ChatModel` | `ChatLanguageModel` |
| `EmbeddingClient` | `Embeddings` | `EmbeddingModel` |
| `VectorStore` | `VectorStore` | `EmbeddingStore` |
| `RagAdvisor` | `RetrievalQA` Chain | `RetrievalAugmentor` |
| `@Tool` (Function Calling) | `@tool` | `@Tool` |
| `ChatMemory` | `ConversationBufferMemory` | `ChatMemory` |
| Advisor 链 | Chain / Runnable | AI Service |

---

## 七、风险与应对

| 风险 | 应对策略 |
|------|---------|
| 数学焦虑 | 应用方向只需懂概念,看不懂公式直接跳过 |
| 追新焦虑 | 基础打牢,W05-W07 三块吃透足够 |
| 代码量焦虑 | 早做项目,W05 就开始写 Demo |
| 求职焦虑 | W12 起每周投简历,边面试边补短板 |
| 算力焦虑 | 用云端 API + Colab + 阿里云免费 GPU |
| 信息过载 | 严格按本计划走,不要看到新教程就切换 |

---

## 八、每周通用节奏

```
周一 Day 1  →  新知识(理论 + 代码)
周二 Day 2  →  新知识(深入)
周三 Day 3  →  新知识(扩展)
周四 Day 4  →  新知识(进阶)
周五 Day 5  →  新知识(收尾)
周六 Day 6  →  本周综合项目实践(整合所有知识)
周日 Day 7  →  上午复盘 + 下午自由/休息
```

**每日 8 小时拆分**:
- 上午 09:00-12:00(3h):理论学习
- 下午 14:00-17:00(3h):动手实践
- 晚上 19:00-21:00(2h):整理 + GitHub + 总结

---

## 九、求职目标岗位关键词

- AI 应用工程师
- LLM 工程师 / 大模型应用工程师
- 智能体工程师 / Agent 工程师
- AI 中台工程师
- RAG 工程师
- AIGC 工程师
- Java + AI 复合型工程师(稀缺,溢价高)

---

## 十、最终交付物清单

完成 14 周后,你应该拥有:

- ✅ GitHub 仓库:`ai-learning`(每周代码 + 每日 commit)
- ✅ 三个完整项目(各自独立 GitHub 仓库 + README + 架构图 + 部署文档)
- ✅ 至少 3 篇技术博客(掘金/CSDN/公众号)
- ✅ 更新后的简历(突出 Java + AI 复合能力)
- ✅ 14 份周复盘文档
- ✅ 一份个人知识库(整理的所有笔记)
- ✅ 至少 5 场面试经验

---

下一步:打开 `week-01-python-basics.md` 开始 Day 1。
