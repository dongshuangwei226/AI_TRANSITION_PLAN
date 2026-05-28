# 第 3 周:PyTorch 基础与深度学习入门

## 本周目标
- 理解神经网络与反向传播的工作机制
- 熟练使用 PyTorch:Tensor、autograd、nn.Module、DataLoader
- 完成 MNIST、CIFAR-10 两个完整训练项目
- 理解 CNN 的工作原理
- 学会读懂别人的 PyTorch 代码

## 前置准备
- [ ] 完成 Week 1-2
- [ ] 安装:`pip install torch torchvision torchaudio`
- [ ] 验证 PyTorch:`python -c "import torch; print(torch.__version__)"`
- [ ] (有 GPU)验证 CUDA:`python -c "import torch; print(torch.cuda.is_available())"`
- [ ] (无 GPU)注册 Google Colab 或 Kaggle 账号(免费 GPU)

---

## Day 1 - 神经网络基础 + PyTorch Tensor

**主题**:理解神经网络 + PyTorch 最核心的 Tensor

### 上午(3h)理论学习
- [ ] 观看 3Blue1Brown《神经网络》系列 P1-P4(B 站中文版)(2h)
      https://www.bilibili.com/video/BV1bx411M7Zx
  - 重点理解:神经元、激活函数、前向传播、反向传播的几何直觉
- [ ] 阅读 PyTorch 60 分钟入门教程 Part 1(1h)
      https://pytorch.org/tutorials/beginner/blitz/tensor_tutorial.html

### 下午(3h)动手实践
- [ ] PyTorch Tensor 全面练习(2h)
  - 创建 Tensor(从 list / NumPy / 全 0 / 全 1 / 随机)
  - 索引、切片、reshape、view、squeeze、unsqueeze
  - 算术运算、广播机制
  - CPU ↔ GPU 转移:`.to('cuda')`
  - Tensor ↔ NumPy 互转
  - 提交到 `week03/day1/tensor_basics.ipynb`
- [ ] autograd 实验(1h)
  - 演示 `requires_grad=True`、`.backward()`、`.grad`
  - 手动实现一个最简单的线性回归(用 autograd 自动求梯度)
  - 提交到 `week03/day1/autograd_demo.ipynb`

### 晚上(2h)整理与提交
- [ ] 整理"PyTorch Tensor 速查表"
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] Tensor 操作 notebook
- [ ] autograd 线性回归 notebook

### 推荐资源
- PyTorch 中文教程:https://pytorch.apachecn.org/
- 3Blue1Brown 神经网络:https://www.bilibili.com/video/BV1bx411M7Zx

---

## Day 2 - nn.Module + 训练流程模板

**主题**:用 PyTorch 构建神经网络的标准范式

### 上午(3h)理论学习
- [ ] PyTorch 训练五件套(1.5h)
  - 模型:`nn.Module`
  - 数据:`Dataset` + `DataLoader`
  - 损失:`nn.CrossEntropyLoss`、`nn.MSELoss`
  - 优化器:`optim.SGD`、`optim.Adam`
  - 训练循环:`forward → loss → backward → step`
- [ ] 常用层(1.5h)
  - `nn.Linear`、`nn.ReLU`、`nn.Sigmoid`、`nn.Softmax`
  - `nn.Dropout`、`nn.BatchNorm1d`
  - 网络的搭建方式:`nn.Sequential` vs 自定义 `forward`

### 下午(3h)动手实践
- [ ] 手写一个全连接神经网络分类 MNIST(2.5h)
  - 自定义 `Dataset`(或用 `torchvision.datasets.MNIST`)
  - 定义 `MLP` 类(2 个隐藏层)
  - 完整训练循环 + 验证集评估
  - 目标:验证集准确率 ≥ 96%
  - 提交到 `week03/day2/mnist_mlp.py`
- [ ] 学习 `torch.save` / `torch.load`(30min)
  - 保存与加载模型参数

### 晚上(2h)整理与提交
- [ ] 整理 PyTorch 训练模板代码,以后所有项目复用
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] MNIST MLP 完整训练代码
- [ ] 通用 PyTorch 训练模板

### 推荐资源
- 《动手学深度学习》PyTorch 版第 3 章:https://zh.d2l.ai/
- PyTorch 官方 60 分钟教程

