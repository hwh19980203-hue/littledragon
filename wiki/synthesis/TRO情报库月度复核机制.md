---
type: synthesis
title: TRO 情报库月度复核机制
tags: [TRO, Schedule-A, Keith, monitoring, evidence]
created: 2026-11-01
updated: 2026-11-01
sources: ["[[wiki/synthesis/TRO案件涉案作品与商品线索目录]]", "[[wiki/sources/2026-11-01-Anagram官网产品目录与情人节气球线索]]"]
aliases: [TRO月检SOP, 律所情报月更]
---

# TRO 情报库月度复核机制

## 月检范围与顺序

1. 先读 [[wiki/index]]、[[wiki/synthesis/TRO案件涉案作品与商品线索目录]]、[[wiki/entities/law-firms/Keith-Vogt-Ltd]] 及所有待复核案件的 `last_checked_at`、`next_check_at`、`tro_stage`。覆盖库内其他 TRO 律所；Keith 为重点，但不以一个第三方律所标签替代法院核实。
2. 搜索上次检查以来的新 Schedule A 案、新权利人、版权号、专利号、商标号和可公开获取的被告商品附件。使用法院 docket/PACER/CourtListener、USCO/USPTO 等权利库为主；商业追踪站、中文预警站和搜索摘要仅作发现线索。
3. 逐案核验律师/律所、案号、法院、原告、权利、动议、获批命令、到期/撤销/驳回、后续初步禁令和被告名单变化。`complaint`、`motion-filed`、`granted`、`expired` 不能混用；仅出现 `ex parte motion` 且未明申请内容时 `tro_stage: unknown`。
4. 取得实际作品/注册证明、原告官网商品图、被告 listing/附件图时，分别登记来源、访问日期、截图日期、SKU/ASIN、目标市场、视觉证据等级及一对一对应状态。官网现售目录不能自动映射到历史诉讼版权号；原告商品不是被告商品。
5. 只在证据确有新增、程序状态改变、旧错误需纠正时增改 `wiki/sources/`、`wiki/entities/`、`wiki/synthesis/`；同步 [[wiki/index]]，向 [[wiki/log]] 追加增量、来源、未核边界。`raw/` 保持只读，保留既有用户改动，不自动改变产品审查的 Go/No-Go。

## 证据与通知门槛

| 等级 | 例子 | 可以入库为 | 不可以写为 |
|---|---|---|---|
| L0 发现线索 | 商业站称某案属 Keith | 待核线索 | 律所已核、TRO 已获批 |
| L1 案卷核验 | Docket 显示 Keith appearance | 已核律师出庭 | 律所实体已核、商品侵权 |
| L2 权利核验 | 起诉状列 VA 号，登记证可读取 | 本案主张权利，注明主张/登记区别 | 已与具体商品匹配 |
| L3 程序核验 | 法院命令明确签发 TRO | 历史 TRO 获批，注明日期/效力 | 永久有效、所有被告侵权 |
| L4 商品对应 | 作品图与被告 listing 图、URL/ASIN 均取得 | 商品级指控样本，附视觉比对 | 法院最终侵权认定（除非终局判决支持） |

每次月检要记“检索日—覆盖来源—新增/状态改变—未取得附件—下次复核日”。无实质变化时不制造新案件或重复改文件，可仅在定期任务运行记录中保留“无新增”。只有新 TRO 获批/到期、重要案件、具体商品证据、错误纠正或需要用户补充资料时通知；网络/认证失败也通知失败原因。**不自动推送 GitHub、不发送飞书、不发对外消息。**

## 重点官方产品目录

- [Anagram Catalogs](https://anagramballoons.com/catalogs/)：官方 2027 Valentine's Day 目录提供可复查的系列名称。[[wiki/sources/2026-11-01-Anagram官网产品目录与情人节气球线索]] 已识别 `HVD Coquette Bows`，但尚未与 2024 年 Keith 案的 18 个 VA 版权号建立一对一对应。
- [Anagram 2027 Valentine's Day 目录](https://secure.viewer.zmags.com/publication/40b20862)：优先观察与用户已提供图片相邻的 `HVD Coquette Bows`、`HVD Hearts on Hearts`、`Satin Key to My Heart`、`HVD Infinite Knots`、`Valentine Romantic Glow` 等系列。这些是**官网产品识别词**，不是已证实涉诉作品或被告商品。新增系列/货号须从目录正文逐项核实，不能据网页片段补猜。

## 固定检查输出

简报只包含：新增已核实案件数、TRO/PI 阶段变化、权利号与具体商品证据新增、关键纠错、尚未取得的高优先级附件、库内修改文件、需要用户决策之处。每条带来源链接和检索日期。
