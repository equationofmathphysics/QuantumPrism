
# 量化投资系统 (Quant Alpha System)

[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-development-orange)]()

> 基于多模态数据融合的智能量化投资系统，专注于政策驱动因子的挖掘与应用

---

## 📋 项目概述

**Quant Alpha System** 是一个全面的量化投资研究与执行平台，旨在通过理性的数据分析和严格的风险控制，实现长期稳定的投资收益。

### 核心特点

- 🎯 **政策驱动分析**：独特的政策影响量化框架
- 🧠 **多模态融合**：结合数值数据、文本信息和市场情绪
- 📊 **状态识别**：基于HMM的市场环境智能识别
- 🛡️ **风险优先**：严格的风控体系和回撤控制
- 🔄 **持续演进**：模块化设计支持快速迭代

### 预期目标

| 阶段 | 年化收益 | 最大回撤 | 夏普比率 | 策略容量 |
|-----|---------|---------|---------|---------|
| 基础系统 | 10-15% | <20% | >0.6 | 50万-100万 |
| 完善系统 | 15-25% | <15% | >1.0 | 100万-5000万 |
| 成熟系统 | 20-35% | <12% | >1.5 | 5000万+ |

---

## 🏗️ 系统架构

```
quant_alpha_system/
│
├── data_layer/              # 数据采集层
│   ├── policy_collector/    # 政策数据采集
│   ├── market_collector/    # 市场数据采集
│   └── alternative_collector/ # 另类数据采集
│
├── processing_layer/        # 数据处理层
│   ├── data_cleaner/        # 数据清洗
│   ├── text_parser/         # 文本解析
│   └── feature_engineer/    # 特征工程
│
├── analysis_layer/          # 分析计算层
│   ├── regime_detector/     # 市场状态识别
│   ├── multi_factor/        # 多因子模型
│   └── policy_analyzer/     # 政策影响分析
│
├── strategy_layer/          # 策略层
│   ├── asset_allocator/     # 资产配置
│   ├── timing_strategy/     # 择时策略
│   └── portfolio_optimizer/ # 组合优化
│
├── execution_layer/         # 执行层
│   ├── order_manager/       # 订单管理
│   ├── risk_controller/     # 风险控制
│   └── performance_analyzer/ # 绩效分析
│
├── backtest_layer/          # 回测评估层
│   ├── backtest_engine/     # 回测引擎
│   ├── strategy_validator/  # 策略验证
│   └── hyperparameter_optimizer/ # 参数优化
│
├── monitoring_layer/        # 监控预警层
│   ├── real_time_monitor/   # 实时监控
│   ├── anomaly_detector/    # 异常检测
│   └── audit_logger/        # 日志审计
│
├── storage/                 # 数据存储
│   ├── raw_data/           # 原始数据
│   ├── processed_data/     # 处理后数据
│   ├── features/           # 特征数据
│   └── models/             # 模型文件
│
├── config/                  # 配置文件
├── tests/                   # 测试
├── docs/                    # 文档
├── scripts/                 # 脚本
├── utils/                   # 工具函数
└── main.py                  # 主程序入口
```

---

## 🚀 快速开始

### 环境要求

- Python 3.9+
- 8GB+ RAM
- 50GB+ 硬盘空间（用于数据存储）

### 安装步骤

#### 1. 克隆或创建项目

**Windows用户**：
```bash
# 运行项目结构创建脚本
setup_project.bat
cd quant_alpha_system
```

**Linux/Mac用户**：
```bash
# 运行项目结构创建脚本
bash setup_project.sh
cd quant_alpha_system
```



## 📦 核心模块说明

### 1. 数据采集层 (Data Layer)

采集多源数据，包括：
- **政策数据**：20个官方渠道的政策文本
- **市场数据**：股票行情、基本面、资金流向
- **另类数据**：社交媒体情绪、新闻舆情

**示例**：
```python
from data_layer.policy_collector import PolicyDataCollector

collector = PolicyDataCollector()
policies = collector.collect_recent_policies(days=7)
```

### 2. 数据处理层 (Processing Layer)

清洗和转换原始数据：
- 数据清洗和标准化
- 政策文本NLP解析
- 多维度特征工程

**示例**：
```python
from processing_layer.text_parser import PolicyParser

parser = PolicyParser()
structured_policy = parser.parse(policy_text)
# 输出：{'type': '货币政策', 'impact': 0.8, 'industries': ['金融', '地产']}
```

### 3. 分析计算层 (Analysis Layer)

核心智能分析：
- 市场状态识别（HMM模型）
- 多因子模型构建
- 政策影响量化分析

**示例**：
```python
from analysis_layer.regime_detector import MarketRegimeDetector

detector = MarketRegimeDetector()
current_state = detector.predict_state(market_features)
# 输出：'BULL' / 'BEAR' / 'SIDEWAYS' / 'POLICY_DRIVEN'
```

### 4. 策略层 (Strategy Layer)

投资决策生成：
- 资产配置（风险平价、Black-Litterman）
- 择时策略（趋势跟踪、政策驱动）
- 组合优化（均值方差、HRP）