---

## Day 3 - CNN + 图像分类

**主题**:卷积神经网络与 CIFAR-10 实战

### 上午(3h)理论学习
- [ ] 卷积的直觉(1.5h)
  - 卷积核、padding、stride、特征图
  - 池化(MaxPool / AvgPool)
  - 为什么 CNN 适合图像(局部感知、参数共享)
  - 观看 3Blue1Brown CNN 视频
- [ ] 经典 CNN 架构(1.5h)
  - LeNet → AlexNet → VGG → ResNet
  - 重点理解 ResNet 的"残差连接"思想
  - 这些在 LLM Transformer 中也有应用

### 下午(3h)动手实践
- [ ] 用 PyTorch 实现 LeNet 训练 CIFAR-10(2h)
  - 使用 `torchvision.datasets.CIFAR10`
  - 数据增强:`transforms.RandomCrop`、`transforms.RandomHorizontalFlip`
  - 目标:测试集准确率 ≥ 70%
  - 提交到 `week03/day3/cifar10_cnn.py`
- [ ] 用预训练 ResNet18 微调 CIFAR-10(1h)
  - 体会"迁移学习"思想(为 Week 4 微调 BERT 铺垫)
  - 提交到 `week03/day3/resnet_finetune.py`

### 晚上(2h)整理与提交
- [ ] 整理 CNN 知识点笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] CIFAR-10 LeNet 训练脚本
- [ ] ResNet 微调脚本

### 推荐资源
- 《动手学深度学习》第 6-7 章
- CS231n 笔记(英文):https://cs231n.github.io/

---

## Day 4 - RNN / LSTM + 文本分类入门

**主题**:序列模型,为 Transformer 打基础

### 上午(3h)理论学习
- [ ] RNN / LSTM / GRU(1.5h)
  - 序列建模的核心问题
  - RNN 为什么会梯度消失
  - LSTM 的"门"机制(直觉理解即可)
  - **重要**:这一节不必深究,Transformer 已经基本取代 RNN
- [ ] 词嵌入(Word Embedding)(1.5h)
  - One-Hot 编码的问题
  - Word2Vec / GloVe 的思想
  - PyTorch `nn.Embedding`
  - **重要**:这是后面 BERT/LLM Embedding 的基础

### 下午(3h)动手实践
- [ ] 用 LSTM 做 IMDB 情感分类(2h)
  - 数据加载、分词、构建词表、padding
  - `nn.Embedding` + `nn.LSTM` + `nn.Linear`
  - 提交到 `week03/day4/imdb_lstm.py`
- [ ] 探索 `nn.Embedding`(1h)
  - 训练一个简单 Embedding,可视化(用 t-SNE)
  - 观察语义相近的词是否在向量空间中接近

### 晚上(2h)整理与提交
- [ ] 整理 RNN / Embedding 笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] IMDB LSTM 训练脚本
- [ ] Embedding 可视化

### 推荐资源
- 《动手学深度学习》第 8-9 章
- The Illustrated Word2vec:https://jalammar.github.io/illustrated-word2vec/

---

## Day 5 - 注意力机制 + Transformer 直觉

**主题**:为 Week 4 大模型铺路

### 上午(3h)理论学习
- [ ] Attention 机制(1.5h)
  - 为什么需要注意力(RNN 长依赖问题)
  - Q / K / V 的直觉理解
  - Self-Attention 的计算过程
- [ ] Transformer 架构总览(1.5h)
  - Encoder / Decoder 结构
  - Multi-Head Attention
  - Position Encoding
  - LayerNorm + 残差连接
  - **强烈推荐**:阅读 The Illustrated Transformer
        https://jalammar.github.io/illustrated-transformer/

### 下午(3h)动手实践
- [ ] 手撸一个最简 Self-Attention(2h)
  - 用 PyTorch 实现 scaled dot-product attention
  - 输入一段简单序列,观察输出
  - 提交到 `week03/day5/self_attention.py`
- [ ] 阅读 PyTorch 官方 `nn.Transformer` 源码注释(1h)
  - 知道用法和参数即可,不必完全看懂

