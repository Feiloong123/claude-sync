---
name: 简历模板批量生成项目
description: 用户目标:程序化批量生成一万份形式各异的简历 Word(.docx)模板
type: project
originSessionId: 09d680ae-df56-4d88-90f8-85374420776d
---
# 简历模板批量生成项目(进行中)

**任务**:生成 10,000 份形式各样的简历 Word 模板(.docx)。

**已确定的技术方案**(2026-10-11 与用户确认):
- 路线:纯程序化组合生成(布局 × 主题 × 字体 × 密度 × 语言 × 栏目组合),非 AI 逐份生成
- 内容:程序生成逼真假数据(中英文姓名、职业方向、公司、学校、量化成就条目)
- 环境:Windows 11,Python 3.12.10,python-docx 1.2.0 + lxml 6.1.0 已装,MS Word(Office16)可用于视觉 QA,无需装 docxtpl
- 调研结论:现成简历 skill(如 ZiyuAI/resume-builder-skill、paramchoudhary/resumeskills)都是"JD 定制单份简历"模式,不适用批量模板;以 anthropics/skills@docx(官方,199K 安装)作为 python-docx 技术参考底座
- 输出规划:C:\Users\YYY\Desktop\resume_templates\,按布局分文件夹 + manifest.csv,round-trip 校验 + 哈希查重,预估渲染 20~80 分钟

**Why**:用户需要大批量、高多样性的简历 Word 模板素材(可能用于模板库/商业素材)。

**How to apply**:后续会话若涉及此任务,按"纯程序化组合 + 假数据 + QA"方案继续;方案设计已到规划阶段(布局清单、主题规格、组合策略),尚未写代码。
