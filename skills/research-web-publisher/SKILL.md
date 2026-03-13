---
name: research-web-publisher
description: 调研报告网页发布工作流。用于将调研内容发布为可在线查看的HTML网页，并推送到GitHub生成国内可访问的镜像链接。触发场景：(1) 用户要求发布调研报告 (2) 需要将HTML部署到线上 (3) 需要生成国内可访问的链接 (4) 完成从内容到网页发布的完整流程 (5) 用户发送"研究"、"调研"、"分析"等关键词时自动触发
---

# Research Web Publisher

将调研内容发布为网页的完整工作流。

## ⚠️ 输出目录规则（重要）

**生成的 HTML 文件必须统一放到 `workplace-doc` 文件夹**，不要散落在其他位置。

示例路径：
```
/Users/jasperchen/.openclaw/workspace-aiquanzi/workplace-doc/xxx.html
```

## 适用场景

- 发布调研报告、市场分析、内容创作
- 需要生成国内可访问的HTML链接
- 从原始内容到在线查看的完整流程

## ⚠️ 触发条件（重要）

当用户发送以下内容时，**必须**自动触发此skill：
- 包含"研究"、"调研"、"分析"、"研究报告"等词
- 包含"研究•"（带特殊字符）格式
- 包含"/"分隔的多主题（如"研究• 千问 / 阿里"）
- 要求发布到网页/网站/博客

**重要：内容排版要求**
- 必须**图文并茂**，不能是纯文字
- 需要包含截图、图标、代码高亮等视觉元素
- 排版要美观专业，适合在线阅读
- 可以使用卡片式布局、徽章、代码块等元素

**不要**在没有触发skill的情况下仅创建飞书文档！

## 工作流程

### 1. 收集需求

与用户确认：
- 源文件路径（HTML/markdown/文档）
- 标题和元信息
- 是否需要飞书文档版本
- GitHub仓库信息（已有还是新建）

### 2. 推送到 GitHub

```bash
cd <repo-path>
git add <file>
git commit -m "Add/update report"
git push
```

### 3. 生成国内访问链接

使用 jsDelivr CDN：
```
https://cdn.jsdelivr.net/gh/<username>/<repo>@main/<filename>
```

预览链接：
```
https://htmlpreview.github.io/?<jsdelivr-url>
```

## 输出格式

完成后向用户返回：
1. jsDelivr 国内镜像链接（主要使用）✅

## 注意事项

- jsDelivr 需要仓库公开才能使用
- 飞书文档适合纯内容