### 晚上(2h)整理与提交
- [ ] 整理 Transformer 概念图(可手绘)
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] Self-Attention 手写实现
- [ ] Transformer 概念笔记

### 推荐资源
- The Illustrated Transformer(强烈推荐):https://jalammar.github.io/illustrated-transformer/
- 李宏毅 Transformer 视频(B 站):https://www.bilibili.com/video/BV1Wv411h7kN
- Karpathy《Let's build GPT》(英文,实战级):https://www.youtube.com/watch?v=kCc8FmEb1nY

---

## Day 6 - 本周综合项目:从零搭建图像分类完整流水线

**主题**:整合本周所学,做一个工程化的图像分类项目

### 上午(3h)项目设计
- [ ] 选定数据集:Fashion-MNIST 或自己收集的小数据集(1h)
- [ ] 设计工程结构(2h)
  ```
  image_classifier/
  ├── README.md
  ├── requirements.txt
  ├── config.yaml          # 超参数配置
  ├── data/                # 数据目录
  ├── src/
  │   ├── dataset.py       # Dataset 实现
  │   ├── model.py         # 模型定义
  │   ├── train.py         # 训练入口
  │   ├── eval.py          # 评估脚本
  │   └── utils.py
  ├── checkpoints/         # 模型保存
  └── logs/                # tensorboard / 日志
  ```

### 下午(3h)动手实践
- [ ] 实现完整流水线(2.5h)
  - 配置文件加载(用 yaml + pydantic)
  - 训练循环 + 验证 + 保存最佳模型
  - 用 `tensorboard` 或 `wandb` 记录训练曲线
- [ ] 写一个 `predict.py`(30min)
  - 加载模型对单张图片做推理

### 晚上(2h)收尾与提交
- [ ] 完善 README(包含训练命令、结果表格、曲线截图)
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 工程化图像分类项目
- [ ] 训练曲线截图与结果表格

### 推荐资源
- TensorBoard 入门:https://pytorch.org/docs/stable/tensorboard.html
- Weights & Biases:https://wandb.ai

---

## Day 7 - 复盘 + 自由学习

### 上午(3h)复盘
- [ ] 填写"本周复盘"
- [ ] 整理本周所有 notebook 和代码
- [ ] 复习 Transformer 概念(为 Week 4 关键)
- [ ] 自评里程碑

### 下午(3h)自由学习
- 选项 A:重看 The Illustrated Transformer
- 选项 B:跟着 Karpathy《Let's build GPT》自己撸 GPT
- 选项 C:复习薄弱点
- 选项 D:休息 ✅

### 晚上(2h)
- [ ] 预读 `week-04-transformer-hf.md`
- [ ] 注册 Hugging Face 账号:https://huggingface.co
- [ ] 安装:`pip install transformers datasets accelerate`

---

## 本周里程碑检查

- [ ] 能解释:Tensor、autograd、nn.Module、训练循环
- [ ] 能用 PyTorch 独立训练一个 CNN
- [ ] 能用 PyTorch 微调一个预训练模型
- [ ] 能解释 Self-Attention 的 Q/K/V 在做什么
- [ ] 有 1 个工程化的 PyTorch 项目放在 GitHub

## 本周资源汇总

### 视频
- 3Blue1Brown 神经网络系列
- 李宏毅深度学习(B 站)
- Andrej Karpathy YouTube 频道(英文,殿堂级)

### 文档
- 《动手学深度学习》PyTorch 版:https://zh.d2l.ai/
- PyTorch 中文教程:https://pytorch.apachecn.org/
- The Illustrated Transformer

### 书籍
- 《深度学习入门:基于 Python 的理论与实现》(鱼书,极易读)
- 《动手学深度学习》(李沐,推荐)

---

## 本周复盘

### 完成度自评
- 整体完成度:____ / 7 天
- 学习时长统计:____ 小时
- GitHub commit 数:____
- MNIST 准确率:____
- CIFAR-10 准确率:____

### 收获最大的三个点
1.
2.
3.

### 最大的卡点
-

### 是否需要 GPU 资源
- [ ] 本地 GPU 充足
- [ ] 需要用 Colab/Kaggle
- [ ] 需要考虑租用云 GPU(autodl 等)

### 下周需要重点关注
-
