---
name: 简历模板批量生成项目
description: 用户目标:程序化批量生成一万份形式各异的简历 Word(.docx)模板;生成器已完成,测试批次通过,待用户确认后全量
type: project
originSessionId: 09d680ae-df56-4d88-90f8-85374420776d
---
# 简历模板批量生成项目(测试通过,待全量)

**任务**:生成 10,000 份形式各样的简历 Word 模板(.docx)。

**已确定的技术方案**(2026-10-11 与用户确认):
- 路线:纯程序化组合生成(布局 × 主题 × 字体 × 密度 × 语言 × 栏目组合),非 AI 逐份生成
- 内容:程序生成逼真假数据(中英文姓名、职业方向、公司、学校、量化成就条目)
- 环境:Windows 11,Python 3.12.10,python-docx 1.2.0,MS Word COM 转 PDF + PyMuPDF 渲染 PNG 做视觉 QA
- 输出:C:\Users\YYY\Desktop\resume_templates\,按布局分文件夹 + manifest.csv + qa_report.txt

**当前进度**(2026-10-11):
- 生成器 5 个模块已完成:themes.py / fake_data.py / docx_helpers.py / layouts.py(13 种布局)/ generate.py
- 用户要求"先下载真实简历学习布局再展示样例":已下载 8 份开源参考简历到 resume-gen\refs\,据此新增 gutter(日期左栏)、block(深色信息条带)、light_left(左侧浅色侧栏)3 种布局
- 30 份测试批次已通过双重质检(round-trip 零错误、零重复)+ 全部关键布局视觉目检
- 8 份代表样例(8 docx + 8 PDF)已导出到 C:\Users\YYY\Desktop\resume_samples\ 供用户查看
- **下一步:等用户看过样例确认后,跑 `python generate.py --count 10000 --start 1` 全量生成(约 10~15 分钟,后台)**

**Why**:用户需要大批量、高多样性的简历 Word 模板素材(可能用于模板库/商业素材);用户明确要求生成前先参照真实简历布局并人工确认样例。

**How to apply**:后续会话涉及此任务时,先检查 resume_templates\manifest.csv 行数判断全量是否已跑;若用户对样例提出修改意见,改 layouts.py/themes.py 后需删除受影响 docx 重新生成(run() 会跳过已存在文件)。
