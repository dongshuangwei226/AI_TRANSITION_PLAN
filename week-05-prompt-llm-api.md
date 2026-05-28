# 第 5 周:Prompt 工程 + LLM API 实战 ⭐ 主战场开始

## 本周目标
- 掌握 Prompt Engineering 核心方法论
- 熟练调用 OpenAI / Anthropic / DeepSeek / 通义千问 等主流 LLM API
- 实现 Function Calling 与 Structured Output
- 理解 Token 计量与成本控制
- 封装一个统一的 LLM 客户端(对照 Spring 的抽象思想)

## 前置准备
- [ ] 完成 Week 1-4
- [ ] 至少有 1 个可用的 LLM API key(推荐 DeepSeek + 通义千问)
- [ ] 安装:`pip install openai anthropic dashscope tiktoken`
- [ ] 创建 `.env` 文件存放 API key(并加入 .gitignore!)

---

## Day 1 - Prompt Engineering 基础

**主题**:写出有效 Prompt 的核心方法

### 上午(3h)理论学习
- [ ] OpenAI Prompt Engineering 官方指南(1.5h)
      https://platform.openai.com/docs/guides/prompt-engineering
- [ ] Anthropic Prompt Engineering 指南(1.5h)
      https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering
- [ ] 重点掌握:
  - **清晰指令**:具体、量化、给出格式
  - **角色设定**:System Prompt 的作用
  - **少样本示例(Few-shot)**:给 2-3 个例子
  - **思维链(CoT)**:"让我们一步步思考"
  - **分隔符**:用 `"""` 或 XML 标签区分指令与内容
  - **限制输出格式**:JSON / Markdown / 列表

### 下午(3h)动手实践
- [ ] 同一个任务,5 种 Prompt 方式对比(2h)
  - 任务:从一段商品评论中抽取情感、关键问题、改进建议
  - 用 Zero-shot / Few-shot / CoT / 角色扮演 / 结构化输出 五种方式
  - 记录每种方式的输出质量
  - 提交到 `week05/day1/prompt_compare.md`
- [ ] Prompt 调试技巧(1h)
  - 用 OpenAI Playground / 通义千问 Web 调试
  - 学会"逐步追问"调试错误输出

### 晚上(2h)整理与提交
- [ ] 整理"Prompt 模式速查":10 种常用模式
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] Prompt 5 方式对比报告
- [ ] Prompt 速查表

### 推荐资源
- OpenAI 指南(必读):https://platform.openai.com/docs/guides/prompt-engineering
- Anthropic 指南(必读):https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering
- Prompt Engineering Guide:https://www.promptingguide.ai/zh

---

## Day 2 - LLM API 调用基础

**主题**:OpenAI / DashScope / DeepSeek 三大主流 API

### 上午(3h)理论学习
- [ ] OpenAI Chat Completions API(1h)
      https://platform.openai.com/docs/api-reference/chat
  - 请求参数:`model` / `messages` / `temperature` / `max_tokens` / `top_p`
  - 响应结构:`choices` / `usage` / `finish_reason`
  - 错误码与重试策略
- [ ] DashScope API(通义千问)(1h)
      https://help.aliyun.com/zh/dashscope/
  - 兼容 OpenAI SDK 的调用方式
- [ ] DeepSeek API(1h)
      https://api-docs.deepseek.com/zh-cn/
  - 高性价比首选
  - `deepseek-chat` vs `deepseek-reasoner`

### 下午(3h)动手实践
- [ ] 三种 API 各调通一次(1h)
  - 用相同 prompt 比较输出
  - 提交到 `week05/day2/api_compare.py`
- [ ] 实现一个统一 LLM 客户端抽象(2h)
  - 类似 Spring AI `ChatClient` 思想
  - 接口:`chat(messages, model, **kwargs) -> ChatResponse`
  - 用 Pydantic 定义统一的请求/响应模型
  - 支持 OpenAI / DashScope / DeepSeek 三个后端
  - 提交到 `week05/day2/llm_client/`

### 晚上(2h)整理与提交
- [ ] 整理"LLM 客户端封装设计文档"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 统一 LLM 客户端代码
- [ ] 三大 API 对比报告

### 推荐资源
- OpenAI Python SDK:https://github.com/openai/openai-python
- LiteLLM(统一封装库,可参考设计):https://github.com/BerriAI/litellm

