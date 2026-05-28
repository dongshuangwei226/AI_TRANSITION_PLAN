# 第 1 周:Python 速成

## 本周目标
- 从"看得懂 Python"到"能独立写小项目"
- 建立 Java↔Python 的概念映射
- 掌握 NumPy / Pandas / Matplotlib 基础
- 配置好 Python 开发环境
- 在 GitHub 建立学习仓库,保持每日 commit

## 前置准备
- [ ] 安装 Python 3.11
- [ ] 安装 Miniconda
- [ ] 安装 VSCode + Python 插件 + Jupyter 插件
- [ ] 注册 GitHub 账号(若没有)
- [ ] 阅读 `README.md` 的"环境准备清单"

---

## Day 1 - Python 语法与 Java 对比

**主题**:从 Java 视角快速掌握 Python 基础语法

### 上午(3h)理论学习
- [ ] 观看莫烦 Python 基础教程 P1-P10(1.5h)
      https://www.bilibili.com/video/BV1Vx411G7ec
- [ ] 阅读 Python 官方教程第 3-5 章(1.5h)
      https://docs.python.org/zh-cn/3/tutorial/

### 下午(3h)动手实践
- [ ] 配置开发环境(30min)
  - 安装 Python 3.11、Miniconda、VSCode
  - 创建 conda 环境:`conda create -n ai python=3.11`
  - 激活并验证:`conda activate ai && python --version`
- [ ] 创建 GitHub 仓库 `ai-learning`(30min)
  - 添加 `.gitignore`(Python 模板)
  - 添加 README,写明学习计划
  - clone 到本地
- [ ] 编写第一段 Python 代码:Java 与 Python 语法对比(2h)
  - 变量与类型、条件、循环、函数、异常
  - 同一个功能用 Java 和 Python 各写一遍,放在 `week01/day1/compare.md`

### 晚上(2h)整理与提交
- [ ] 整理"Java↔Python 速查表"笔记(1h)
- [ ] 推送代码到 GitHub(30min)
- [ ] 填写每日总结到 `daily-logs/`(30min)

### 今日交付物
- [ ] GitHub 仓库已建立,有 README 和第一个 commit
- [ ] `week01/day1/compare.md`:Java↔Python 语法对照笔记

### 推荐资源
- 视频:【B 站】莫烦 Python 基础教程
- 文档:https://docs.python.org/zh-cn/3/tutorial/
- 速查:https://learnxinyminutes.com/docs/zh-cn/python-cn/

---

## Day 2 - 数据结构与函数式编程

**主题**:列表、字典、集合、列表推导式、Lambda、map/filter/reduce

### 上午(3h)理论学习
- [ ] 学习 Python 内置数据结构(1.5h)
  - list / tuple / dict / set / frozenset
  - 切片(slicing)、负索引
  - 与 Java Collection 的对照
- [ ] 学习列表推导式与生成器表达式(1h)
  - `[x*2 for x in nums if x > 0]`
  - 与 Java Stream API 的对照
- [ ] 学习 `lambda`、`map`、`filter`、`reduce`、`zip`、`enumerate`(30min)

### 下午(3h)动手实践
- [ ] 用 Python 重写 Java Stream API 常见操作(1.5h)
  - filter + map + collect
  - groupBy
  - reduce 求和、求最大
- [ ] 完成 10 道 LeetCode 简单题(1.5h),要求:
  - 至少 5 道用列表推导式或函数式风格
  - 提交到 `week01/day2/leetcode/`
  - 推荐题目:Two Sum、Reverse Integer、Valid Parentheses、Palindrome Number、Roman to Integer

### 晚上(2h)整理与提交
- [ ] 整理"Python 数据结构速查"笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 10 道 LeetCode 题代码
- [ ] Stream API ↔ Python 函数式对照笔记

### 推荐资源
- 《Fluent Python》第 2-5 章(可选,有英文版 PDF)
- https://realpython.com/list-comprehension-python/

---

## Day 3 - 面向对象、模块、异常、文件 IO

**主题**:Python 的 OOP 与 Java OOP 的差异

### 上午(3h)理论学习
- [ ] Python 面向对象(1.5h)
  - class、`__init__`、`self`、继承、多重继承、MRO
  - 类方法 `@classmethod`、静态方法 `@staticmethod`、属性 `@property`
  - 魔术方法 `__str__`、`__repr__`、`__eq__`、`__hash__`
  - 与 Java OOP 的差异:鸭子类型、无 `private` 关键字、约定 `_` 和 `__`
