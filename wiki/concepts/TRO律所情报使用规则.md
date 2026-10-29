---
type: concept
title: TRO 律所情报使用规则
tags: [TRO, law-firm, Schedule-A, evidence, workflow]
created: 2026-10-28
updated: 2026-10-28
sources: ["[[wiki/dashboards/TRO律所情报库]]", "[[wiki/dashboards/Keith-TRO情报看板]]"]
aliases: [TRO律所预警规则, 律所历史联动规则]
---

# TRO 律所情报使用规则

## 核心判断

```mermaid
flowchart LR
    A[产品或关键词] --> B{命中律所历史?}
    B -->|否| C[常规五层检索]
    B -->|是| D[增强检索]
    D --> E[核对权利人与权利号]
    E --> F[取得作品图/专利图/商标]
    F --> G[核对目标市场效力]
    G --> H[产品实质比对]
    H --> I[核对最新 TRO 阶段]
    I --> J[形成产品风险结论]
```

## 联动等级

| 命中情况 | 处理 | 能否单独改变产品结论 |
|---|---|:---:|
| 只命中律所名称 | 增加律所名、律师名和近 12 个月案件检索 | ❌ |
| 命中律所 + 权利人 | 检索该权利人的全部相关案件与权利清单 | ❌ |
| 命中律所 + 具体权利号 | 强制取得官方权利状态和案件文件 | ⚠️ 仍需产品比对 |
| 命中有效权利 + 产品实质相似 + TRO 已获批 | 至少上调一级，不得 Go | ✅ |
| 用户已收到冻结/传票 | 立即保存通知、案号、店铺和资金证据，转专业律师处理 | ✅ 实操高风险 |

## 产品审查页新增记录

每次命中律所历史时，产品页至少记录：

- `matched_law_firms`
- `matched_rights`
- `matched_cases`
- `law_firm_match_basis`
- `tro_stage`
- `stage_evidence`
- `last_checked_at`

## 禁止事项

- 不得因为“Keith/GBC/HSPRD/JiangIP 代理过类似产品”直接判侵权。
- 不得用律所网站、商业追踪页或中文预警代替法院 TRO 命令。
- 不得把同一案件中的共同代理重复统计为两宗案件。
- 不得把历史 TRO 写成当前仍在执行；必须记录日期和最新阶段。