**示例**：
```python
from strategy_layer.portfolio_optimizer import MeanVarianceOptimizer

optimizer = MeanVarianceOptimizer()
weights = optimizer.optimize(expected_returns, cov_matrix)
```

### 5. 回测层 (Backtest Layer)

策略验证：
- 历史回测引擎
- 滚动窗口验证
- 参数优化

**示例**：
```python
from backtest_layer.backtest_engine import BacktestEngine

engine = BacktestEngine(initial_capital=1000000)
results = engine.run(strategy, data, '2020-01-01', '2023-12-31')
print(f"年化收益: {results['annual_return']:.2%}")
print(f"夏普比率: {results['sharpe_ratio']:.2f}")
```

---

## 📊 使用示例

### 完整工作流程

```python
from quant_alpha_system import QuantSystem

# 1. 初始化系统
system = QuantSystem(config_path='config/config.yaml')

# 2. 数据采集
system.collect_data(start_date='2020-01-01', end_date='2023-12-31')

# 3. 特征工程
system.engineer_features()

# 4. 训练模型
system.train_models()

# 5. 回测策略
backtest_results = system.backtest(
    strategy='policy_driven',
    start_date='2022-01-01',
    end_date='2023-12-31'
)

# 6. 查看结果
system.display_results(backtest_results)

# 7. 生成报告
system.generate_report(output_path='reports/backtest_report.html')
```

---

## 🔧 配置说明

### config/config.yaml

```yaml
# 系统全局配置
system:
  mode: "backtest"  # backtest / paper / live
  log_level: "INFO"
  
# 数据配置
data:
  market_data_source: "tushare"
  update_frequency: "daily"
  history_days: 1000
  
# 模型配置
models:
  regime_detector:
    type: "hmm"
    n_states: 4
  
  multi_factor:
    type: "lightgbm"
    features: ["value", "growth", "quality", "momentum", "policy"]
    
# 策略配置
strategy:
  initial_capital: 1000000
  max_position_size: 0.10
  max_industry_exposure: 0.30
  rebalance_frequency: "weekly"
  
# 风控配置
risk:
  max_daily_loss: 0.02
  max_drawdown: 0.15
  stop_loss_pct: 0.08
```

---

## 🧪 测试

### 运行所有测试

```bash
python -m pytest tests/ -v
```

### 测试覆盖率

```bash
python -m pytest --cov=. tests/
```

### 单独测试某个模块

```bash
python -m pytest tests/test_data_collector.py -v
```

---

## 📈 性能监控

系统提供实时监控面板：

```bash
# 启动监控面板
streamlit run frontend/dashboard/app.py
```

监控指标包括：
- 实时收益曲线
- 风险指标（波动率、回撤）
- 因子有效性
- 交易日志

---

## 🤝 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork 本仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 代码规范

- 遵循 PEP 8 风格指南
- 添加必要的文档字符串
- 编写单元测试
- 使用类型提示

---

## 📝 开发路线图

### 第一阶段（1-2个月）：基础架构
- [x] 项目结构搭建
- [ ] 数据采集模块
- [ ] 数据清洗模块
- [ ] 基础回测引擎

### 第二阶段（2-3个月）：核心算法
- [ ] 政策文本解析
- [ ] 多因子模型
- [ ] 市场状态识别
- [ ] 基础策略实现

### 第三阶段（1-2个月）：系统集成
- [ ] 完整工作流程
- [ ] 监控预警系统
- [ ] Web前端界面
- [ ] 性能优化

### 第四阶段（持续）：迭代完善
- [ ] 实盘接入
- [ ] 策略扩展
- [ ] 大模型集成
- [ ] 社区建设

---

## ⚠️ 风险提示

1. **投资有风险**：本系统仅供研究学习使用，不构成投资建议
2. **历史收益不代表未来**：回测结果不能保证实盘表现
3. **数据质量**：请确保数据来源的合法性和准确性
4. **市场变化**：模型可能在市场环境变化时失效
5. **合规要求**：请遵守当地金融监管法规

---

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

---

## 📧 联系方式

- **项目主页**：[GitHub Repository]
- **问题反馈**：[Issues]
- **邮件联系**：quant.alpha.system@example.com

---

## 🙏 致谢

感谢以下开源项目：

- [Pandas](https://pandas.pydata.org/) - 数据处理
- [NumPy](https://numpy.org/) - 数值计算
- [Scikit-learn](https://scikit-learn.org/) - 机器学习
- [LightGBM](https://lightgbm.readthedocs.io/) - 梯度提升树
- [Tushare](https://tushare.pro/) - 金融数据
- [Streamlit](https://streamlit.io/) - Web界面

---

## 📚 相关文档

- [架构设计文档](docs/architecture/system_architecture.md)
- [API文档](docs/api/api_reference.md)
- [使用教程](docs/tutorials/getting_started.md)
- [常见问题](docs/faq.md)

---

**让我们一起用理性和技术，探索量化投资的可能性！** 🚀