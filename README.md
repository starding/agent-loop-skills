# work-loops

「我如何把工作交给 Agent」分享的配套技能。一项重复出现的工作就是一个循环；这些技能帮一个人不依赖分享者，也能把自己的工作循环交给 Agent。

安装后在 Agent 里输入 `/work-loops`，它会读取工作区的状态，告诉你下一步用哪个技能。

## 目录

```
work-loops/
├── 0-start/
│   └── work-loops/          总入口：看工作区状态，告诉你下一步
├── 1-analyze/               一、建模与分析
│   └── loop-audit/
├── 2-workflow/              二、工作流：写成说明 → 运行 → 沉淀
│   ├── loop-spec/           （含定时任务模板 scheduled-task.md）
│   ├── loop-retro/
│   └── my-standards/
└── 3-etiquette/             三、协作礼仪
    └── agent-etiquette/
```

每个技能是一个文件夹，核心是其中的 `SKILL.md`：写给 Agent 的工作方法说明。

## 三个问题

| 部分 | 要回答的问题 | 技能 | 对应分享 |
|---|---|---|---|
| 一、建模与分析 | 我的时间花在哪里，哪些循环值得交给 Agent | [loop-audit](1-analyze/loop-audit/SKILL.md) | 上篇 · 分析篇 |
| 二、工作流 | 交出去的循环怎样运行，怎样一轮比一轮轻 | [loop-spec](2-workflow/loop-spec/SKILL.md)、[loop-retro](2-workflow/loop-retro/SKILL.md)、[my-standards](2-workflow/my-standards/SKILL.md) | 中篇 · 工具篇 |
| 三、协作礼仪 | Agent 代我与人沟通时，怎样守住对方的信任 | [agent-etiquette](3-etiquette/agent-etiquette/SKILL.md) | 下篇 · 礼仪篇 |

### 一、建模与分析

工作是一个循环：目标 → 计划 → 执行 → 反馈，反馈再进入下一轮。大的循环里套着小的循环：一年的目标、每周的例会、每天早上的消息处理、一份周报。

`loop-audit` 读取最近 4 周的工作记录，把任务归入环节、测量时间，找出要靠人记得去推动的环节，排出前 10 个可以交给 Agent 的循环，写进工作区。

### 二、工作流

一个循环交给 Agent 要经过三步，每一步都读写同一个工作区：

1. **写成说明**：`loop-spec` 逐轮提问，把一个候选循环写成工作流说明，写到另一个 Agent 不用再问任何问题为止。
2. **运行**：按说明创建定时任务或事件触发；简单的循环直接用 [定时任务模板](2-workflow/loop-spec/scheduled-task.md)。
3. **沉淀**：`loop-retro` 在每轮结束后，把本人的修改意见写回这份说明，下一轮不必再说。写作标准跨所有循环通用，用 `my-standards` 单独生成。

### 三、协作礼仪

`agent-etiquette` 在 Agent 起草或阅读消息时生效：按一次来回的四步（发起、接收、回复、结束）约定写法，对外发送的内容一律由本人确认。

## 工作区

三部分共用当前目录下的 `work-loops/`。文件是唯一的依据：换了会话、换了 Agent，都从这里接着做。

```
work-loops/
├── NOTES.md            本人的工作环境：用哪些系统、处理哪些渠道、各自怎么称呼
├── LOOPS.md            候选循环与状态：候选、已写说明、运行中、已放弃
└── workflows/
    └── <名称>.md       一个循环一份工作流说明；复盘的修改直接写回这里
```

| 技能 | 读 | 写 |
|---|---|---|
| work-loops | 整个工作区 | 不写 |
| loop-audit | `NOTES.md` | `NOTES.md`、`LOOPS.md` |
| loop-spec | `NOTES.md`、`LOOPS.md`、`workflows/` | `workflows/<名称>.md`，更新 `LOOPS.md` 中的状态 |
| loop-retro | `workflows/<名称>.md` | 同一份说明；写作标准写进本人的标准技能 |

## 安装

**Claude Code**

```bash
/plugin marketplace add starding/work-loops
/plugin install work-loops@work-loops
```

或者把需要的技能文件夹（例如 `1-analyze/loop-audit/`）复制到 `~/.claude/skills/`。

**其他 Agent 工具**：把对应 `SKILL.md` 的正文作为项目说明或自定义指令粘贴进去即可。

## 数据与合规

- 盘点只读取工作系统，不发送、不修改任何内容；只在本地工作区写结果。
- 客户姓名、账户、持仓、联系方式只记类别，不写进工作区和消息。
- 接入含客户数据的系统前，以所在公司合规部门的意见为准。
- 对外发送的内容一律由本人确认。

## 致谢

工作区的组织方式（工作流说明作为唯一依据、`NOTES.md` 记录本人的工作环境）、`loop-spec` 的提问方式，以及触发、确认尽量后移、给摘要不给原稿等概念，借鉴自 Matt Pocock 的 [loop-me](https://github.com/mattpocock/skills/tree/main/skills/in-progress/loop-me)（MIT）。

## 许可证

MIT
