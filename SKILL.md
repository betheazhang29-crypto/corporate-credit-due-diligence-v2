---
name: corporate-credit-due-diligence
description: 银行对公授信尽职调查主协调器。协调4个子技能（企业情报采集、企业数据分析、企业报告构建、企业报告优化）完成完整的授信尽调流程，生成包含10+专业图表和深度分析文字的高质量尽调报告（15-20页）。支持自动依赖检查、流程协调、进度跟踪、质量优化。
version: 1.0.0
author: Manus AI
created: 2026-02-14
updated: 2026-02-14
dependencies:
  - corporate-intelligence-collector
  - corporate-data-analyst
  - corporate-report-architect
  - corporate-report-optimizer
tools: File
model: sonnet
category: business
color: purple
displayName: 银行授信尽调专家
---

# 银行对公授信尽职调查

## 技能概述

银行对公授信尽职调查主协调器，协调4个专业子技能完成完整的授信尽调流程。从数据采集、深度分析、报告生成到质量优化，实现全流程自动化，确保最终报告达到银行审批标准（9分以上）。

### 核心价值

传统银行授信尽调需要2-5天，涉及多个部门协作，且质量依赖个人经验。本技能将这一过程缩短到1-2小时，并确保流程标准化、分析专业化、报告规范化。

### 主要功能

1. **依赖检查**：自动检查4个子技能是否已安装
2. **流程协调**：按顺序协调4个子技能执行
3. **进度跟踪**：实时显示执行进度
4. **质量保证**：自动优化报告质量，确保达到9分以上
5. **错误处理**：自动处理错误并提示用户
6. **结果交付**：生成高质量尽调报告（10+图表，深度分析）和所有中间数据

### 子技能依赖

本技能依赖以下4个子技能：

1. **corporate-intelligence-collector**（企业情报采集专家）
   - 从10+公开渠道采集企业全方位信息
   - 输出：`intelligence_data.json`、截图、文档

2. **corporate-data-analyst**（企业数据分析专家）
   - 7大维度深度分析，30+财务比率
   - 输出：`analysis_results.json`、图表

3. **corporate-report-architect**（企业报告构建专家）
   - 生成包含10+专业图表和深度分析文字的Word尽调报告
   - 输出：`尽调报告.docx`（15-20页，1.7MB+）

4. **corporate-report-optimizer**（企业报告优化专家）
   - 自动检查报告质量并直接改进
   - 补充缺失数据、深化分析、增加图表
   - 输出：`尽调报告_改进版.docx`（评分9分以上）

### 适用场景

- 银行对公授信尽职调查
- 企业信用评估
- 投资尽职调查

---

## 核心工作流程

### 完整流程（4个阶段）

```
阶段1：数据采集（10-30分钟）
  ↓
  调用 corporate-intelligence-collector
  ├── 企查查/天眼查（企业基本信息）
  ├── 国家企业信用信息公示系统（工商信息）
  ├── 上市公司年报（财务数据）
  ├── 行业研究报告（行业数据）
  ├── 裁判文书网/执行信息公开网（风险数据）
  └── 企业官网/新闻搜索（市场情报）
  ↓
  输出：intelligence_data.json + screenshots/ + documents/

阶段2：数据分析（30-60分钟）
  ↓
  调用 corporate-data-analyst
  ├── 企业基本情况分析
  ├── 行业分析
  ├── 经营情况分析
  ├── 财务分析（30+比率）
  ├── 融资情况分析
  ├── 担保能力分析
  └── 风险分析
  ↓
  输出：analysis_results.json + charts/

阶段3：报告生成（30-60分钟）
  ↓
  调用 corporate-report-architect
  ├── 生成10-15张专业图表
  ├── 编写8个核心章节（深度分析文字）
  ├── 嵌入图表到Word文档
  ├── 格式化表格
  └── 生成目录
  ↓
  输出：尽调报告.docx（15-20页，1.7MB+）

阶段4：报告优化（30-60分钟）
  ↓
  调用 corporate-report-optimizer
  ├── 5大维度质量检查
  ├── 识别改进优先级
  ├── 自动补充缺失数据
  ├── 深化分析文字
  ├── 增加缺失图表
  └── 重新生成Word报告
  ↓
  输出：尽调报告_改进版.docx（评分9.0-9.5分）

总耗时：55-120分钟
```

---

## 依赖检查

在执行前，自动检查3个子技能是否已安装：

