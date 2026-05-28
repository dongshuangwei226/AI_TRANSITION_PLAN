# 第 4 周:Transformer + Hugging Face 生态

## 本周目标
- 深入理解 Transformer 架构(Encoder/Decoder/Decoder-only)
- 熟练使用 Hugging Face transformers / datasets / tokenizers
- 完成中文 BERT 微调:文本分类任务
- 理解"预训练 + 微调"范式
- 掌握 LLM 基础原理:Token、Embedding、Attention、生成

## 前置准备
- [ ] 完成 Week 1-3
- [ ] 安装:`pip install transformers datasets tokenizers accelerate evaluate`
- [ ] 注册 Hugging Face 账号并配置 token
- [ ] (国内)配置镜像:`export HF_ENDPOINT=https://hf-mirror.com`

---

## Day 1 - Transformer 深入

**主题**:把 Week 3 的 Transformer 直觉变成深入理解

### 上午(3h)理论学习
- [ ] 完整阅读 The Illustrated Transformer 中文版(1.5h)
      https://blog.csdn.net/qq_41664845/article/details/84969266
- [ ] 观看李宏毅 Transformer 视频(1.5h)
      https://www.bilibili.com/video/BV1Wv411h7kN
- [ ] 重点掌握:
  - 输入 → Token → Embedding + Position
  - Self-Attention 的 Q/K/V 计算
  - Multi-Head 拆分与拼接
  - Encoder vs Decoder 的区别(Masked Attention)
  - Layer Normalization + 残差连接

### 下午(3h)动手实践
- [ ] 从零实现 Mini-GPT(2h)
  - 参考 Karpathy nanoGPT 简化版
  - 训练在莎士比亚文本上生成
  - 提交到 `week04/day1/mini_gpt.py`
- [ ] 用 PyTorch `nn.TransformerEncoder` 做文本分类(1h)
  - 与 Day 1 Encoder-only 模型对照

### 晚上(2h)整理与提交
- [ ] 整理 Transformer 架构图(可手绘 + 数字标注)
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] Mini-GPT 训练脚本
- [ ] Transformer 架构图

### 推荐资源
- Karpathy《Let's build GPT》:https://www.youtube.com/watch?v=kCc8FmEb1nY
- nanoGPT:https://github.com/karpathy/nanoGPT

---

## Day 2 - Hugging Face 生态总览

**主题**:transformers / datasets / tokenizers 三件套

### 上午(3h)理论学习
- [ ] HF Hub 介绍(1h)
  - Model Hub / Dataset Hub / Spaces
  - 模型卡(Model Card)
  - License 概念(尤其商用许可)
- [ ] transformers 库结构(1h)
  - AutoModel / AutoTokenizer / AutoConfig
  - Pipeline 高阶 API
  - 加载本地模型 vs 从 Hub 加载
- [ ] tokenizers 库(1h)
  - 分词器原理:BPE / WordPiece / SentencePiece
  - 中文分词的特殊性
  - 特殊 Token:[CLS]、[SEP]、[PAD]、[MASK]、[UNK]

### 下午(3h)动手实践
- [ ] Pipeline 速通(1h)
  - 文本分类:`pipeline("sentiment-analysis")`
  - 命名实体识别:`pipeline("ner")`
  - 问答:`pipeline("question-answering")`
  - 文本生成:`pipeline("text-generation")`
  - 翻译:`pipeline("translation")`
  - 提交到 `week04/day2/pipeline_demo.ipynb`
- [ ] 手动加载模型与分词器(1h)
  - 加载 `bert-base-chinese` 和 `Qwen2.5-0.5B`
  - 探索 tokenizer:`encode` / `decode` / 中文分词结果
- [ ] datasets 库基础(1h)
  - `load_dataset` 加载 Hub 数据集
  - `map` / `filter` / `train_test_split`

### 晚上(2h)整理与提交
- [ ] 整理 HF 生态速查表
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] HF Pipeline 完整示例
- [ ] 中英文 tokenizer 对比实验

### 推荐资源
- HF Course 中文版:https://huggingface.co/learn/nlp-course/zh-CN/chapter1/1
- HF 镜像站:https://hf-mirror.com

