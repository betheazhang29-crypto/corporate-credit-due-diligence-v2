# 银行对公授信尽职调查专家

专业的银行授信尽调主协调器，协调4个子技能完成从数据采集、多维度分析、报告生成到质量优化的全流程自动化，生成高质量尽调报告（评分9.0-9.5分）。

## 功能特点

- **4个阶段流程**：数据采集（10-30分钟）→ 数据分析（30-60分钟）→ 报告生成（30-60分钟）→ 报告优化（30-60分钟）
- **4个子技能协调**：自动调用4个专业子技能
- **质量保证**：确保最终报告达到9.0-9.5分（优秀）
- **完整输出**：15-20页Word报告 + 12张专业图表 + 深度分析文字

## 使用方法

```
对【某某公司】进行授信尽调
```

Manus 会自动：
1. 调用 corporate-intelligence-collector 采集数据
2. 调用 corporate-data-analyst 分析数据
3. 调用 corporate-report-architect 生成报告
4. 调用 corporate-report-optimizer 优化报告
5. 交付最终高质量报告

## 输出

- `尽调报告_{company_name}_{date}.docx`：完整的Word尽调报告（15-20页，1.7MB+，评分9.0-9.5分）
- `intelligence_data.json`：企业情报数据
- `analysis_results.json`：分析结果
- `charts/`：12张专业图表

## 依赖技能

本技能需要安装以下4个子技能：
1. corporate-intelligence-collector（企业情报采集专家）
2. corporate-data-analyst（企业数据分析专家）
3. corporate-report-architect（企业报告构建专家）
4. corporate-report-optimizer（企业报告优化专家）

## 安装

在 Manus 技能广场搜索 "corporate-credit-due-diligence" 并安装。

**注意**：安装后请确保4个子技能也已安装。

## 版本

v2.0.0

## 许可证

Copyright © 2026 Manus AI. All rights reserved.
