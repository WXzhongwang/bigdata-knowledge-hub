# 大数据知识巩固台（bigdata-knowledge-hub）

面向大数据开发工程师的知识学习巩固静态站点，托管在 GitHub Pages。

**在线访问**：<https://wxzhongwang.github.io/bigdata-knowledge-hub/>

## 功能

- **今天要处理**：自动汇总逾期 / 今日到期 / 近 3 天到期的知识卡片，一键完成复习
- **艾宾浩斯复习节奏**：完成复习后按 1 / 3 / 7 / 15 / 30 天间隔自动安排下次复习，掌握度随复习次数提升（≥1 次学习中、≥3 次已掌握）
- **知识卡片库**：覆盖 Hadoop / Spark / Flink / Kafka / Hive / HBase / ClickHouse / Doris / 数据湖 / 数仓调度等技术栈，支持按技术栈、知识类型（原理 / 使用方法 / 面试题 / 架构方案 / 核心代码）筛选与全文搜索
- **面试题专项**：汇总所有带「面试题」标签的卡片，展开即看参考答案
- **学习统计**：KPI 卡片 + 掌握度环形图 + 技术栈 / 知识类型分布图（纯内联 SVG，零外部依赖）
- 单文件 `index.html`，无任何外部 CDN / 字体 / JS 库依赖，PC 与移动端自适应

## 仓库结构

```
├── index.html                     # 站点页面（单文件，零依赖）
├── data.json                      # 知识卡片数据（唯一数据源）
└── .github/workflows/deploy.yml   # push main 自动部署 GitHub Pages
```

## 数据说明

- `data.json` 是知识库的唯一数据源，数组元素字段：

```json
{
  "id": "唯一ID",
  "name": "知识点名称",
  "stack": "技术栈",
  "types": ["原理", "面试题"],
  "level": "待学习",
  "content": "Markdown 内容",
  "reviewCount": 0,
  "lastReview": "",
  "nextReview": "2026-09-01"
}
```

- 浏览器端的**复习进度**、**本地新增卡片**保存在访问者浏览器的 localStorage 中，不回写仓库
- 页面右上角支持「导出备份 / 导入恢复」JSON 快照

## 更新知识库

向 `data.json` 追加新卡片并 push 到 `main` 分支，GitHub Actions 会自动重新部署，约 1 分钟后生效。本仓库配合 WorkBuddy 每日自动化任务，每天自动补充新的大数据知识卡片。

## 技术栈清单（持续扩充）

Hadoop · Spark · Flink · Kafka · Hive · HBase · ClickHouse · Doris · Iceberg / Hudi / Delta Lake · DolphinScheduler / Airflow · DataX / SeaTunnel · Pulsar / RocketMQ · Elasticsearch · 数仓建模与分层