---

## Day 3 - 微调 BERT:中文文本分类

**主题**:本周最重要的实战 —— "预训练 + 微调"范式

### 上午(3h)理论学习
- [ ] 预训练 + 微调范式(1h)
  - 为什么有效:大规模无监督 + 小规模有监督
  - BERT 的 MLM 任务
  - 微调 vs Prompt(为后面 LLM 铺垫)
- [ ] HF Trainer API(2h)
  - `TrainingArguments` 参数详解
  - `Trainer` 类
  - 评估指标 `compute_metrics`
  - 数据预处理流程

### 下午(3h)动手实践
- [ ] 微调 `bert-base-chinese` 做中文情感分析(3h)
  - 数据集:ChnSentiCorp(`load_dataset("seamew/ChnSentiCorp")`)或自建
  - 完整流程:加载分词器 → tokenize 数据 → 加载模型 → 配置 Trainer → 训练 → 评估
  - 目标:验证集准确率 ≥ 90%
  - 提交到 `week04/day3/bert_finetune.py`

### 晚上(2h)整理与提交
- [ ] 整理"BERT 微调完整模板"代码
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] BERT 中文情感分析微调完整代码
- [ ] 训练日志 + 评估指标

### 推荐资源
- HF Course 第 3-4 章:https://huggingface.co/learn/nlp-course/zh-CN/chapter3/1
- 《BERT 实战》(可选)

---

## Day 4 - 不同 NLP 任务的微调

**主题**:横向扩展到命名实体识别、问答、文本生成

### 上午(3h)理论学习
- [ ] NLP 任务分类(1.5h)
  - 单文本分类(情感、主题)
  - 双文本分类(NLI 自然语言推断)
  - 序列标注(NER、词性标注)
  - 抽取式问答(SQuAD)
  - 生成式任务(摘要、翻译)
- [ ] 不同任务的模型 Head(1.5h)
  - `AutoModelForSequenceClassification`
  - `AutoModelForTokenClassification`
  - `AutoModelForQuestionAnswering`
  - `AutoModelForCausalLM` / `AutoModelForSeq2SeqLM`

### 下午(3h)动手实践
- [ ] 微调中文 NER(1.5h)
  - 数据集:人民日报 NER 数据集
  - 用 `bert-base-chinese`
  - 提交到 `week04/day4/ner.py`
- [ ] 跑一个文本摘要(1h)
  - 用 `csebuetnlp/mT5_multilingual_XLSum`
  - 体会 Seq2Seq 任务
- [ ] 加载并对话一个 Decoder-only 模型(30min)
  - `Qwen/Qwen2.5-0.5B-Instruct` 或 `Qwen/Qwen2.5-1.5B-Instruct`
  - 用 `generate` 函数

### 晚上(2h)整理与提交
- [ ] 整理"不同任务的微调对比"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] NER 微调代码
- [ ] 摘要 + 对话 Demo

### 推荐资源
- HF Course 第 7 章

---

## Day 5 - LLM 基础原理 + 生成参数

**主题**:为 Week 5+ 的 LLM 应用开发铺路

### 上午(3h)理论学习
- [ ] 现代 LLM 概览(1h)
  - GPT / Claude / Gemini / Qwen / DeepSeek / Llama
  - Decoder-only 架构为何成为主流
  - 模型规模与能力的关系(Scaling Law)
- [ ] LLM 训练阶段(1h)
  - 预训练(Pre-training)
  - 监督微调(SFT)
  - 强化学习(RLHF / DPO)
  - 各阶段产出的模型差异(Base vs Chat)
- [ ] 生成参数(1h)
  - `temperature`:随机性
  - `top_p` / `top_k`:采样策略
  - `max_tokens`:输出长度
  - `frequency_penalty` / `presence_penalty`:重复惩罚
  - `stop`:停止词

### 下午(3h)动手实践
- [ ] 用 transformers 加载小型 LLM(1.5h)
  - `Qwen/Qwen2.5-1.5B-Instruct`(本地能跑)
  - 实现一个简单对话循环
  - 调试不同 temperature / top_p 效果
  - 提交到 `week04/day5/local_llm.py`
