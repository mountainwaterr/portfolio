# DESIGN SYSTEM — 100% 提取自 Darko Bratina / federicopian.com

> 来源: Darko Bratina _ Federico Pian - Freelance Creative Developer.html
> 框架: Nuxt 3 + Tailwind CSS v3.4.17 + GSAP (smooth scroll)

---

## 1. 颜色系统 (CSS Custom Properties)

### 浅色模式 (:root)
| Token | 值 | 用途 |
|---|---|---|
| `--color-bg` | `#E7E4DF` | 页面背景 |
| `--color-primary` | `#17191A` | 标题、主文字、按钮文字、SVG描边 |
| `--color-secondary` | `#505050` | 正文、元数据值、导航链接 |
| `--color-border` | `rgba(0,0,0,0.1)` | 分割线、边框、进度环底色 |
| `--color-circle` | `rgba(0,0,0,0.1)` | 圆形元素背景 |
| `--color-circle-darker` | `rgba(0,0,0,0.6)` | 进度环填充色 |
| `--color-switch` | `#000` | 主题切换按钮 |

### 深色模式 (html.dark)
| Token | 值 |
|---|---|
| `--color-bg` | `#262626` |
| `--color-primary` | `#BEBEBE` |
| `--color-secondary` | `#A0A09F` |
| `--color-border` | `hsla(0,0%,100%,0.2)` |
| `--color-circle` | `rgba(97,97,97,0.1)` |
| `--color-circle-darker` | `rgba(97,97,97,0.6)` |
| `--color-switch` | `#FFF` |

### 特定页面覆盖 (Darko Bratina 页面上 HTML 内联)
| Token | 值 |
|---|---|
| `--color-border` | `rgba(23, 25, 26, 0.2)` |
| `--color-primary` | `rgba(23, 25, 26, 1)` |
| `--color-secondary` | `rgba(80, 80, 80, 1)` |

---

## 2. 排版系统

### 字体
```css
font-family: safiro-regular, sans-serif;           /* 正文 */
font-family: safiro-medium, sans-serif;            /* 标签/按钮/导航 */
font-family: safiro-regular-i, sans-serif;         /* 斜体标题 */
font-family: safiro-semibold, sans-serif;          /* 半粗体 */
```
(替代方案: `-apple-system, 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif`)

### 流体根字号
```css
/* 移动端 < 1024px */
html { font-size: min(10 * 100vw / 390, 10px); }
/* 桌面端 ≥ 1024px */
html { font-size: min(10 * 100vw / 1920, 25.6px); }
```

### 字号层级 (参考站点 Tailwind 自定义类)
| Class | Font Size | Letter Spacing | Line Height | 用途 |
|---|---|---|---|---|
| `text-xxl` | 12.8rem | -0.05em | 0.8 | 大标题 (桌面) |
| `text-xl` | 9.6rem | -0.05em | 0.8 | 详情页标题 (桌面) |
| `text-lg` | 6.4rem | -0.05em | 1 | 项目编号 / 百分比 (桌面) |
| `text-lg2` | 3.6rem | -0.05em | 0.8 | 详情页标题 (移动) |
| `text-md` | 2.4rem | -0.05em | 1 | 次级标题 |
| `text-md2` | 2rem | -0.05em | 1.2 | 详情描述 (桌面) |
| `text-sm` | 1.6rem | -0.02em | 1.2 | 小标题 |
| `text-xs` | 1.4rem | -0.05em | 1 | 元数据标签 |
| `text-xxs` | 1.2rem | -0.05em | 1 | 元数据标签 (移动) |

---

## 3. 间距系统

单位: 1 = 0.25rem (Tailwind 默认)

### 导航
| 属性 | 移动端 | 桌面端 |
|---|---|---|
| 水平内边距 | `2rem` | `8rem` |
| 顶部间距 | `2rem` | `0` + `padding-top: 4rem` |

### 详情页布局
| 元素 | 移动端 | 桌面端 |
|---|---|---|
| 左标题 top | `7rem` | `14rem` |
| 左标题 left | `2rem` | `7.2rem` |
| 右元数据 top | `7.3rem` | `14rem` |
| 右元数据 right | `0` | `8rem` |
| 右元数据 width | `14rem` | `28.2rem` |
| Gallery top padding | `0` | `14rem` |
| Gallery bottom padding | 水平滚动 | `4rem` |
| Gallery item 间距 | `1rem` (水平) | `5rem` (垂直) |
| Gallery item width | `30rem` | `80rem` |
| Gallery item height | `17rem` | `46rem` |
| Gallery item border-radius | `2rem` | `2rem` |

