# 第 2 周:数学回顾 + 机器学习入门

## 本周目标
- 用最低成本补齐 AI 所需的数学概念(理解即可,不深推)
- 掌握机器学习核心概念:监督/无监督、过拟合、交叉验证、评估指标
- 用 scikit-learn 跑通至少 3 个完整 ML 流程
- 完成 Kaggle Titanic 入门项目并提交

## 前置准备
- [ ] 完成 Week 1 全部内容
- [ ] 安装库:`pip install numpy pandas matplotlib scikit-learn seaborn jupyter`
- [ ] 注册 Kaggle 账号:https://www.kaggle.com

---

## Day 1 - 线性代数(够用就好)

**主题**:向量、矩阵、点积、相似度(RAG 必备)

### 上午(3h)理论学习
- [ ] 观看 3Blue1Brown《线性代数的本质》P1-P5(B 站中文版)(2h)
      https://www.bilibili.com/video/BV1ys411472E
- [ ] 阅读"机器学习中的线性代数"概念笔记(1h)
  - 重点:向量、矩阵乘法、点积、范数、余弦相似度
  - **不要陷入证明,理解几何意义即可**

### 下午(3h)动手实践
- [ ] 用 NumPy 实现下列操作(2h)
  - 向量加法、数乘、点积、L1/L2 范数
  - 矩阵乘法、转置、逆矩阵
  - 余弦相似度函数(为 RAG 铺垫)
  - 提交到 `week02/day1/linear_algebra.ipynb`
- [ ] 实战:用余弦相似度做"文本相似度匹配"(1h)
  - 用简单的词频向量,比较 3 段文本
  - 输出最相似的两段

### 晚上(2h)整理与提交
- [ ] 整理线性代数核心概念笔记(只保留 AI 用得到的)
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 线性代数 notebook
- [ ] 文本相似度小工具

### 推荐资源
- 3Blue1Brown 线代:https://www.bilibili.com/video/BV1ys411472E
- 速读:https://zhuanlan.zhihu.com/p/30191876

---

## Day 2 - 概率统计 + 微积分(够用就好)

**主题**:贝叶斯、分布、梯度下降

### 上午(3h)理论学习
- [ ] 概率统计核心(1.5h)
  - 概率、条件概率、贝叶斯公式
  - 期望、方差、标准差
  - 常见分布:正态分布、伯努利、二项、泊松(知道是啥就行)
  - 大数定律、中心极限定理(听说过即可)
- [ ] 微积分核心(1.5h)
  - 导数的几何意义
  - 偏导数、梯度
  - **重点理解"梯度下降"在做什么**
  - 链式法则(为反向传播铺垫)

### 下午(3h)动手实践
- [ ] 用 NumPy 模拟梯度下降(2h)
  - 拟合一条直线 `y = wx + b`
  - 手动实现梯度计算与参数更新
  - 用 Matplotlib 画出损失下降曲线
  - 提交到 `week02/day2/gradient_descent.ipynb`
- [ ] 用 NumPy 实现简单的朴素贝叶斯分类器(1h)
  - 二分类垃圾邮件分类(用小数据演示)

### 晚上(2h)整理与提交
- [ ] 整理"AI 数学速查卡":梯度、贝叶斯、损失函数
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 梯度下降可视化 notebook
- [ ] 朴素贝叶斯实现

### 推荐资源
- 3Blue1Brown《微积分的本质》:https://www.bilibili.com/video/BV1qW411N7FU
- 《深度学习的数学》(涌井良幸,日本作者,极易读)

---

## Day 3 - 机器学习核心概念 + 第一个 ML 流程

**主题**:监督/无监督、训练流程、scikit-learn API

### 上午(3h)理论学习
- [ ] 观看吴恩达机器学习课程 Week 1(B 站搬运)(2h)
      https://www.bilibili.com/video/BV1Bq421A74G
