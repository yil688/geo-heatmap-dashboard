# 区域经营热力图谱 · Regional Business Heatmap

交互式地理数据可视化看板：把区域经营指标映射为地图热力分布，支持多指标切换与联动下钻。

An interactive geospatial dashboard that maps regional business metrics onto a heat distribution, with multi-metric switching and linked drill-down.

**在线预览 / Live Demo** — [https://yil688.github.io/regional-heatmap/](https://github.com/yil688/geo-heatmap-dashboard/blob/main/regional-heatmap)

---

## ⚠️ 数据声明 / Data Notice

本项目为**个人技术作品展示**。页面内所有经营数值均为**脱敏示意数据**：逐条独立扰动并整体缩放，单条字段与各口径汇总指标相对原值的失真幅度均超过 15%，且已校验派生指标与聚合指标不存在方向抵消。数据**不代表任何企业的真实经营结果**。景区名称与地理坐标属公开地理信息；区域标识使用匿名代号。

This is a **personal portfolio piece**. All business figures are **anonymized placeholder data**: independently perturbed per record and globally rescaled, with every individual field and every aggregate metric deviating more than 15% from any original value, verified to contain no directional cancellation in derived or aggregated indicators. The figures **do not represent the actual performance of any company**. Scenic spot names and coordinates are public geographic information; regional identifiers are anonymous codes.

---

## ✨ 功能 / Features

**热力图渲染 · Heatmap rendering**
两阶段离屏 Canvas 合成：先按指标值加权叠加高斯光斑并累加 alpha，再查 256 色 LUT 上色。相邻点位的光斑自然相加，表达的是"区域总量"而非点位密度。
Two-pass offscreen Canvas compositing — value-weighted Gaussian blobs accumulate in alpha, then map through a 256-entry LUT. Adjacent points sum naturally, expressing *regional totals* rather than point density.

**极值隔离 · Outlier isolation**
头部单点量级远超次高值，若参与颜色分档会把其余点位压成一片浅色。归一化分母剔除极值，极值自身单独给饱和峰值，可通过开关还原。
A top-tier outlier would flatten the entire color scale. It is excluded from the normalization denominator while still rendering at saturated peak, toggleable at runtime.

**多指标切换 · Multi-metric switching**
营业额 / 毛利值 / 毛利率 / 单客价值四个口径，热力层、图例刻度、排行榜同步重算。
Four metrics — revenue, gross profit, margin, per-customer value — with heat layer, legend scale and ranking recomputed in sync.

**行政边界层 · Administrative boundaries**
内嵌市州级矢量边界，当前区域覆盖的市州加深描边与填充，解决纯热力图难以辨认"点位落在哪个市"的问题。
Embedded prefecture-level vector outlines; the active region's coverage is emphasized, solving the "which city does this point belong to" ambiguity of a bare heatmap.

**联动下钻 · Linked drill-down**
榜单点击飞行定位并展开详情卡片，层级筛选与图层开关实时生效。
Click a ranking row to fly to its marker and open the detail card; level filters and layer toggles apply instantly.

---

## 🛠 技术栈 / Tech Stack

- 原生 HTML / CSS / JavaScript — 零构建、零框架、单文件交付
  Vanilla HTML / CSS / JS — no build step, no framework, single-file delivery
- [Leaflet](https://leafletjs.com/) 1.9.4 — 地图引擎 / map engine
- 自研 Canvas 热力层 — 扩展 `L.Layer`，含缩放自适应半径与色彩查找表
  Custom Canvas heat layer extending `L.Layer`, with zoom-adaptive radii and a color lookup table
- 行政边界数据 / Boundary data — [DataV.GeoAtlas](https://datav.aliyun.com/portal/school/atlas/area_selector)（GCJ-02，已抽稀 / simplified）

## 🎨 设计 / Design

米白纸面 × 墨色 × 朱砂的报刊式版式：衬线标题、等宽数字、全局纸面噪点与印章元素，弱化仪表盘的工业感。

A newsprint-inspired layout in off-white, ink black and cinnabar: serif headings, tabular figures, global paper grain and seal motifs, deliberately avoiding the industrial feel of a typical dashboard.

## 📄 License

MIT