- [ ] 流式输出实现(1h)
  - 用 `TextStreamer`
  - 体会 streaming 在用户体验上的重要性
- [ ] 探索 chat template(30min)
  - `tokenizer.apply_chat_template`
  - 了解不同模型的 prompt 格式差异

### 晚上(2h)整理与提交
- [ ] 整理"LLM 生成参数调优指南"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 本地 LLM 对话脚本
- [ ] 生成参数实验报告

### 推荐资源
- 《How GPT Works》:https://jalammar.github.io/how-gpt3-works-visualizations-animations/
- Qwen 文档:https://qwen.readthedocs.io/

---

## Day 6 - 本周综合项目:智能简历筛选器

**主题**:用 BERT 微调 + LLM 生成,做一个实用的小工具

### 上午(3h)需求与设计
- [ ] 需求:输入一份简历文本,输出
  - 简历类别(前端/后端/AI/产品/其他)—— 用微调 BERT 分类
  - 关键技能列表 —— 用 NER 或 LLM 抽取
  - 简短点评 —— 用本地 LLM 生成
- [ ] 项目结构设计(1h)
  ```
  resume_screener/
  ├── README.md
  ├── data/
  │   └── resumes.csv         # 自己造或网上找
  ├── src/
  │   ├── classifier.py       # BERT 分类
  │   ├── extractor.py        # NER 抽取
  │   ├── reviewer.py         # LLM 点评
  │   └── pipeline.py         # 串联
  └── app.py                  # gradio 简单界面
  ```
- [ ] 准备数据(2h)
  - 至少 100 条简历样本(可用 LLM 生成)
  - 标注类别

### 下午(3h)动手实践
- [ ] 实现 BERT 分类器(1.5h)
- [ ] 实现技能抽取(1h)
- [ ] 实现 LLM 点评(30min)

### 晚上(2h)集成与提交
- [ ] 用 Gradio 做一个简单界面
      https://www.gradio.app/
- [ ] 完善 README
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 完整可运行的简历筛选器
- [ ] Gradio 界面截图

### 推荐资源
- Gradio 中文教程:https://www.gradio.app/zh-cn/

---

## Day 7 - 复盘 + 自由学习

### 上午(3h)复盘
- [ ] 填写"本周复盘"
- [ ] 整理所有本周项目
- [ ] 自评里程碑

### 下午(3h)自由学习
- 选项 A:再做一个 HF 实战项目(摘要 / 翻译)
- 选项 B:把 Mini-GPT 训练得更好
- 选项 C:复习薄弱点
- 选项 D:休息 ✅

### 晚上(2h)
- [ ] 预读 `week-05-prompt-llm-api.md`(进入主战场)
- [ ] 充值 DeepSeek 或通义千问 API 额度(10-20 元够用一周)
- [ ] (可选)申请 OpenAI / Anthropic API key

---

## 本周里程碑检查

- [ ] 能解释 Transformer 的核心组件
- [ ] 能用 HF Trainer 微调一个分类模型,准确率 ≥ 90%
- [ ] 能在本地用 transformers 加载并运行 LLM
- [ ] 理解 temperature / top_p 等生成参数
- [ ] 有 1 个可演示的 HF 实战项目

## 本周资源汇总

### 视频
- 李宏毅 Transformer 课程
- Andrej Karpathy 系列(英文)
- 沐神《动手学深度学习》Transformer 章节

### 文档
- HF Course 中文版:https://huggingface.co/learn/nlp-course/zh-CN
- HF transformers 文档:https://huggingface.co/docs/transformers/index
- HF 镜像:https://hf-mirror.com

### 书籍
- 《Natural Language Processing with Transformers》(O'Reilly,强烈推荐)

---

## 本周复盘

### 完成度自评
- 整体完成度:____ / 7 天
- 学习时长统计:____ 小时
- GitHub commit 数:____
- BERT 微调最佳准确率:____

### 收获最大的三个点
1.
2.
3.

### 最大的卡点
-

### 是否能独立完成 LLM 调用
- [ ] 是 ✅
- [ ] 还需要练习

### 下周(进入主战场)需要重点关注
-
