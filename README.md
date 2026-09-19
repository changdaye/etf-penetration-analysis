# ETF 组合穿透分析套件与数据示例 (ETF Penetration Analysis)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

投资组合 ETF 底层持仓一键穿透分析工具与样本数据集。帮助投资者透过 ETF 表面代码，穿透至最底层的个股标的，计算真实资产敞口、行业集中度与重叠持仓。

---

## 📊 包含的示例数据与报表

本仓库随附完整的实战测试数据与生成报表：

- `汇总持仓.xlsx`：包含同花顺格式导出的多只 ETF 混合持仓样本（脱敏处理）
- `ETF 穿透分析示例_*.xlsx`：标准穿透报表（含穿透后个股权重、金额与行业分类）
- `ETF 穿透分析_前 500 大_*.xlsx`：全市场大盘宽基组合穿透后前 500 大底层持仓全景透视图

---

## 🚀 核心功能

1. **ETF 底层穿透解构**：支持 51/15/56 开头的沪深公募 ETF，自动根据基金最新公布持仓计算权重分解。
2. **底层个股穿透求和**：自动合并不同 ETF（如沪深300 ETF + 创业板 ETF + 芯片 ETF）中重叠的底层股票持仓，计算实际真实占比。
3. **行业多级穿透**：根据底层股票名称智能归类所属行业（涵盖 1800+ 只 A 股/港股/美股标的）。
4. **LLM 研报解读集成**：集成 DeepSeek / OpenAI 大模型，自动针对穿透后的前十大持仓与行业暴露生成宏观风险与风格点评。

---

## 🛠️ 快速上手

```bash
# 1. 克隆仓库
git clone https://github.com/changdaye/etf-penetration-analysis.git
cd etf-penetration-analysis

# 2. 安装依赖
cd backend
pip install -r requirements.txt

# 3. 启动本地 Web 分析服务
python app.py
```

服务启动后，浏览器访问 `http://localhost:5001` 上传持仓 Excel 文件即可实时生成穿透报表。

---

## 📑 辅助指南文档

- [LLM_INTEGRATION_GUIDE.md](LLM_INTEGRATION_GUIDE.md)：大语言模型分析模块接入指引
- [DEEPSEEK_SETUP.md](DEEPSEEK_SETUP.md)：DeepSeek API / 本地模型配置说明
- [README_CN_EN.md](README_CN_EN.md)：双语完整项目规范

