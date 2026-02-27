# ETF 穿透分析工具

基于 Web 的 ETF 持仓穿透分析工具，帮你查看 ETF 底层买了什么股票。

## 功能特点

- 📁 上传 Excel 持仓文件
- 🔍 自动识别 ETF 并获取持仓
- 📊 展示穿透后的底层股票
- 🏭 行业分类统计
- 📈 集中度分析
- 📥 导出 Excel 结果

## 项目结构

```
etf-penetration-website/
├── backend/
│   ├── app.py              # Flask 后端
│   └── requirements.txt    # Python 依赖
├── frontend/
├── static/
│   ├── css/
│   │   └── style.css      # 样式
│   └── js/
│       └── app.js         # 前端逻辑
├── templates/
│   └── index.html         # 主页面
└── data/
    └── industry_map.json  # 股票 - 行业映射
```

## 快速开始

### 1. 安装依赖

```bash
cd backend
pip3 install -r requirements.txt
```

### 2. 启动服务

```bash
python3 app.py
```

服务启动后访问：http://localhost:5000

### 3. 上传持仓文件

Excel 文件需要包含以下列：
- `代码` - 股票/ETF 代码
- `名称` - 股票/ETF 名称  
- `持有金额` - 持仓金额

## 行业映射维护

股票 - 行业映射保存在 `data/industry_map.json` 中。

格式：
```json
{
  "00700": "互联网 - 社交平台",
  "600519": "食品饮料 - 白酒"
}
```

可以通过 API 动态添加：
```bash
curl -X POST http://localhost:5000/api/industry-map \
  -H "Content-Type: application/json" \
  -d '{"code": "00700", "industry": "互联网 - 社交平台"}'
```

## API 接口

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/upload` | POST | 上传持仓文件 |
| `/api/analyze` | POST | 分析 ETF 持仓 |
| `/api/industry-map` | GET | 获取行业映射 |
| `/api/industry-map` | POST | 更新行业映射 |
| `/api/export` | POST | 导出结果 |

## 技术栈

- **后端**: Flask + akshare
- **前端**: 原生 HTML/CSS/JS + Chart.js
- **数据**: akshare (东方财富)

## 注意事项

1. 首次运行需要安装 akshare 和相关依赖
2. ETF 持仓数据来自东方财富，可能存在延迟
3. 行业分类基于本地映射，可手动维护
