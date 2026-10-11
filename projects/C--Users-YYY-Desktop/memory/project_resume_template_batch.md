---
name: 简历模板批量生成项目
description: 程序化批量生成一万份形式各异的简历 Word(.docx)模板;10000 份已全部生成并通过质检
type: project
originSessionId: 09d680ae-df56-4d88-90f8-85374420776d
---
# 简历模板批量生成项目(10000 份已完成)

**任务**:生成 10,000 份形式各样的简历 Word 模板(.docx)。

**已确定的技术方案**(2026-10-11 与用户确认):
- 路线:纯程序化组合生成(布局 × 主题 × 字体 × 密度 × 语言 × 栏目组合),非 AI 逐份生成
- 内容:程序生成逼真假数据(中英文姓名、职业方向、公司、学校、量化成就条目)
- 环境:Windows 11,Python 3.12.10,python-docx 1.2.0,MS Word COM 转 PDF + PyMuPDF 渲染 PNG 做视觉 QA
- 输出:C:\Users\YYY\Desktop\resume_templates\,按布局分文件夹 + manifest.csv + qa_report.txt

**当前进度**(2026-10-11,已完成):
- 生成器 5 个模块:themes.py / fake_data.py / docx_helpers.py / layouts.py(13 种布局)/ generate.py
- 用户要求"先下载真实简历学习布局再展示样例":已下载 8 份开源参考简历到 resume-gen\refs\,据此新增 gutter(日期左栏)、block(深色信息条带)、light_left(左侧浅色侧栏)3 种布局
- **全量已完成**:10000 份生成(9970 秒级重跑+30 测试批次跳过,0 失败,10.2 分钟),最终 QA 10000/10000 通过(0 打开错误、0 重复、150s),manifest.csv 10000 行
- 产物:C:\Users\YYY\Desktop\resume_templates\(按 13 个布局分子目录)+ resume_samples\(8 份代表样例 docx+PDF)

**Why**:用户需要大批量、高多样性的简历 Word 模板素材(可能用于模板库/商业素材);用户明确要求生成前先参照真实简历布局并人工确认样例。

**How to apply**:若用户后续要求修改样式或增减,改 layouts.py/themes.py/fake_data.py 后需删除受影响 docx 再重跑(run() 会跳过已存在且 >1500 字节的文件);新增文件用 --count 保持与 build_signatures 的确定性一致。