```python
def check_dependencies():
    """检查依赖的子技能是否已安装"""
    required_skills = [
        "corporate-intelligence-collector",
        "corporate-data-analyst",
        "corporate-report-architect"
    ]
    
    missing_skills = []
    for skill in required_skills:
        if not skill_installed(skill):
            missing_skills.append(skill)
    
    if missing_skills:
        print("❌ 缺少以下子技能，请先安装：")
        for skill in missing_skills:
            print(f"  - {skill}")
        print("\n安装方法：在Manus技能界面点击 '+ 添加'，输入技能名称")
        return False
    
    print("✓ 所有依赖的子技能已安装")
    return True
```

---

## 进度跟踪

实时显示执行进度：

```
========================================
银行对公授信尽职调查
企业名称：珠海金智维人工智能股份有限公司
========================================

[1/3] 正在采集企业数据... (预计10-30分钟)
  ├── [企查查] 正在采集企业基本信息...
  │   └── ✓ 采集完成
  ├── [国家企业信用信息公示系统] 正在采集工商信息...
  │   └── ✓ 采集完成
  ├── [上交所] 正在下载年报...
  │   └── ✓ 下载完成
  ├── [裁判文书网] 正在采集涉诉信息...
  │   └── ✓ 采集完成
  └── [执行信息公开网] 正在采集被执行人信息...
      └── ✓ 采集完成
  
  ✓ 数据采集完成（耗时：25分钟）
  
[2/3] 正在进行数据分析... (预计30-60分钟)
  ├── [企业基本情况分析] 正在分析...
  │   └── ✓ 分析完成
  ├── [行业分析] 正在分析...
  │   └── ✓ 分析完成
  ├── [经营情况分析] 正在分析...
  │   └── ✓ 分析完成
  ├── [财务分析] 正在计算30+财务比率...
  │   └── ✓ 分析完成
  ├── [融资情况分析] 正在分析...
  │   └── ✓ 分析完成
  ├── [担保能力分析] 正在分析...
  │   └── ✓ 分析完成
  └── [风险分析] 正在进行风险评估...
      └── ✓ 分析完成
  
  ✓ 数据分析完成（耗时：45分钟）
  
[3/3] 正在生成报告... (预计15-30分钟)
  ├── [封面] 正在生成...
  │   └── ✓ 生成完成
  ├── [目录] 正在生成...
  │   └── ✓ 生成完成
  ├── [第一章：企业基本情况] 正在生成...
  │   └── ✓ 生成完成
  ├── [第二章：行业分析] 正在生成...
  │   └── ✓ 生成完成
  ├── [第三章：经营情况] 正在生成...
  │   └── ✓ 生成完成
  ├── [第四章：财务分析] 正在生成...
  │   └── ✓ 生成完成
  ├── [第五章：融资情况] 正在生成...
  │   └── ✓ 生成完成
  ├── [第六章：担保情况] 正在生成...
  │   └── ✓ 生成完成
  ├── [第七章：风险分析] 正在生成...
  │   └── ✓ 生成完成
  └── [第八章：授信建议] 正在生成...
      └── ✓ 生成完成
  
  ✓ 报告生成完成（耗时：20分钟）

========================================
✅ 尽调完成！
总耗时：90分钟
========================================

输出文件：
  - 尽调报告：/home/ubuntu/due_diligence/珠海金智维/尽调报告_20260214.docx
  - 数据文件：/home/ubuntu/due_diligence/珠海金智维/intelligence_data.json
  - 分析结果：/home/ubuntu/due_diligence/珠海金智维/analysis_results.json
  - 图表目录：/home/ubuntu/due_diligence/珠海金智维/charts/
  - 截图证据：/home/ubuntu/due_diligence/珠海金智维/screenshots/
  - 文档证据：/home/ubuntu/due_diligence/珠海金智维/documents/
```

---

## 错误处理

如果某个阶段失败，自动提示用户：

```
❌ 阶段1失败：数据采集失败

原因：无法访问企查查网站

建议：
1. 检查网络连接
2. 重试数据采集
3. 手动提供企业信息

是否继续？
```

---

## 使用方法

### 方法1：在 Manus 中直接调用（推荐）

```
对【珠海金智维人工智能股份有限公司】进行授信尽调
统一社会信用代码：91440400MA4UKDGM8E
```

Manus 会自动：
1. 检查依赖的子技能是否已安装
2. 按顺序调用3个子技能
3. 实时显示进度
4. 生成完整的尽调报告