- [ ] 模块与包(1h)
  - `import`、`from ... import ...`、`__init__.py`、`__name__ == "__main__"`
  - 与 Java package 的对照
- [ ] 异常处理与文件 IO(30min)
  - `try/except/else/finally`、`raise`
  - `with open(...) as f:` 上下文管理器(对应 Java try-with-resources)

### 下午(3h)动手实践
- [ ] 实现一个简单的"日志解析器"项目(2.5h)
  - 读取一个 log 文件,统计 ERROR/WARN/INFO 数量
  - 抽出最高频的 10 个错误信息
  - 输出到 CSV 文件
  - 用 OOP 风格组织代码:`LogParser` 类
  - 提交到 `week01/day3/log_parser/`
- [ ] 用 pytest 编写单元测试(30min)

### 晚上(2h)整理与提交
- [ ] 整理 OOP 对比笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 完整的日志解析器项目(含测试)
- [ ] OOP Java↔Python 对照笔记

### 推荐资源
- https://realpython.com/python3-object-oriented-programming/
- pytest 入门:https://docs.pytest.org/en/stable/getting-started.html

---

## Day 4 - 装饰器、生成器、类型注解、Pydantic

**主题**:Python 高级特性 + AI 开发常用工具

### 上午(3h)理论学习
- [ ] 装饰器(1.5h)
  - 函数装饰器、带参数的装饰器、类装饰器
  - 常用装饰器:`@functools.lru_cache`、`@functools.wraps`、`@dataclass`
  - **重要**:装饰器 ↔ Spring AOP
- [ ] 生成器与迭代器(1h)
  - `yield`、生成器表达式
  - 迭代器协议
- [ ] 类型注解与 Pydantic(30min)
  - `typing` 模块:`List`、`Dict`、`Optional`、`Union`、`Callable`
  - `pydantic.BaseModel`:数据校验(对标 Java Bean Validation)

### 下午(3h)动手实践
- [ ] 编写 3 个实用装饰器(1.5h)
  - `@timer`:统计函数执行时间
  - `@retry(times=3)`:失败重试
  - `@log_call`:打印参数和返回值
  - 提交到 `week01/day4/decorators/`
- [ ] 用 Pydantic 定义数据模型(1.5h)
  - 定义 `User`、`Order`、`Product` 模型
  - 演示字段校验、默认值、嵌套模型
  - 演示 JSON 序列化/反序列化(对照 Java Jackson)

### 晚上(2h)整理与提交
- [ ] 整理装饰器与 Pydantic 笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] 3 个装饰器实现
- [ ] Pydantic 数据模型示例

### 推荐资源
- https://realpython.com/primer-on-python-decorators/
- https://docs.pydantic.dev/latest/

---

## Day 5 - NumPy + Pandas + Matplotlib

**主题**:数据科学三件套(为 ML 阶段铺路)

### 上午(3h)理论学习
- [ ] NumPy 基础(1.5h)
  - `ndarray` 创建、形状、索引、切片
  - 广播机制(broadcasting)
  - 常用函数:`sum`、`mean`、`max`、`reshape`、`concatenate`
  - 向量化运算思想(为什么比 for 循环快)
- [ ] Pandas 基础(1h)
  - `Series` 与 `DataFrame`
  - 读写 CSV/Excel:`read_csv`、`to_csv`
  - 选择、过滤、分组聚合(对照 SQL)
- [ ] Matplotlib 基础(30min)
  - `plt.plot`、`plt.scatter`、`plt.bar`、`plt.hist`
  - subplot 子图

### 下午(3h)动手实践
- [ ] NumPy 练习(1h)
  - 创建随机矩阵,做矩阵乘法
  - 用 NumPy 计算余弦相似度
  - 提交到 `week01/day5/numpy_basics.ipynb`
- [ ] Pandas 实战:分析一个真实数据集(1.5h)
  - 下载 Titanic 数据集(Kaggle / seaborn 内置)
  - 计算:存活率、按性别/船舱等级的存活率
  - 处理缺失值
  - 提交到 `week01/day5/titanic_eda.ipynb`
- [ ] Matplotlib 可视化(30min)
  - 画存活率柱状图、年龄分布直方图

### 晚上(2h)整理与提交
- [ ] 整理 NumPy / Pandas 速查笔记
- [ ] commit & push
- [ ] 填写每日总结

