# 黑伞专利侵权审核知识库 — 操作规范

本文档是 Schema 层配置，指导 LLM 如何维护本知识库。

## 目录结构

```
raw/                      # 原始资料（不可变，只读）
  └── assets/             # 附件图片（Obsidian 自动存入）
wiki/                     # LLM 维护的知识库
  ├── index.md            # 内容索引（LLM 维护）
  ├── log.md              # 操作日志（LLM 追加）
  ├── overview.md         # 领域总览
  ├── entities/           # 实体页：专利、公司、产品、人物
  ├── concepts/           # 概念页：法律概念、技术概念
  ├── sources/            # 资料来源摘要
  ├── synthesis/          # 综合分析/对比/问答页
  ├── products/           # 产品审查记录（用户创建，LLM 辅助分析）
  ├── cases/              # 已结案归档的产品审查
  └── dashboards/         # Dataview 看板页面
```

## 页面模板

所有 Wiki 页面使用统一 frontmatter 格式：

```yaml
---
type: entity | concept | source | synthesis | product-review | dashboard
title: 页面标题
tags: [标签1, 标签2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: ["[[raw/xxx.md]]"]
aliases: [别名1]
---
```

正文使用标准 Markdown。

## 命名规范

| 页面类型 | 格式 | 示例 |
|---------|------|------|
| 实体页 | `实体名称.md` | `华为技术有限公司.md` |
| 概念页 | `概念名称.md` | `等同原则.md` |
| 来源摘要 | `YYYY-MM-DD-简短描述.md` | `2026-05-10-最高院专利侵权判例.md` |
| 综合页 | 主题名.md | `华为vs三星专利对比分析.md` |

## 工作流

### Ingest（收录资料）

当用户将新资料放入 `raw/` 并通知你时：

1. 读取 `raw/` 中的新资料，理解内容
2. 与用户讨论要点和关注方向
3. 在 `wiki/sources/` 创建摘要页面
4. 更新或创建相关的 `wiki/entities/` 和 `wiki/concepts/` 页面
5. 如果发现关联或矛盾，在 `wiki/synthesis/` 中添加分析
6. 更新 `wiki/index.md` 添加新页面条目
7. 追加 `wiki/log.md` 记录本次操作

### Query（问答查询）

当用户提问时：

1. 读取 `wiki/index.md` 定位相关页面
2. 读取具体页面获取详细信息
3. 综合答案（可生成 Markdown 表格、列表等格式）
4. 如果答案有长期价值，存入 `wiki/synthesis/` 并更新索引
5. 追加 `wiki/log.md` 记录本次查询

### Review（产品侵权审查）

当用户提交一个待审产品时：

1. 读取产品信息，确认产品类型、目标市场和关键特征
2. 检索相关专利：使用智慧芽（以图搜图）、USPTO PPUBS、WIPO、CNIPA、EUIPO 等数据库
3. 整理检索结果，识别相关专利列表
4. 制作权利要求对照表（Claim Chart），逐项比对
5. 结合全面覆盖原则和等同原则评估侵权风险
6. 生成风险评估结论（cleared / risky / blocked）
7. 更新产品审查页，写入检索记录和分析结论
8. 更新 wiki/index.md 和 wiki/log.md

### Lint（健康检查）

当用户要求检查时：

1. 审查页面间的矛盾和陈旧断言
2. 识别孤儿页（无入链页面）
3. 发现缺少交叉引用的页面
4. 建议新的探索方向和资料来源
5. 追加 `wiki/log.md` 记录检查结果

## 链接规范

- 页面间引用使用 `[[wiki/路径/页面名]]` 格式
- 引用原始资料使用 `[[raw/文件名]]` 格式
- 同义词/别名记录在 frontmatter 的 `aliases` 字段

## Dataview 兼容

所有页面 frontmatter 包含 `type`、`tags`、`created`、`updated` 字段，支持 Dataview 查询。
