# 日照间距计算器 · Sunlight Spacing Calculator

> 面向城市规划师与建筑师的方案阶段快速估算工具，根据城市纬度、日照标准与遮挡建筑高度，估算住宅建筑所需的最小日照间距。

### 🔗 [▶ 立即打开使用](https://mxy1129-oss.github.io/sunlight-spacing-calculator/)

[![Live Demo](https://img.shields.io/badge/▶-在线试用-2563eb?style=for-the-badge)](https://mxy1129-oss.github.io/sunlight-spacing-calculator/) ![Static](https://img.shields.io/badge/纯前端-HTML%2FJS-94a3b8) ![Standard](https://img.shields.io/badge/参考-GB%2050180--2018-475569) ![License](https://img.shields.io/badge/license-MIT-green)

## 在线使用

直接访问 → **https://mxy1129-oss.github.io/sunlight-spacing-calculator/**

无需安装、无需登录、无需后端。也可直接克隆后用浏览器打开 `index.html`，无需任何构建。

## 功能

- **30+ 常用城市预设**：哈尔滨、北京、上海、广州、海口…自动同步纬度
- **三种日照标准**：大寒日 ≥ 2h / 3h、冬至日 ≥ 1h，覆盖 GB 50180 各气候区
- **核心指标**：所需最小间距 L、间距系数 L/H、太阳高度角 h、太阳方位角 A
- **建筑朝向修正**：支持南偏东/南偏西 ±45° 范围
- **侧视示意图**：SVG 实时渲染太阳、建筑、阴影投影、窗台线
- **规范对照**：自动与各气候区常用 L/H 区间对比，提示是否满足

## 计算原理

太阳高度角（球面三角法）：
```
sin(h) = sin(φ)·sin(δ) + cos(φ)·cos(δ)·cos(ω)
```

太阳方位角（自正南起算，西为正）：
```
sin(A) = cos(δ)·sin(ω) / cos(h)
```

日照间距（投影到建筑朝向法线方向）：
```
L = (H − H₁) · cos(A − α) / tan(h)
```

参数说明：
- `φ` 地理纬度（°N）
- `δ` 太阳赤纬：冬至 −23.45°，大寒约 −20.0°
- `ω` 时角，15° / 小时，正午为 0
- `H` 遮挡建筑高度
- `H₁` 被遮挡建筑窗台高度（默认 0.9 m）
- `α` 建筑朝向相对正南的偏角

**日照时段边界算法**：取所需连续日照小时数 T，按对称布置在太阳正午两侧，取边界时刻 ω = ±T/2 × 15° 计算，取阴影投影较长者作为最不利时刻。

## 适用场景

- 控规 / 修详方案阶段的容积率与建筑布局验算
- 设计前期快速判断楼栋间距合理性
- 教学演示太阳几何与日照间距关系

## 局限

仅用于规划方案阶段的快速估算，不替代专业日照分析。最终方案应使用众智日照、Ecotect、Ladybug 等专业软件进行多时段、多遮挡体的精确仿真，并以正式日照分析报告为准。

## 技术栈

零依赖纯前端：单文件 `index.html`（HTML + CSS + Vanilla JS + 内联 SVG）。可直接托管在 GitHub Pages、对象存储或任意静态服务器。

## 规范参考

- GB 50180-2018《城市居住区规划设计标准》
- GB 50352-2019《民用建筑设计统一标准》
- 各地方城市规划管理技术规定

## License

MIT