### 底部元素
| 元素 | 移动端 | 桌面端 |
|---|---|---|
| 进度圆环 left/bottom | `2rem` / `2rem` | `8rem` / `4rem` |
| 进度圆环 size | `13.5rem` | `28rem` |
| 下一项目 right/bottom | `2rem` / `2rem` | `8rem` / `4rem` |
| 下一项目 size | `14rem` | `28rem` |

### CTA 按钮间距
| 属性 | 移动端 | 桌面端 |
|---|---|---|
| 内边距 | `0.5rem 1rem` | `1rem 1.5rem` |
| 圆角 | `1rem` | `1.5rem` |
| 上边距 | `1.5rem` | `4rem` |
| 左边距 | `0.2rem` | `1rem` |
| 箭头图标宽度 | `1.8rem` | `1.8rem` |

### 元数据组间距
- 标签底边距: `0.2rem`
- 组间距 (移动): `1rem`
- 组间距 (桌面): 嵌套在 flex-col 中

---

## 4. 组件规格

### 4.1 CTA 按钮 (.cta)
```css
display: inline-flex; justify-content: space-between; align-items: center;
border: 1px solid currentColor;
border-radius: 1rem (m) / 1.5rem (d);
padding: 0.5rem 1rem (m) / 1rem 1.5rem (d);
color: var(--color-primary);
/* Hover: 第一个箭头 slideOut → 第二个箭头 slideIn */
transition: transform 0.4s cubic-bezier(0.215, 0.61, 0.355, 1);
```

### 4.2 导航链接 (.nav-item)
```css
position: relative;
font-family: safiro-medium; text-transform: uppercase;
font-size: 1.2rem (m) / 1.4rem (d);
/* 下划线动画 */
::before {
  content: ''; position: absolute; bottom: -4px; left: 0;
  width: 100%; height: 1px;
  background: var(--color-secondary);
  transform: scaleX(0); transform-origin: 100% 100%;
  transition: transform 0.6s cubic-bezier(0.43, 0.195, 0.02, 1);
}
:hover::before { transform: scaleX(1); transform-origin: 0 100%; }
```

### 4.3 Gallery 图片卡片 (.item)
```css
/* 移动端 */
width: 30rem; height: 17rem;
flex-shrink: 0; margin-right: 1rem;
/* 桌面端 */
width: 80rem; height: 46rem;
margin: 0 auto 5rem;
/* 通用 */
border-radius: 2rem; overflow: hidden;
/* 图片 */
img { width: 100%; height: 100%; object-fit: cover; border-radius: inherit; }
/* 悬停缩放 */
transition: transform 1s cubic-bezier(0.165, 0.84, 0.44, 1);
:hover img { transform: scale(1.1); }
```

### 4.4 进度圆环 (.gallery-progress)
```css
position: fixed; z-index: 10;
width: 13.5rem (m) / 28rem (d);
height: 13.5rem (m) / 28rem (d);
left: 2rem (m) / 8rem (d);
bottom: 2rem (m) / 4rem (d);
/* SVG */
circle { cx: 140; cy: 140; r: 139.5; }
stroke-dasharray: 880;
stroke: var(--color-border);     /* 背景环 */
stroke: var(--color-primary);    /* 进度环 */
/* 百分比文字 */
font-size: 4rem (m) / 8rem (d);
font-family: safiro-medium;
letter-spacing: -0.05em; line-height: 0.8;
color: var(--color-primary);
```

### 4.5 下一项目预览 (.next-project)
```css
position: fixed; z-index: ?;
width: 14rem (m) / 28rem (d);
height: 14rem (m) / 28rem (d);
right: 2rem (m) / 8rem (d);
bottom: 2rem (m) / 4rem (d);
border-radius: 9999px; overflow: hidden;
/* 内容层 (absolute overlay) */
display: flex; flex-direction: column; justify-content: space-between;
text-transform: uppercase;
/* 标签 */
font-size: 1rem (m) / 1.4rem (d);
color: #FFF; text-shadow: 0 1px 2px rgba(0,0,0,0.5);
/* 圆点 */
width: 0.4rem; height: 0.4rem; border-radius: 50%;
background: var(--color-secondary);
/* 背景图片 */
img { width: 100%; height: 100%; object-fit: cover; border-radius: 9999px; }
```

