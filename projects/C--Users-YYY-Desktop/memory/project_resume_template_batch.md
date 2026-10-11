---
name: 简历模板批量项目(生成+下载)
description: 桌面 resume_work 工作区:10000 份生成简历已完成;开源模板下载已完成(Word 2793 + 12 仓库其他格式,3901 文件);用户觉得生成质量"一般"
type: project
originSessionId: 09d680ae-df56-4d88-90f8-85374420776d
---
# 简历模板工作区 C:\Users\YYY\Desktop\resume_work\

**总背景**:用户要大量、多样的简历模板素材。工作区含两个阶段的工作:

## 阶段 1:程序化生成 10000 份(已完成,2026-10-11)
- 代码:`resume_work\resume-gen\`(generate.py / layouts.py 13 布局 / themes.py / fake_data.py / docx_helpers.py;refs\ 有 8 份参考简历)
- 成品:`resume_work\resume_templates\`(10000 份,manifest.csv)+ `resume_samples\`(8 份样例 docx+PDF)+ `_qa_pdf\`、`_qa_png\`
- 质检 10000/10000 通过;重跑逻辑:run() 跳过已存在且 >1500B 文件;签名由 BASE_SEED=20261011 确定性生成
- **用户评价:质量"一般"**——尚未细化改进需求,后续若用户再提需先问清期望

## 阶段 2:网络下载开源模板(已完成,2026-10-11)
- 目标目录:`resume_work\downloaded_templates\`;**按 格式→来源→模板类型 分类**;合计 3901 文件/1.3GB
- Word 2793 份:HICV 2132(15 类,需署名 HICV.cn)+ ResumeCollection 661(5 类,MIT),全部下载成功 0 失败
- 其他 12 仓库:LaTeX 213 文件(Awesome-CV 等 6 仓)、Markdown 31(3 仓)、HTML 857(best-resume-ever/DeerResume/startbootstrap-resume)
- 关键经验:raw.githubusercontent.com 本机被限速(~0.3 文件/s,32 线程也没用);codeload.github.com 整包 ZIP 可达 ~10MB/s → **批量下载一律走 codeload 整包**,逐文件 raw 仅作兜底
- 脚本:`_meta\download_templates.py` + `extract_word_zips.py`(断点续跑);清单 `_meta\word_files.json`;README.txt 记录了来源/许可
- 无法达成 10000:国内模板站禁抓取/付费版权,开源 docx 存量约 2800;用户已确认"Word 为主 + 混入其他格式"方案

**Why**:用户要模板素材库(可能商用/模板库),要求分类整理;先有自产 10000 份,再补充网络真实模板。

**How to apply**:改动生成器后需删受影响 docx 重跑;下载任务可断点续跑(跳过已存在 >1KB);hicv 素材商用/再发布需标注 HICV.cn 来源。
