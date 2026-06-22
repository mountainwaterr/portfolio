# DESIGN SYSTEM — 张韵婷 Portfolio v2

> 参考: federicopian.com | 框架: 纯 HTML/CSS/JS | 动画: GSAP 3.12.5 | 背景: Canvas 2D

---

## 1. 颜色系统

### 浅色模式
| Token | 值 | 用途 |
|---|---|---|
| `--bg` | `#E7E4DF` | Canvas 底色 |
| `--primary` | `#0D0E0F` | 标题/主文字 |
| `--secondary` | `#2A2A2A` | 正文/Caption |
| `--muted` | `#8A8780` | 辅助/禁用 |
| `--border` | `rgba(0,0,0,0.2)` | 分割线/边框/进度环底 |
| `--circle-bg` | `rgba(0,0,0,0.08)` | 圆形占位背景 |
| `--circle-fill` | `rgba(0,0,0,0.55)` | 进度环填充 |
| `--switch` | `#000` | 主题切换按钮 |

### 深色模式
| Token | 值 |
|---|---|
| `--bg` | `#262626` |
| `--primary` | `#E8E8E8` |
| `--secondary` | `#C0C0BF` |
| `--muted` | `#8A8A88` |
| `--border` | `hsla(0,0%,100%,0.2)` |
| `--switch` | `#FFF` |

### 章节配色 (Canvas 光球 3 色)
| 章节 | Color1 | Color2 | Color3 |
|---|---|---|---|
| Hero | `255,150,85` | `185,60,100` | `223,151,173` |
| About | `155,155,155` | `36,52,78` | `137,145,159` |
| Experience | `2,141,234` | `113,53,114` | `141,204,246` |
| Work | `236,183,150` | `0,50,71` | `244,215,197` |
| Skills | `208,180,72` | `195,129,113` | `237,218,213` |

---

## 2. 排版系统

### 字体
```css
font-family: -apple-system, 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif;
```
(原始参考: Safiro 商业字体, 替代: 系统无衬线栈)

### 流体根字号
```css
/* 移动 < 1024px */
html { font-size: min(14 * 100vw / 390, 14px); }
/* 桌面 ≥ 1024px */
html { font-size: min(14 * 100vw / 1920, 20px); }
```

### 字号层级
| 用途 | rem | 移动 (~px) | 桌面 (~px) | 字重 | 行高 | 字间距 |
|---|---|---|---|---|---|---|
| Hero 标题 | `clamp(4.8rem,8vw,12.8rem)` | ~67 | ~256 | 400 italic | 0.85 | -0.04em |
| 章节标题 | `clamp(3.6rem,6vw,9.6rem)` | ~50 | ~192 | 400 italic | 0.85 | -0.04em |
| Hero tagline | `clamp(1.6rem,2.5vw,2.2rem)` | ~22 | ~44 | 300 | 1.6 | 0.02em |
| 正文 | `1.4rem` | ~20px | ~28px | 300 | 1.8 | 0.02em |
| 辅助文字 | `1.2rem` | ~17px | ~24px | 400 | 1 | -0.05em |
| 导航 | `1.2rem` | ~17px | ~24px | 500 | 1.2 | 0 |
| CTA 按钮 | `1.2rem` | ~17px | ~24px | 500 | 1 | 0.04em |

### 文字阴影
```css
/* 标题在 Canvas 彩色背景上的可读性 */
text-shadow: 0 0 3px rgba(255,255,255,0.4);  /* Hero */
text-shadow: 0 0 2px rgba(255,255,255,0.35); /* 章节标题 */
```

---

## 3. 间距系统

| Token | rem | 移动 (~px) | 桌面 (~px) | 用途 |
|---|---|---|---|---|
| xs | 0.5rem | 7 | 10 | 紧凑间距 |
| sm | 1rem | 14 | 20 | 元素间距 |
| md | 1.5rem | 21 | 30 | 段落间距 |
| lg | 2rem | 28 | 40 | 模块间距 |
| xl | 4rem | 56 | 80 | 大区块 |
| 2xl | 8rem | 112 | 160 | 页面内边距 |

### 导航 padding
- 移动: `2rem 2rem`
- 桌面: `4rem 8rem 10rem` (上/左右/下)

### 章节 padding
- 移动: `6rem 2rem`
- 桌面: `10rem 8rem`

---

## 4. 圆角系统

| 用途 | 移动 | 桌面 |
|---|---|---|
| CTA 按钮 | `1rem` | `1.5rem` |
| 圆形元素 | `9999px` | `9999px` |
| 光标预览图 | `7px` | `7px` |
| 主题切换 | `9999px` | `9999px` |
| Tag 标签 | `1rem` | `1rem` |

---

## 5. 组件清单

### 导航栏 `.nav`
- 固定顶部, z-index:100
- Logo: 左, 斜线动画 hover
- 链接: 中英双语, 下划线 scaleX 动效 0.6s
- 主题切换: 右, 圆形按钮 2rem×2rem

### 章节 `.chapter`
- 全屏 fixed, 5 个叠加, opacity 切换
- 每个章节 data-colors 存储 3 色

### CTA 按钮 `.cta`
- 描边按钮, 双 SVG 箭头接力滑动
- 过渡: 0.4s cubic-bezier(0.215,0.61,0.355,1)

### 进度圆环 `.progress-wrap`
- SVG circle r=139.5, stroke-dasharray:880
- 中心数字 "1/5" 格式
- 左右箭头 CTA 动效
- 底部 "Project" 标签
- 右侧描述文字 (仅桌面)

### 光标尾迹 `.cursor-preview`
- 5 张 fixed 图片 slot
- GSAP 交错动画: 淡入 0.06s → 保持 0.28s → 淡出 0.18s
- 50ms 生成间隔, 5 槽轮换

### Canvas 背景
- 8 个柔光球, sin/cos 漂移
- 鼠标 50% 范围内 pull 系数 0.5
- createRadialGradient, 多层透明度 0.55→0

### 暗色噪点蒙版 `.glass-overlay`
- 仅 dark mode 显示
- SVG 噪点纹理 + steps(3) 动画

---

## 6. 缓动函数

| 用途 | 函数 | 时长 |
|---|---|---|
| 颜色/背景过渡 | `cubic-bezier(0.4,0,0.2,1)` | 0.3s |
| 导航下划线 | `cubic-bezier(0.43,0.195,0.02,1)` | 0.6s |
| CTA 箭头 | `cubic-bezier(0.215,0.61,0.355,1)` | 0.4s |
| 图片缩放 | `cubic-bezier(0.165,0.84,0.44,1)` | 1s |
| 进度环 | `cubic-bezier(0.19,1,0.22,1)` | 0.8s |

---

## 7. Z-Index 层级

| 层级 | 元素 |
|---|---|
| 0 | Canvas 背景 |
| 1 | 玻璃噪点蒙版 |
| 2 | 章节层 |
| 50 | 光标尾迹图片 |
| 96 | 滚动提示 |
| 98 | 右下圆形预览 |
| 99 | 左下进度圆环 |
| 100 | 导航栏 |

---

## 8. 交互清单

1. 滚轮 → 切换章节 (800ms 防抖, deltaY>10)
2. 键盘 ←↑↓→ → 切换章节
3. 触控滑动 → 切换章节 (40px 阈值)
4. 导航点击 → 跳转章节
5. CTA 点击 → 跳转 About
6. 主题切换 → 0.3s 全局过渡
7. Canvas 光球 → 鼠标 50% 范围拉动
8. 光标尾迹 → GSAP 交错淡出
