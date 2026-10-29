---
type: dashboard
title: TRO 律所情报库
tags: [TRO, law-firm, Schedule-A, dashboard, litigation-intelligence]
created: 2026-10-28
updated: 2026-10-28
sources: ["[[wiki/concepts/TRO律所情报使用规则]]"]
aliases: [TRO律所库, Schedule A律所库, 侵权律所预警库]
---

# TRO 律所情报库

> [!danger] 使用边界
> 本库是“执行能力预警库”，不是侵权黑名单。律所有历史 TRO 只能触发更严格检索，不能单独把产品判为 No-Go。

## 全部律所

![[TRO律所库.base#全部律所]]

## 高优先级

![[TRO律所库.base#高优先级]]

## 版权 TRO 律所

![[TRO律所库.base#版权TRO律所]]

## 商标 TRO 律所

![[TRO律所库.base#商标TRO律所]]

## 待复核

![[TRO律所库.base#待复核]]

## 已核验律所

| 律所 | 已核验 TRO 案最低数 | 代表案件 | 重点领域 |
|---|---:|---|---|
| [[wiki/entities/law-firms/Keith-Vogt-Ltd]] | 2 | Anagram、Bonsall | 版权 |
| [[wiki/entities/law-firms/Greer-Burns-Crain]] | 2 | Turner、NBCUniversal | 商标、品牌周边 |
| [[wiki/entities/law-firms/HSPRD]] | 1 | Art Ask Agency | 版权、装饰图案 |
| [[wiki/entities/law-firms/JiangIP-LLC]] | 1 | Bonsall | 版权；曾与 Keith 联合出现 |
| [[wiki/entities/law-firms/TME-Law-PC]] | 1 | Warner Bros. | 商标、影视娱乐品牌周边 |
| [[wiki/entities/law-firms/Sriplaw-PA]] | 1 | C.H. / Your True Nature | 商标与版权并行 |
| [[wiki/entities/law-firms/Ference-Associates-LLC]] | 2 | Nixon、Winget | 版权、宾夕法尼亚西区 Schedule A |
| [[wiki/entities/law-firms/Whitewood-Law-PLLC]] | 1 | Yanushevskaya | 版权、印花与装饰图案 |
| [[wiki/entities/law-firms/Epstein-Drangel-LLP]] | 1 | Rovio / Angry Birds | 商标、角色与游戏品牌周边 |

> [!note] 数量口径
> 上表是本库“已打开法院 docket 并确认 TRO 命令”的最低案件数，不是律所真实案件总数，也不用于律所排名。

## 产品审查触发方式

发现以下任一匹配时，进入增强排查：

1. 产品品牌/角色/图案与该律所已核验客户或权利主题接近。
2. 搜索结果同时出现律所名、权利人、版权号/商标号或案号。
3. 同类产品已有该律所申请 TRO 的官方案件。

进入增强排查后，仍须依次取得：具体权利 → 作品/商标/专利图 → 目标市场效力 → 产品比对 → 最新法院阶段。

## 关联页面

- [[wiki/dashboards/Keith-TRO情报看板]] — 案件级看板
- [[wiki/concepts/TRO律所情报使用规则]] — 产品审查中的联动规则
- [[wiki/entities/law-firms/_template]] — 新律所录入模板

