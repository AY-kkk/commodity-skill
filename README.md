<p align="center">
  <strong>简体中文</strong> · <a href="README.en.md">English</a>
</p>

<h1 align="center">大宗商品期货研究 Skill 库</h1>
<p align="center"><strong>为 AI 助手提供基本面、价格关系与风险研究方法。</strong></p>
<p align="center">产业供需 · 宏观驱动 · 基差价差 · 交割结构 · 贸易风险</p>
<p align="center">
  <a href="#skill-清单"><strong>13 Skills</strong></a>
</p>
<p align="center">
  <a href="#从研究问题开始">研究场景</a> ·
  <a href="#输入与输出示例">输出示例</a> ·
  <a href="#skill-清单">Skill 清单</a> ·
  <a href="#安装与首次调用">开始使用</a>
</p>

## 为什么需要这套 Skill

商品研究需要把产业事实、价格关系和风险敞口放在同一口径下。库存下降未必代表全国短缺，期货单腿盈利也不能说明套保业务盈利。

本库把这些研究任务拆成可调用的方法：确定品种、地区与期限，核对数据与单位，复算关键关系，再给出有证据、能被推翻的判断。

## 从研究问题开始

| 你要研究什么 | 先用哪个 Skill | 交付物 |
|---|---|---|
| 库存与利润为何背离？ | 基本面与研究观点 | 供需归因、基准与相反情景、观点失效条件 |
| 现货下跌，套保业务是否仍盈利？ | 基差与套保 | 期现双腿损益、费用及未覆盖敞口 |
| PTA 与乙二醇为何强弱不同？ | 跨品种研究 | 经济联系、各自驱动、两腿贡献与反证 |
| 政策、天气或汇率怎样影响商品？ | 宏观 / 天气 / 外汇 | 传导路径、兑现时点和待验证指标 |
| 仓单减少意味着交割紧张吗？ | 交割与期限结构 | 可交割货源、批次资格及持有成本核查 |
| 需要从报告建模或更新原表？ | 平衡表搭建 / 维护 | 可追溯输入、明确假设及计算验证 |

## 如何开展研究

1. **定对象**：明确品种、地区、合约、观察日与交付物。
2. **选方法**：由专业 Skill 主办，跨主题时交接变量、单位、期间和证据。
3. **做验证**：区分事实、假设与缺口，复算关键关系，检验相反情景。
4. **交结论**：写明依据、未覆盖风险、失效条件与下一次核验数据。

<p align="center">
  <img src="assets/skill-collaboration.png" width="920" alt="专业研究为主体，平衡表搭建与维护为按需调用的辅助流程">
</p>

**1 个研究入口 + 10 个专业研究 Skill + 2 个辅助工作流。** 图表示任务分工；平衡表仅在需要建模时调用。研究入口现有路由覆盖 10 个专业 Skill，搭建和维护可按名称直接调用。

## 输入与输出示例

以下均为仓库已有的**合成教学算例**，数字用于展示核算过程。

### 现货亏损，期现合计结果是多少？

**输入**：同地、同品级、同一合约，100 吨现货与等量期货空头完全对冲。现货价 3,000 → 2,960 元/吨，期货价 3,050 → 2,980 元/吨；全期费用 12 元/吨。

| 核算项目 | 结果 |
|---|---:|
| 现货损益 | −4,000 元 |
| 期货损益 | +7,000 元 |
| 合计毛收益 | +3,000 元 |
| 扣费后净收益 | **+1,800 元** |

输出同时解释：基差由 −50 走强至 −20 元/吨，每吨毛收益 30 元；实际业务仍需核对合约乘数、数量和费用。

<details>
<summary>展开计算过程</summary>

```text
现货损益 = (2,960 − 3,000) × 100 = −4,000 元
期货损益 = (3,050 − 2,980) × 100 = +7,000 元
净收益 = −4,000 + 7,000 − 12 × 100 = +1,800 元
```

</details>

### 产品上涨，加工利润也会上升吗？

**输入**：每吨产品报价 7,200 元，原料单耗 3 吨、原料价 2,200 元/吨，加工费 450 元/吨产品；仅考虑上述收支。随后产品涨 90 元/吨，原料涨 50 元/吨，加工费不变。