---

## Day 3 - 流式输出 + Token 计量 + 成本控制

**主题**:工程化必备技能

### 上午(3h)理论学习
- [ ] Streaming 原理与实现(1.5h)
  - SSE(Server-Sent Events)协议
  - OpenAI / DashScope 的 stream 参数
  - Python 异步迭代器
- [ ] Token 计量(1.5h)
  - 什么是 Token,中英文 Token 差异
  - tiktoken 库使用
  - 不同模型的定价(input / output / cache)
  - 上下文长度限制(8K / 32K / 128K / 1M)

### 下午(3h)动手实践
- [ ] 给统一客户端添加 Streaming 支持(1.5h)
  - 接口:`chat_stream(messages, model) -> Iterator[str]`
  - 支持三个后端
  - 命令行流式打印
- [ ] 实现 Token 计数与成本估算(1h)
  - 调用前估算 token 数
  - 调用后从 `usage` 字段读取实际值
  - 维护一个简单的成本统计表
- [ ] 异步并发调用(30min)
  - 用 `asyncio` 同时发起 10 个请求
  - 体会异步的吞吐优势

### 晚上(2h)整理与提交
- [ ] 整理"LLM API 工程化清单"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 流式 LLM 客户端
- [ ] Token 与成本统计工具
- [ ] 异步并发示例

### 推荐资源
- tiktoken:https://github.com/openai/tiktoken
- OpenAI Cookbook 异步示例

---

## Day 4 - Function Calling + Structured Output

**主题**:让 LLM 可控、可程序化集成

### 上午(3h)理论学习
- [ ] Function Calling / Tool Use 原理(1.5h)
      https://platform.openai.com/docs/guides/function-calling
  - 模型为何能"调用函数"(其实是输出结构化 JSON)
  - JSON Schema 描述工具
  - 多轮工具调用流程
- [ ] Structured Output(1.5h)
  - `response_format={"type": "json_object"}`
  - OpenAI Structured Outputs(强类型 JSON)
  - 用 Pydantic 定义输出 schema
  - **类比 Java**:像 Jackson 的强类型反序列化

### 下午(3h)动手实践
- [ ] 实现一个天气查询 Bot(1.5h)
  - 定义 `get_weather(city)` 函数
  - 用 Function Calling 让 LLM 调用
  - 处理多轮工具调用(用户 → LLM → 工具 → LLM → 用户)
  - 提交到 `week05/day4/weather_bot.py`
- [ ] 实现简历信息抽取(1.5h)
  - 输入:简历文本
  - 输出:Pydantic 模型 `Resume(name, age, skills, experience)`
  - 用 Structured Output 保证 JSON 合法
  - 提交到 `week05/day4/resume_extract.py`

### 晚上(2h)整理与提交
- [ ] 整理"Function Calling 工程模板"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 天气查询 Bot(含工具调用)
- [ ] 简历信息抽取器(结构化输出)

### 推荐资源
- OpenAI Function Calling 文档(必读)
- Instructor 库(基于 Pydantic 的结构化输出):https://github.com/jxnl/instructor

---

## Day 5 - 高级 Prompt 模式 + Prompt 安全

**主题**:Prompt 工程的进阶与防御

### 上午(3h)理论学习
- [ ] 高级 Prompt 模式(1.5h)
  - Chain-of-Thought(CoT)与 Self-Consistency
  - Tree-of-Thoughts(ToT,知道即可)
  - ReAct(推理 + 行动)(为 Week 7 Agent 铺路)
  - Self-Reflection / Self-Critique
  - 多轮 Prompt 拆解复杂任务
- [ ] Prompt 安全(1.5h)
  - Prompt Injection(注入攻击)
  - Jailbreak(越狱)
  - 数据泄露风险
  - 防御策略:输入过滤、输出过滤、System Prompt 加固

### 下午(3h)动手实践
- [ ] 用 CoT 解决数学应用题(1h)
  - 对比有无 CoT 的准确率
  - 推荐用 DeepSeek-Reasoner 体验"推理模型"
- [ ] 实现一个能"自我反思"的代码生成器(1.5h)
  - LLM 生成代码 → 自我审查 → 修复 → 输出
  - 提交到 `week05/day5/self_refine.py`
