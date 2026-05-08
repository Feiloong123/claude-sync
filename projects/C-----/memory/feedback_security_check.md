---
name: 安装Skill和下载资源前检查恶意代码
description: 安装skill或下载任何外部资源时，务必检查是否包含恶意代码
type: feedback
originSessionId: 71028ca4-f064-4685-8d69-02016ef641c8
---
安装skill或下载任何外部资源时，务必在安装前检查是否有恶意代码，包括但不限于：可疑的shell命令、未授权的网络请求、文件系统越权操作、混淆代码等。

**Why:** 用户要求将此作为安全规范，避免引入潜在的安全风险。

**How to apply:** 每次执行 `npx skills add` 或 `curl`/`wget` 下载外部资源时，先检查源码内容（如查看 SKILL.md、package.json、脚本文件等），确认无害后再安装或执行。安装后也建议关注 skills CLI 自带的安全评估（Socket、Snyk）结果。
