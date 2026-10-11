# AI 与词元经济数据看板

一个**单文件、零依赖**的可交互数据看板，用于「凡能仙·今经乐道」经济热点分析大赛。

开箱即用：所有数据内嵌在 `index.html` 中，不需要后端、不需要联网、不需要任何依赖。

---

## 看板包含 11 个分栏

| 分栏 | 内容 |
|---|---|
| **词元价格天梯** | 369 个在售模型的输入价格排行，可按厂商筛选、点表头排序 |
| **价格时间轴** | 208 个有确切发布日期的模型，价格 vs 发布时间散点 |
| **厂商价格区间** | 11 家厂商的最低价—最高价区间条 + 中位数 |
| **公司发展速率** | 10 家公司的 ECI 前沿增速对比（点/年）与前沿曲线 |
| **数据中心用电** | 全球（2010–2030E）与中国（2017–2030E） |
| **数据中心数量** | 全球超大规模数据中心 · 中国在用标准机架 |
| **算力与资本开支** | 英伟达数据中心收入（含 FY27 Q1/Q2）· 2026 云厂商 capex |
| **词元消耗量** | 中国日均调用量 · 谷歌月度处理量 · 中国智能算力 |
| **股价走势** | 美股 10 年 / A 股归一化走势，图例可隐藏 |
| **量化指标体系** | 六层指标体系 + 三层价值核算 + 单位任务成本价值阶梯 + 指标黑名单 + 数据缺口 |
| **价值与分配** | 单位算力价值阶梯（价差 70–160×）、AI 头部公司 ARR、Agent 任务词元消耗倍数、算力去向（训练 vs 推理） |
| **数据信源** | 42 条原始来源，分 10 组列出，带可点击原网址与搜索 |

## 交互功能

- **纵坐标等比/等差一键切换**——价格跨度数千倍时，等比看清低端，等差反映绝对差距
- **纵轴最大/最小值可手填**——数据差距过大时手动收窄范围，避免散点重合看不清
- 厂商标签筛选 · 搜索 · 表头排序 · 时间范围选择 · 图例开关 · 悬停查看详情

---

## 部署到 GitHub Pages（三种方式，任选其一）

### 方式一：网页上传（最简单，无需 Git）

1. 登录 GitHub，点右上角 **+ → New repository**
2. 仓库名填 `token-economy-dashboard`，可见性选 **Public**，点 **Create repository**
3. 进入仓库，点 **uploading an existing file**
4. 把本文件夹里的 **全部文件**（`index.html`、`README.md`、`.nojekyll`、`LICENSE`）拖进去
   > ⚠️ `.nojekyll` 是隐藏文件，Windows 需在资源管理器「查看」里勾选「隐藏的项目」才能看到
5. 点 **Commit changes**
6. 进入 **Settings → Pages**
7. **Source** 选 `Deploy from a branch`，**Branch** 选 `main` + `/ (root)`，点 **Save**
8. 等 1–2 分钟，访问：`https://你的用户名.github.io/token-economy-dashboard/`

### 方式二：命令行

```bash
cd token-economy-dashboard
git init
git add .
git commit -m "Add token economy dashboard"
git branch -M main
git remote add origin https://github.com/你的用户名/token-economy-dashboard.git
git push -u origin main
```

推送后同样到 **Settings → Pages** 开启（Source 选 `main` / `/ (root)`）。

### 方式三：作为已有仓库的子目录

把 `index.html` 放到仓库根目录或 `docs/` 目录，然后在 **Settings → Pages** 里
把 Source 指向该目录即可。

---

## 常见问题

**Q：为什么必须有 `index.html` 这个名字？**
A：GitHub Pages 默认把 `index.html` 作为站点入口。如果你用中文文件名（如 `看板.html`），
URL 会被编码成一长串 `%E7%9C%8B...`，既难看又容易出错。

**Q：`.nojekyll` 有什么用？**
A：GitHub Pages 默认用 Jekyll 处理站点，会忽略以下划线开头的文件和目录。
加一个空的 `.nojekyll` 可以跳过 Jekyll，避免意外问题。

**Q：打开后没看到最新版？**
A：浏览器会缓存。按 `Ctrl + F5`（Mac 是 `Cmd + Shift + R`）强制刷新。

**Q：数据会更新吗？**
A：不会。所有数据在构建时已内嵌，是静态快照。需要更新数据请重新生成 `index.html`。

---

## 数据来源

| 数据 | 来源 |
|---|---|
| 模型价格（369 个） | LiteLLM 官方挂牌价库 |
| 模型发布日期（208 个） | OpenRouter 模型接口 |
| 能力指数 ECI（274 个模型） | Epoch AI Capabilities & benchmarking |
| 任务时间跨度（48 个模型） | METR Time Horizon 1.1 |
| 数据中心用电 | IEA / IEA-4E / 中国信通院 |
| 数据中心数量 | Synergy Research Group / 工信部 |
| 算力与资本开支 | 英伟达官方财报 / TrendForce |
| 词元消耗量 | 国家数据局 / 谷歌 I/O 2026 |
| 股价 | 纳斯达克官方行情接口 / 东方财富 |

各分栏内均标注了具体来源与口径说明。

---

## 许可

代码部分采用 MIT 许可。数据部分版权归各自来源所有，请遵循原始来源的许可条款。

生成日期：2026-10-11