### 4.6 元数据侧栏 (aside)
```css
position: fixed; z-index: ?;
width: 14rem (m) / 28.2rem (d);
top: 7.3rem (m) / 14rem (d);
right: 0 (m) / 8rem (d);
/* 项目编号 */
font-size: 3rem (m) / 6.4rem (d);
font-family: safiro-medium; text-transform: uppercase;
line-height: 0.8; color: var(--color-primary);
/* 分隔线 */
width: 3.6rem (m) / 6.4rem (d);
height: 1px (m) / 3px (d);
transform: rotate(-45deg);
background: var(--color-border);
/* 元数据标签 */
font-size: 1.2rem (m) / 1.4rem (d);
font-family: safiro-medium; text-transform: uppercase;
color: var(--color-primary);
margin-bottom: 0.2rem;
/* 元数据值 */
font-size: 1.2rem (m) / 1.4rem (d);
color: var(--color-secondary);
```

### 4.7 详情页标题 (左固定区)
```css
position: fixed; z-index: 1;
top: 7rem (m) / 14rem (d);
left: 2rem (m) / 7.2rem (d);
/* 标题 */
font-family: safiro-regular-i; font-style: italic;
font-size: 3.6rem (m) / 9.6rem (d);
line-height: 0.8; letter-spacing: -0.05em;
color: var(--color-primary);
/* 描述 */
max-width: 20rem (m) / 30rem (d);
font-size: 1.4rem (m) / 2rem (d);
font-family: safiro-regular;
line-height: 1.2; color: var(--color-secondary);
```

### 4.8 主题切换按钮
```css
width: 2rem; height: 2rem; border-radius: 9999px;
background: var(--color-switch);
```

---

## 5. 缓动函数

| 用途 | 函数 | 时长 |
|---|---|---|
| 颜色/背景过渡 | `cubic-bezier(0.4, 0, 0.2, 1)` (ease-out) | 0.3s |
| CTA 箭头滑动 | `cubic-bezier(0.215, 0.61, 0.355, 1)` | 0.4s |
| 导航下划线 | `cubic-bezier(0.43, 0.195, 0.02, 1)` | 0.6s |
| Logo 悬停 | `cubic-bezier(0.43, 0.195, 0.02, 1)` | 0.3s |
| 图片悬停缩放 | `cubic-bezier(0.165, 0.84, 0.44, 1)` | 1s |

---

## 6. Z-Index 层级

| 层级 | 元素 |
|---|---|
| -1 | Canvas 背景 |
| 1 | 玻璃噪点蒙版 / 详情页左标题 |
| 2 | 导航栏 / 页面切换层 |
| 10 | 进度圆环 / 元数据/ 预加载文字 |
| 50 | 光标尾迹图片 |
| 100 | 光标尾迹容器 |

---

## 7. 用户网站保留色（5章节背景色）

| 章节 | Color1 | Color2 | Color3 |
|---|---|---|---|
| Ch0 Hero | `255,150,85` | `185,60,100` | `223,151,173` |
| Ch1 About | `155,155,155` | `36,52,78` | `137,145,159` |
| Ch2 Experience | `2,141,234` | `113,53,114` | `141,204,246` |
| Ch3 Portfolio | `236,183,150` | `0,50,71` | `244,215,197` |
| Ch4 Contact | `208,180,72` | `195,129,113` | `237,218,213` |

---

## 8. 交互清单 (详情页)

1. **滚轮** → Gallery 垂直滚动 (桌面) / 水平滚动 (移动)
2. **进度圆环** → 随滚动位置实时更新百分比 + SVG 环填充
3. **下一项目预览** → 点击跳转到下一个章节的详情页
4. **图片悬停** → scale(1.1) 缩放 (1s ease)
5. **CTA 按钮** → 双箭头交错滑动 (0.4s)
6. **导航链接** → 下划线 scaleX 展开 (0.6s)
7. **色彩过渡** → 所有颜色属性 0.3s ease-out
8. **Gallery 图片** → 滚动触发依次淡入出现 (通过 GSAP ScrollTrigger)