- [ ] Prompt 注入实验(30min)
  - 故意构造注入 prompt
  - 测试不同模型的鲁棒性
  - 尝试加固 System Prompt

### 晚上(2h)整理与提交
- [ ] 整理"高级 Prompt 模式 + 安全清单"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] CoT / Self-Refine 示例
- [ ] Prompt 安全实验报告

### 推荐资源
- OWASP LLM Top 10:https://owasp.org/www-project-top-10-for-large-language-model-applications/
- 论文阅读:CoT、ReAct(可选)

---

## Day 6 - 本周综合项目:智能邮件助手

**主题**:整合 Prompt + API + Function Calling + 结构化输出

### 上午(3h)需求与设计
- [ ] 需求(1h)
  - 输入:一封邮件
  - 输出:
    - 邮件分类(工作/营销/账单/垃圾)
    - 紧急程度(高/中/低)
    - 关键信息抽取(发件人、主题、行动项、截止日期)
    - 自动生成回复草稿(三种风格:正式/友好/简短)
- [ ] 项目结构设计(2h)
  ```
  email_assistant/
  ├── README.md
  ├── .env.example
  ├── src/
  │   ├── client.py        # 上周的统一 LLM 客户端
  │   ├── classifier.py    # 邮件分类
  │   ├── extractor.py     # 信息抽取(Structured Output)
  │   ├── replier.py       # 回复生成
  │   └── tools.py         # Function Calling 工具(查日历等)
  ├── prompts/             # 所有 Prompt 模板
  │   ├── classify.txt
  │   ├── extract.txt
  │   └── reply.txt
  └── app.py               # Gradio 界面
  ```

### 下午(3h)动手实践
- [ ] 实现核心模块(2.5h)
- [ ] Gradio 界面(30min)

### 晚上(2h)收尾与提交
- [ ] 完善 README,加 GIF
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 完整可运行的邮件助手
- [ ] 至少 3 封邮件的端到端演示

---

## Day 7 - 复盘 + 自由学习

### 上午(3h)复盘
- [ ] 填写"本周复盘"
- [ ] 检查统一 LLM 客户端代码质量(为 Week 12 项目准备)
- [ ] 自评里程碑

### 下午(3h)自由学习
- 选项 A:写一篇博客《我封装的 LLM 客户端 vs LangChain》
- 选项 B:深度玩玩 Prompt 框架 dspy / promptflow
- 选项 C:复习薄弱点
- 选项 D:休息 ✅

### 晚上(2h)
- [ ] 预读 `week-06-rag.md`(重头戏)
- [ ] 启动 Docker,准备拉取 Chroma / Qdrant 镜像
- [ ] 安装:`pip install langchain langchain-community chromadb sentence-transformers`

---

## 本周里程碑检查

- [ ] 能写出符合 5 大 Prompt 原则的高质量 prompt
- [ ] 能用三种以上 LLM API 完成调用
- [ ] 能实现 Function Calling 多轮工具调用
- [ ] 能用 Pydantic 实现 Structured Output
- [ ] 有 1 个统一 LLM 客户端可复用到后续项目
- [ ] 有 1 个完整的 LLM 应用 Demo

## 本周资源汇总

### 文档(本周重点是读文档)
- OpenAI Cookbook:https://github.com/openai/openai-cookbook
- Anthropic Cookbook:https://github.com/anthropics/anthropic-cookbook
- Prompt Engineering Guide(中文):https://www.promptingguide.ai/zh
- DeepSeek 文档:https://api-docs.deepseek.com/zh-cn/

### 工具
- LiteLLM(参考其封装设计)
- Instructor(结构化输出)
- LangSmith / LangFuse(下周用)

### 阅读
- 论文《Chain-of-Thought Prompting Elicits Reasoning in Large Language Models》
- 论文《ReAct: Synergizing Reasoning and Acting in Language Models》

---

## 本周复盘

### 完成度自评
- 整体完成度:____ / 7 天
- 学习时长统计:____ 小时
- GitHub commit 数:____
- API 调用花费:____ 元

### 收获最大的三个点
1.
2.
3.

### 与 Java 经验的映射
- 统一 LLM 客户端 ↔ Spring AI ChatClient:
- Structured Output ↔ Jackson 反序列化:
- Function Calling ↔ ?:

### 最大的卡点
-

### 下周(RAG)需要重点关注
-
