[English](README.md) · [中文](README.zh.md)

# 第二大脑模板

[![Obsidian](https://img.shields.io/badge/Obsidian-483699?style=flat&logo=obsidian&logoColor=white)](https://obsidian.md)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat&logo=anthropic&logoColor=white)](https://claude.ai/code)
[![PARA Method](https://img.shields.io/badge/PARA-Method-4CAF50?style=flat)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

基于 **Obsidian** 和 **Claude Code** 的 AI 增强个人知识管理系统。使用 PARA 方法组织内容，通过分层 Wiki 进行知识编织，借助 AI 实现上下文感知检索——让你的笔记成为一个与你共同成长的工作记忆。

---

## 问题

你收集了大量笔记、书签、高亮和想法——但它们躺在文件夹里，从不相互连接。需要时找不到，找到时缺乏上下文。

这个模板通过三层设计解决这个问题：

1. **清晰的结构** — PARA 将行动项与参考资料分离
2. **知识层** — Wiki 将原始材料编织成实体、概念和分析
3. **AI 层** — Claude Code 理解你的知识图谱，自动检索相关上下文

> 把它想象成一座记忆宫殿，AI 是你的图书管理员。

---

## 目录结构

```
Second Brain/
├── Inbox/                  # 先把所有内容捕获到这里
├── Projects/               # 有截止日期的活跃项目
├── Areas/                  # 持续的责任领域（无终点）
├── Resources/              # 原始材料——文章、报告、笔记
├── Archives/               # 已完成或暂停的项目
├── Identity/               # 你是谁——使命、上下文、偏好
│   ├── TELOS.md            # 你的目标和愿景
│   ├── CONTEXT.md          # 当前状态和活跃项目
│   └── PROFILE.md          # 沟通风格和偏好
├── System/                 # 运维支持
│   └── working-memory/     # 任务、日志、操作规则
│       ├── tasks.md
│       ├── OPERATING_RULES.md
│       └── daily/          # 每日交互日志
├── Wiki/                   # 编织后的知识（真正的价值）
│   ├── index.md            # 知识地图——AI 检索的入口
│   ├── entities/           # 人物、公司、项目（具体事物）
│   ├── concepts/           # 想法、框架、方法论（抽象事物）
│   ├── analyses/           # 深度研究报告
│   └── overviews/          # 领域全景导览
└── .claude/
    └── CLAUDE.md           # AI 系统提示词——大脑的操作系统
```

---

## 工作原理

### 1. 捕获

把任何内容保存到 `Inbox/` 或 `Resources/`。文章、会议笔记、随机想法——先不用整理，先捕获。

### 2. 编织

AI 处理原始材料并编织进 Wiki：

```
关于 EigenLayer 的文章 (Resources/)
        ↓ AI 处理
Wiki/entities/EigenLayer.md      — 结构化的实体页面
Wiki/concepts/Restaking.md       — 概念提取
Wiki/analyses/EigenLayer-Thesis  — 投资分析
        ↓ AI 连接
[[EigenLayer]] ←→ [[Ethereum]] ←→ [[DeFi-Core-Concepts]]
```

每个 Wiki 页面包含：
- **Frontmatter** 记录来源、标签和创建日期
- **双向链接** 连接相关知识
- **来源追溯** 回溯到 Resources/ 中的原始材料

### 3. 检索

当你提问时，AI 沿着检索路径查找：

```
你：「EigenLayer 的投资逻辑是什么？」
        ↓
AI 读取 Wiki/index.md → 找到 [[entities/EigenLayer]]
        ↓
AI 读取实体页面 → 沿链接找到分析、概念
        ↓
AI 基于你的知识回答，而非通用训练数据
```

### 4. 演化

系统自我维护：
- **Frontmatter 一致性** — 元数据与文件位置保持同步
- **索引更新** — Wiki/index.md 反映最新知识
- **知识坏味道** — AI 检测孤岛笔记、过时内容、断裂链接
- **身份追踪** — 偏好和操作规则随时间积累

---

## 快速开始

### 第一步：克隆

```bash
git clone https://github.com/Nowhitestar/second-brain-template.git "My Second Brain"
```

### 第二步：在 Obsidian 中打开

1. 打开 Obsidian → 「打开文件夹作为仓库」
2. 选择克隆的目录
3. 启用社区插件（Dataview、Templater 等）

### 第三步：配置 Claude Code

`.claude/CLAUDE.md` 已预配置。你需要自定义：

1. 编辑 `Identity/TELOS.md` — 定义你的使命和目标
2. 编辑 `Identity/CONTEXT.md` — 描述你当前的工作重点
3. 编辑 `Identity/PROFILE.md` — 设置你的沟通偏好

### 第四步：开始使用

```bash
# 在你的仓库目录打开 Claude Code
claude

# 试试这些：
# 「帮我整理 Inbox」
# 「我关于 [主题] 知道什么？」
# 「总结一下我的活跃项目」
```

---

## AI 层

`.claude/CLAUDE.md` 将 Claude Code 变成知识感知助手。主要能力：

### 上下文检索

AI 根据你讨论的内容自动加载相关知识：

```
检索路径：
1. 根据话题判断相关的 PARA 目录
2. 读取目录说明文件获取成员清单
3. 根据标题和摘要匹配相关内容
4. 检查 Resources/ 下的跨领域内容
5. 搜索 Wiki/index.md → 加载匹配的实体/概念
```

### 三层记忆

| 层级 | 内容 | 触发 | 存储位置 |
|------|------|------|---------|
| **日常碎片** | 对话日志 | 自动，每次会话 | `System/working-memory/daily/` |
| **周度蒸馏** | 模式识别 | 每周触发 | 候选池 |
| **稳定偏好** | 确认的习惯 | 用户审批 | `Identity/PROFILE.md` |

### 知识编织流程

```
Inbox/Resources → AI 处理 → Wiki/（实体、概念、分析）
                                ↓
                         index.md 更新
                                ↓
                         双向链接创建
                                ↓
                        Frontmatter 验证
```

### 变更控制

| 类型 | 操作 | 审批 |
|------|------|------|
| **A 类** | 文件归档、标签补全、README 同步 | 自动 |
| **B 类** | Identity 变更、新增分类 | 需审批 |
| **C 类** | 顶层目录改动、系统提示词改动 | 需审批 |

---

## 自定义

### 调整 PARA 结构

编辑每个 PARA 目录中的 README.md 以匹配你的领域。模板提供了起点——根据需要重命名、添加或删除目录。

### 自定义检索

编辑 `.claude/CLAUDE.md` 中的 `<RETRIEVAL>` 部分来改变搜索优先级。例如，如果你主要在某个领域工作，可以优先检索该目录。

### 添加 Wiki 分类

默认 Wiki 有四个分类：entities、concepts、analyses、overviews。根据需要添加更多（如 `decisions/`、`people/`、`tools/`）。

### 推荐 Obsidian 插件

| 插件 | 用途 |
|------|------|
| **Dataview** | 查询和展示笔记数据 |
| **Templater** | 高级笔记模板 |
| **QuickAdd** | 快速捕获工作流 |
| **Graph Analysis** | 可视化知识连接 |

---

## 架构

### 三层分形设计

```
L1  .claude/CLAUDE.md       — 全局规则（是 L2/L3 的折叠）
L2  目录 README.md          — 局部地图、成员清单
L3  笔记 frontmatter        — 内容契约、归属定位
```

每层自相似：L1 是 L2 的压缩，L2 是 L3 的压缩。目录 README 充当分布式索引——不需要单独的索引文件（Wiki/index.md 除外，用于 AI 检索）。

### 同构原则

> 结构与内容必须保持同步。任何一方的变化必须在另一方体现。

这意味着：
- 新增文件 → 更新目录 README
- 移动文件 → 更新 frontmatter + 新旧目录 README
- 删除文件 → 更新目录 README
- 创建目录 → 创建其 README

### 知识坏味道（反模式）

| 坏味道 | 描述 |
|--------|------|
| **孤岛** | 有价值内容与其他知识无连接 |
| **冗余** | 同一想法在多处重复存在 |
| **僵化** | 过时内容仍标记为活跃 |
| **混沌** | 大量内容堆积在 Inbox 未归类 |
| **断裂** | 链接指向已删除/移动的文件 |
| **空洞** | 目录存在但无 README 或成员 |

---

## 安全与隐私

- **本地优先**：所有数据保存在你的 Obsidian 仓库
- **无云依赖**：离线可用，通过 iCloud/Git 同步
- **身份保护**：Identity 文件变更需要明确审批
- **变更审计**：B/C 类变更进入审批队列

---

## 致谢

灵感来源：
- [Tiago Forte 的 PARA 方法](https://fortelabs.com/blog/para/)
- [MemPalace](https://github.com/Nowhitestar/openclaw-memory-palace) — AI 的记忆宫殿概念
- [Obsidian](https://obsidian.md) — 本地优先知识管理
- [Claude Code](https://claude.ai/code) — AI 驱动的开发工具

---

## 许可

MIT 许可 — 详情见 [LICENSE](LICENSE)。
