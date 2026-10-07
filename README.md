# Emil 设计技能集 · 中文导读

本仓库是 [Emil Kowalski 设计技能集](https://github.com/emilkowalski/skills)的个人镜像。收录 14 个技能，帮助设计师与工程师把界面、动画和移动端体验做得更好。技能内容保持上游原样；下半部分是上游 README 的中文译文，英文原文见 [README.en.md](./README.en.md)。

## 安装

```bash
npx skills@latest add toRolex/emil-design-skills
```

## 按场景怎么用

**以下分组与推荐顺序是本镜像的归纳，不是上游规定的统一流程。** 不必把所有技能串起来；根据当前问题选用即可。

| 场景 | 技能 | 用法 |
| --- | --- | --- |
| 日常界面与动画决策 | `emil-design-eng` | 独立可用；作为通用设计工程指导 |
| 把动画需求说清楚 | `animation-vocabulary` | 独立可用；先明确运动、节奏和过渡的表达 |
| Apple 风格设计原则 | `apple-design` | 独立可用；将 Apple 的设计与流畅动效原则用于 Web |
| Swift 开发 | `write-swift` | 独立可用；现代 Swift、并发、性能与测试 |
| Sonner 提示组件 | `ask-sonner` | 独立可用；安装、样式、常见用法与排错 |
| 手机上的 Web 体验 | `mobile-native` | 独立可用；修复触摸、视口、安全区等细节 |
| 选择 UI 依赖 | `pick-ui-library` | 独立可用，需显式调用；先选合适的库，避免重复造轮子 |
| 极端数据压测 | `break-ui` | 独立可用；用长文本、空列表、大数字等尝试破坏界面 |
| 探索多个 UI 方向 | `prototype` | 需显式调用；生成不同方案，通过切换器比较与选择 |

### 动画闭环：找机会 → 定计划 → 实现 → 复核

推荐组合顺序：

```text
find-animation-opportunities
  → improve-animations
  → animate（Web）或 animate-expo（React Native / Expo）
  → review-animations
```

- `find-animation-opportunities`：找出值得加入动效的位置，同时明确哪些地方不该动。
- `improve-animations`：审计已有动画，产出按优先级排列、可独立执行的改进计划。
- `animate` / `animate-expo`：分别负责 Web 与 React Native / Expo 的动画实现。
- `review-animations`：严格复核动画，需要显式调用。

这是一条推荐工作路径，不要求每次从头走完。已有明确动画需求可从实现开始；只想审查已有动画可直接调用复核。

**`animate` 硬依赖 `pick-ui-library` 的场景**：当任务需要 toast、drawer、command menu、dropdown 等组件，而不只是动画时，上游明确要求停下来调用 `pick-ui-library`，先选对组件库；此时不可跳过。单纯的动画任务不要求一律调用它。

### 需要显式调用的 3 个技能

`review-animations`、`pick-ui-library`、`prototype` 在上游设置了 `disable-model-invocation: true`，不会由模型自行触发。使用时主动点名调用；具体入口以所用工具为准。

---

# 上游 README · 中文译文

以下内容译自 Emil Kowalski 的上游 README；保留原结构与链接。文中“我”指原作者 **Emil Kowalski**，并非镜像维护者。

<a href="http://aiforui.dev/">
<img width="360" height="202" alt="opengraph-image 2" src="https://github.com/user-attachments/assets/84fca9a6-0b2b-4927-8f48-f3ce194a5c47" />
</a>

# 面向设计师与工程师的技能

[![skills.sh](https://skills.sh/b/emilkowalski/skills)](https://skills.sh/emilkowalski/skills)

帮助设计师与工程师构建更好的用户界面。

无论是动画还是一般设计，要判断自己是否做出了正确选择，都不容易。这些技能旨在帮助你更快地做出正确决策。

它们来自我在 Vercel、Linear 等公司多年的工作经验。

这里所有技能都是领域专长积累的产物。AI 不会取代这样的专长，而是放大它的价值，让你相比他人做得更好。

所以，去学习编程、设计，或培养任何其他领域的专长。这非常有价值。

你可以在这里关注我的技能更新：

[订阅通讯](https://aiforui.dev/skills)

## 安装

```bash
npx skills@latest add emilkowalski/skills
```

## 为什么使用它？

Agent 的品味并不出色。

我见过很多次，Agent 没有为动画选对要素：本该用 `ease-out` 的入场动画，却用了 `ease-in`（[原因在这里](https://emilkowal.ski/ui/7-practical-animation-tips#4.-choose-the-right-easing)）；或者给界面选择了实色边框，而不是半透明阴影。

这些小细节叠加起来，会让你的界面非常出色，或者……没那么好。

正如 [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste) 中所解释的，这些技能列出 Agent 可能犯的细小错误，并说明如何修正。

这是通往优秀界面的捷径，也是从大量粗劣作品中脱颖而出的捷径。

## 参考

- **[emil-design-eng](./skills/emil-design-eng/SKILL.md)** — 核心技能，主要包含动画建议，也有一些设计建议。
- **[animate](./skills/animate/SKILL.md)** — 从零构建动画，选择正确的曲线、时长、属性等。
- **[animate-expo](./skills/animate-expo/SKILL.md)** — 将同样的标准用于 React Native 和 Expo：手势、面板、触觉反馈、页面转场，以及让动画不占用 JS 线程。
- **[review-animations](./skills/review-animations/SKILL.md)** — 按照我的规则严格审查你的动画。
- **[improve-animations](./skills/improve-animations/SKILL.md)** — 审计代码库中的所有动画，生成按优先级排列、完整独立且任何 Agent 都能执行的计划。
- **[find-animation-opportunities](./skills/find-animation-opportunities/SKILL.md)** — 在 UI 中寻找真正能从动效受益的位置，同时告诉你哪些地方不该加动画。
- **[animation-vocabulary](./skills/animation-vocabulary/SKILL.md)** — 使用准确的词汇，向 AI 明确表达你的需求，从而获得更好的动画。
- **[apple-design](./skills/apple-design/SKILL.md)** — 从 Apple 的 WWDC 设计演讲中提炼界面设计与流畅动效原则，并转化为适用于 Web 的指导。
- **[write-swift](./skills/write-swift/SKILL.md)** — 编写现代 Swift，涵盖值类型、Swift 6 并发、泛型、性能和 Swift Testing。
- **[pick-ui-library](./skills/pick-ui-library/SKILL.md)** — 让 Agent 根据我使用并信赖的库为任务选择合适的依赖，而不是让 AI 手写 toast 组件或安装无人维护的包。
- **[prototype](./skills/prototype/SKILL.md)** — 为你描述的 UI 部分构建多个不同版本，并通过切换器逐一比较。
- **[mobile-native](./skills/mobile-native/SKILL.md)** — 让 Web 应用在手机上拥有原生感：修复悬停状态残留、点击高亮闪烁、100vh 问题、输入框导致页面缩放、点击延迟、安全区，以及其他区分网站与应用的小细节。
- **[break-ui](./skills/break-ui/SKILL.md)** — 用最糟糕的数据尝试破坏你构建的 UI：长姓名、特殊邮箱、单字姓名、巨大计数、空列表、长标签。
- **[ask-sonner](./skills/ask-sonner/SKILL.md)** — 使用我的 toast 库 [Sonner](https://sonner.emilkowal.ski) 的指南，包含设置、样式、常见用法，以及最常见问题的修复方法。