### 今日交付物
- [ ] NumPy / Pandas / Matplotlib 三个 notebook
- [ ] Titanic 数据初步分析报告

### 推荐资源
- NumPy 中文文档:https://www.numpy.org.cn/
- Pandas 中文教程:https://www.pypandas.cn/
- 《利用 Python 进行数据分析》第 2 版(Wes McKinney)

---

## Day 6 - 本周综合项目:命令行 AI 助手雏形

**主题**:整合本周所学,做一个调用 LLM API 的 CLI 工具

### 上午(3h)项目设计
- [ ] 设计 CLI 工具功能(1h)
  - 接收用户输入,调用 DeepSeek/通义千问 API,返回回复
  - 支持流式输出
  - 支持多轮对话(保存上下文)
  - 支持配置文件(API key、模型名)
- [ ] 设计项目结构(1h)
  ```
  cli_chat/
  ├── pyproject.toml (或 requirements.txt)
  ├── README.md
  ├── config.yaml
  ├── src/
  │   ├── __init__.py
  │   ├── main.py
  │   ├── llm_client.py
  │   ├── chat_session.py
  │   └── utils.py
  └── tests/
  ```
- [ ] 申请 DeepSeek 或通义千问 API key(1h)

### 下午(3h)动手实践
- [ ] 实现 `llm_client.py`(1h)
  - 用 Pydantic 定义请求/响应模型
  - 封装 HTTP 请求(用 `httpx` 或 `requests`)
- [ ] 实现 `chat_session.py`(1h)
  - 用 list 保存对话历史
  - 限制上下文长度(token 估算)
- [ ] 实现 `main.py` 命令行入口(1h)
  - 用 `argparse` 或 `click`
  - 流式打印输出

### 晚上(2h)收尾与提交
- [ ] 写 README,含使用示例
- [ ] commit & push
- [ ] 录制一个使用 GIF(可选)
- [ ] 填写每日总结

### 今日交付物
- [ ] 完整可运行的 CLI 聊天工具
- [ ] README 含使用截图

### 推荐资源
- DeepSeek API 文档:https://api-docs.deepseek.com/zh-cn/
- 通义千问 API 文档:https://help.aliyun.com/zh/dashscope/

---

## Day 7 - 复盘 + 自由学习

### 上午(3h)复盘
- [ ] 整理本周笔记成一份完整的"Python 速查手册"
- [ ] 填写本文件末尾的"本周复盘"
- [ ] 检查 GitHub 仓库,补全 README 与目录结构
- [ ] 对照"本周里程碑检查",自评完成度

### 下午(3h)自由安排
- 选项 A:补做未完成的练习
- 选项 B:阅读《Effective Python》摘选
- 选项 C:看 1-2 个 AI 应用案例视频,建立兴趣
- 选项 D:休息 ✅

### 晚上(2h)
- [ ] 预读 `week-02-math-ml-intro.md`
- [ ] 提前下载 ML 课程视频(吴恩达 Machine Learning Specialization)

---

## 本周里程碑检查

- [ ] 能用 Python 写出与 Java 同等清晰的 OOP 代码
- [ ] 能熟练使用列表推导式、装饰器、Pydantic
- [ ] 能用 Pandas 完成 CSV 加载、过滤、聚合、绘图
- [ ] 能独立调用 LLM API 并实现多轮对话
- [ ] GitHub 仓库 ai-learning 至少有 20+ commit

## 本周资源汇总

### 视频
- 莫烦 Python:https://www.bilibili.com/video/BV1Vx411G7ec
- 黑马 Python 入门(可选):https://www.bilibili.com/video/BV1qW4y1a7fU

### 文档
- Python 官方教程(中文):https://docs.python.org/zh-cn/3/tutorial/
- Real Python:https://realpython.com/
- Pydantic 文档:https://docs.pydantic.dev/

### 书籍
- 《Python Crash Course》(英文)
- 《流畅的 Python》(高级,可选)
- 《利用 Python 进行数据分析》(Pandas 必读)

---

## 本周复盘

> 周日填写

### 完成度自评
- 整体完成度:____ / 7 天
- 学习时长统计:____ 小时
- GitHub commit 数:____

### 收获最大的三个点
1.
2.
3.

### 最大的卡点
-

### 与 Java 经验的关键映射
-

### 下周需要重点关注
-

### 心态记录
-