**输出**：利润代理值由 **150 降至 90 元/吨产品**，减少 60 元。解释价格变化时按单耗折算原料，而非只看两种价格的涨跌方向；联产装置还需补充副产品收入等项目。

<details>
<summary>展开计算过程</summary>

```text
初始利润代理值 = 7,200 − 3 × 2,200 − 450 = 150 元/吨产品
变化 = 90 − 3 × 50 = −60 元/吨产品
变化后 = 150 − 60 = 90 元/吨产品
```

</details>

## Skill 清单

### 研究入口

| Skill | 用途 |
|---|---|
| [研究入口](skills/commodity-research-guide/SKILL.md) | 研究方法选择、术语查询与跨主题分工 |

### 基本面与驱动

| Skill | 用途 |
|---|---|
| [基本面与研究观点](skills/commodity-fundamental-thesis/SKILL.md) | 产业供需、库存与利润分析，建立可证伪观点 |
| [油脂研究](skills/commodity-oils/SKILL.md) | 豆油、棕榈油、菜油产业链及现货研究 |
| [宏观研究](skills/commodity-macro/SKILL.md) | 宏观与政策向商品需求、成本的传导 |
| [天气影响](skills/commodity-weather/SKILL.md) | 天气对产量、物流及供需时点的影响 |
| [外汇研究](skills/commodity-fx/SKILL.md) | 汇率驱动、收付汇敞口与锁汇成本 |

### 定价、结构与风险

| Skill | 用途 |
|---|---|
| [基差与套保](skills/commodity-basis/SKILL.md) | 现货点价、基差交易与期现合并损益 |
| [有色价差](skills/commodity-metals-spread/SKILL.md) | 有色月差、持有成本与进口窗口 |
| [交割与期限结构](skills/commodity-delivery-structure/SKILL.md) | 仓单、可交割货源与期限结构 |
| [跨品种研究](skills/commodity-cross-commodity/SKILL.md) | 跨品种强弱、加工利润、伴生及替代关系 |
| [贸易风险](skills/commodity-trade-risk/SKILL.md) | 履约、信用、货权、结算与资金风险 |

### 辅助工作流：平衡表

| Skill | 用途 |
|---|---|
| [平衡表搭建](skills/commodity-balance-sheet-build/SKILL.md) | 从报告整理历史数据与假设，搭建供需模型 |
| [平衡表维护](skills/commodity-balance-sheet-maintain/SKILL.md) | 更新已有平衡表，核对期间、产能与公式传导 |

## 安装与首次调用

获取仓库：

```bash
git clone https://github.com/AY-kkk/commodity-skill.git
```

将 `commodity-skill/skills/` 下所需的 **Skill 目录整体**放入所用 AI 助手的 Skill 目录，保留 `SKILL.md`、`references/` 及已有的 `agents/`。安装路径按客户端配置确定；替换已有目录前先核对内容。

启动新任务并描述问题、资料和截止日期，例如：

```text
使用 $commodity-fundamental-thesis 分析我提供的月报。
品种：甲醇；范围：全国；观察截止日：以附件为准。
解释库存与利润背离，区分事实与假设，列出相反证据和观点失效条件。
```

不确定用哪个方法时，先调用 `$commodity-research-guide`。Skill 正文以中文为主；执行取数、PDF 或 Excel 操作需要客户端具备相应工具。

## 仓库结构

```text
commodity-skill/
├── README.md                         # 中文入口
├── README.en.md                      # English
├── assets/skill-collaboration.png     # 研究协作图
└── skills/
    ├── commodity-research-guide/      # 研究入口与参考资料
    ├── commodity-fundamental-thesis/  # 专业研究之一
    ├── commodity-*/                   # 其余专业研究 Skill
    ├── commodity-balance-sheet-build/ # 平衡表搭建
    ├── commodity-balance-sheet-maintain/ # 平衡表维护
    ├── BUILD_MANIFEST.json            # 原始研究包构建记录
    └── capability-destinations.json   # 原始能力映射
```

## 使用边界

历史教学参数与当前市场输入分开；现行规则、合约和费用按研究日核实。研究结论应给出验证条件，文件操作遵循用户授权，新增文件或工作表须先获同意。