### 方法2：指定采集模式

```
对【某某公司】进行授信尽调，使用深度调查模式
```

### 方法3：提供额外信息

```
对【某某公司】进行授信尽调
财务报表文件：/path/to/financial_statements.xlsx
```

---

## 输出标准

### 完整输出目录

```
/home/ubuntu/due_diligence/珠海金智维人工智能股份有限公司/
├── 尽调报告_20260214.docx          # 主报告（40-50页）
├── intelligence_data.json          # 采集的原始数据
├── analysis_results.json           # 分析结果
├── collection_report.md            # 数据采集报告
├── screenshots/                    # 截图证据
│   ├── qichacha_basic.png
│   ├── gsxt_license.png
│   ├── wenshu_case_1234.png
│   └── ...
├── documents/                      # 文档证据
│   ├── annual_report_2023.pdf
│   ├── industry_report_ai_2023.pdf
│   └── ...
├── charts/                         # 分析图表
│   ├── revenue_trend.png
│   ├── financial_ratios.png
│   ├── risk_radar.png
│   └── ...
└── logs/
    ├── collection_log.txt          # 采集日志
    ├── analysis_log.txt            # 分析日志
    └── report_log.txt              # 报告生成日志
```

---

## 子技能独立使用

虽然本技能协调3个子技能完成完整流程，但用户也可以独立使用子技能：

### 独立使用技能1：只采集数据

```
使用 corporate-intelligence-collector 技能采集【某某公司】的企业信息
```

输出：
- `intelligence_data.json`
- `screenshots/`
- `documents/`

### 独立使用技能2：只分析数据

```
使用 corporate-data-analyst 技能分析【某某公司】的财务状况
```

输出：
- `analysis_results.json`
- `financial_analysis_summary.md`
- `charts/`

### 独立使用技能3：只生成报告

```
使用 corporate-report-architect 技能生成【某某公司】的尽调报告
```

前提：已有 `intelligence_data.json` 和 `analysis_results.json`

输出：
- `尽调报告.docx`

---

## 核心脚本说明

### 1. main_coordinator.py - 主协调器

**功能**：协调3个子技能执行完整流程

**主要方法**：
- `check_dependencies()` - 检查依赖
- `run_stage_1_collection(company_name, credit_code)` - 运行阶段1：数据采集
- `run_stage_2_analysis(company_name)` - 运行阶段2：数据分析
- `run_stage_3_report(company_name)` - 运行阶段3：报告生成
- `track_progress(stage, task, status)` - 跟踪进度
- `handle_error(stage, error)` - 处理错误

### 2. dependency_checker.py - 依赖检查器

**功能**：检查子技能是否已安装

**主要方法**：
- `skill_installed(skill_name)` - 检查技能是否已安装
- `check_all_dependencies()` - 检查所有依赖
- `install_skill(skill_name)` - 安装技能（引导用户）

---

## 常见问题

### Q1: 完整流程需要多长时间？
A: 通常55-120分钟，取决于企业规模和数据量。

### Q2: 如果某个子技能未安装怎么办？
A: 系统会自动提示缺少哪些子技能，并引导用户安装。

### Q3: 可以只运行某个阶段吗？
A: 可以，直接使用对应的子技能即可。

### Q4: 如果中途失败怎么办？
A: 系统会保存已完成的阶段结果，可以从失败的阶段重新开始。

### Q5: 生成的报告可以修改吗？
A: 可以，生成的是标准Word文档，可以手动编辑。

---

## 技能安装

### 安装本技能

在Manus技能界面：
1. 点击 "+ 添加"
2. 输入仓库地址：`https://github.com/yourusername/corporate-credit-due-diligence`
3. 点击确认

### 安装子技能

**方法1：自动安装（推荐）**
- 安装本技能后，首次运行时会自动检查并提示安装缺少的子技能

**方法2：手动安装**
1. `corporate-intelligence-collector`
   - 仓库：`https://github.com/yourusername/corporate-intelligence-collector`
   
2. `corporate-data-analyst`
   - 仓库：`https://github.com/yourusername/corporate-data-analyst`
   
3. `corporate-report-architect`
   - 仓库：`https://github.com/yourusername/corporate-report-architect`

---

## 版本历史

- **v1.0.0** (2026-02-14) - 初始版本，支持完整尽调流程

---

## 许可证

Copyright © 2026 Manus AI. All rights reserved.