- [ ] 核心概念笔记(1h)
  - 监督学习 vs 无监督学习 vs 强化学习
  - 训练集 / 验证集 / 测试集
  - 特征工程基础:标准化、归一化、独热编码
  - 过拟合 / 欠拟合 / 正则化
  - **scikit-learn API 范式**:`fit` / `predict` / `transform`

### 下午(3h)动手实践
- [ ] sklearn 第一个流程:鸢尾花分类(1h)
  - 加载数据 → 划分训练/测试集 → 训练逻辑回归 → 评估准确率
  - 完整代码不超过 30 行
  - 提交到 `week02/day3/iris.ipynb`
- [ ] 学习 sklearn Pipeline(1h)
  - `StandardScaler` + `LogisticRegression`
  - 体会"管道"思想(像 Java 的 Builder 模式)
- [ ] 学习交叉验证(1h)
  - `cross_val_score`、`KFold`、`StratifiedKFold`

### 晚上(2h)整理与提交
- [ ] 整理 ML 核心概念笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 鸢尾花完整 ML 流程 notebook
- [ ] Pipeline + 交叉验证示例

### 推荐资源
- 吴恩达 ML(B 站):https://www.bilibili.com/video/BV1Bq421A74G
- sklearn 官方文档:https://scikit-learn.org/stable/

---

## Day 4 - 经典算法巡礼

**主题**:线性/逻辑回归、决策树、随机森林、SVM、KNN

### 上午(3h)理论学习
- [ ] 每个算法 30 分钟,理解直觉,不推公式(2.5h)
  - 线性回归:最小二乘
  - 逻辑回归:sigmoid + 分类
  - 决策树:信息增益
  - 随机森林:Bagging
  - SVM:最大间隔
  - KNN:近朱者赤
- [ ] 评估指标(30min)
  - 分类:Accuracy / Precision / Recall / F1 / ROC-AUC
  - 回归:MSE / RMSE / MAE / R²
  - 混淆矩阵

### 下午(3h)动手实践
- [ ] 在同一数据集(乳腺癌数据集 `load_breast_cancer`)上对比 5 个算法(2h)
  - 用 Pipeline 做特征标准化
  - 用交叉验证评估
  - 画出每个算法的混淆矩阵和 ROC 曲线
  - 提交到 `week02/day4/algorithm_compare.ipynb`
- [ ] 网格搜索调参 `GridSearchCV`(1h)
  - 对随机森林调 `n_estimators` 和 `max_depth`

### 晚上(2h)整理与提交
- [ ] 整理"5 大算法对比表":优缺点、适用场景
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 5 算法对比 notebook
- [ ] 网格搜索调参示例

### 推荐资源
- sklearn 算法地图:https://scikit-learn.org/stable/tutorial/machine_learning_map/
- 《机器学习》(周志华,西瓜书)第 2-6 章

---

## Day 5 - 特征工程 + 无监督学习

**主题**:特征处理、聚类、降维

### 上午(3h)理论学习
- [ ] 特征工程(1.5h)
  - 缺失值处理:删除 / 均值填充 / 中位数 / KNN 填充
  - 类别变量:Label Encoding vs One-Hot Encoding
  - 数值变量:标准化、归一化、对数变换、分箱
  - 特征选择:方差过滤、卡方检验、互信息
- [ ] 无监督学习(1.5h)
  - K-Means 聚类 + 肘部法则
  - 层次聚类
  - PCA 降维(理解:用更少维度保留信息)
  - t-SNE 可视化(知道是用来可视化高维数据的)

### 下午(3h)动手实践
- [ ] 用 K-Means 对鸢尾花做无监督聚类,与真实标签对比(1h)
  - 提交到 `week02/day5/clustering.ipynb`
- [ ] 用 PCA 把 4 维数据降到 2 维并可视化(30min)
- [ ] 用 t-SNE 可视化 MNIST 手写数字(1h)
- [ ] 特征工程综合练习:对房价数据集做完整特征处理(30min)

### 晚上(2h)整理与提交
- [ ] 整理特征工程清单
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 聚类 + PCA + t-SNE notebook
- [ ] 特征工程实战示例

### 推荐资源
- https://scikit-learn.org/stable/modules/clustering.html

---

## Day 6 - 本周综合项目:Kaggle Titanic 完整流程

**主题**:从数据探索到模型提交,走完一个 Kaggle 项目

### 上午(3h)数据探索 EDA
- [ ] 下载 Titanic 数据集 https://www.kaggle.com/c/titanic
- [ ] 用 pandas + seaborn 做探索性分析(2h)
  - 缺失值统计
  - 各特征与存活率的关系(性别、年龄、船舱、票价、家庭成员)
  - 相关性热力图
- [ ] 整理特征工程方案(1h)

### 下午(3h)建模与提交
- [ ] 特征工程(1.5h)
  - 缺失值处理:Age 用中位数,Embarked 用众数
  - 提取 Title 特征(Mr/Mrs/Miss 等)
  - 创建 FamilySize 特征
  - One-Hot 编码 Sex、Embarked、Pclass
- [ ] 训练多个模型并对比(1h)
  - 逻辑回归、随机森林、梯度提升(GradientBoosting / XGBoost)
  - 用 5 折交叉验证选最优
- [ ] 在 Kaggle 提交结果(30min)
  - 记录 Public Leaderboard 分数
  - 目标:0.78+

### 晚上(2h)总结与博客
- [ ] 写一篇技术博客《Java 工程师入门 ML:从 Titanic 项目开始》(可选,推荐)
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] Kaggle 提交结果(截图)
- [ ] 完整 Titanic 项目 notebook
- [ ] (可选)技术博客

### 推荐资源
- Kaggle Titanic Tutorial:https://www.kaggle.com/c/titanic/overview/tutorials
- 优质 Kernel 参考:https://www.kaggle.com/c/titanic/notebooks

---

## Day 7 - 复盘 + 自由学习

### 上午(3h)复盘
- [ ] 填写本文件末尾"本周复盘"
- [ ] 整理本周所有 notebook,补充注释
- [ ] 自评里程碑

### 下午(3h)自由学习
- 选项 A:做另一个 Kaggle 入门题(房价预测)
- 选项 B:看吴恩达课程下一周内容(神经网络入门)
- 选项 C:复习薄弱点
- 选项 D:休息 ✅

### 晚上(2h)
- [ ] 预读 `week-03-pytorch.md`
- [ ] 安装 PyTorch:`pip install torch torchvision torchaudio`
- [ ] 验证 GPU 可用(若有):`python -c "import torch; print(torch.cuda.is_available())"`

---

## 本周里程碑检查

- [ ] 能解释:监督学习、过拟合、交叉验证、Precision/Recall
- [ ] 能用 sklearn Pipeline 完成 ML 全流程
- [ ] 能在新数据集上独立选模型、调参、评估
- [ ] 完成 Kaggle Titanic 提交,分数 ≥ 0.78
- [ ] 理解什么是梯度下降(直觉层面)

## 本周资源汇总

### 视频
- 3Blue1Brown 线代+微积分:B 站搜"3Blue1Brown"
- 吴恩达 Machine Learning Specialization(B 站搬运)

### 文档
- sklearn 中文文档:https://www.sklearndoc.cn/
- Kaggle Learn:https://www.kaggle.com/learn

### 书籍
- 《机器学习》(周志华,西瓜书)
- 《统计学习方法》(李航,可选,偏理论)
- 《Hands-On Machine Learning》(Aurélien Géron,实战推荐)

---

## 本周复盘

### 完成度自评
- 整体完成度:____ / 7 天
- 学习时长统计:____ 小时
- GitHub commit 数:____
- Kaggle 分数:____

### 收获最大的三个点
1.
2.
3.

### 最大的卡点
-

### 数学焦虑评分(1-10)
-
> 提醒:走应用方向不需要会推公式,理解概念即可

### 下周需要重点关注
-

### 心态记录
-
