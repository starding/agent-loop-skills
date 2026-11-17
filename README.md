# agent-loop-skills

「我如何把工作交给 Agent」分享的配套技能集合。目标是让一个人不依赖分享者，也能把自己的工作交给 Agent。过程中要回答三个问题，技能也按这三个问题分成三组：

| 部分 | 要回答的问题 | 技能 | 对应分享 |
|---|---|---|---|
| 一、建模与分析 | 我的时间花在哪里，哪些循环值得交给 Agent | [work-loop-audit](skills/work-loop-audit/SKILL.md) | 上篇 · 分析篇 |
| 二、工作流 | 交出去的循环怎样运行，怎样一轮比一轮轻 | [loop-spec](skills/loop-spec/SKILL.md)、[loop-retro](skills/loop-retro/SKILL.md)、[my-standards](skills/my-standards/SKILL.md)、[定时任务模板](templates/scheduled-task.md) | 中篇 · 工具篇 |
| 三、协作礼仪 | Agent 代我与人沟通时，怎样守住对方的信任 | [agent-etiquette](skills/agent-etiquette/SKILL.md) | 下篇 · 礼仪篇 |

技能是写给 Agent 的工作方法说明。每个技能是一个文件夹，核心是其中的 `SKILL.md`。

## 一、建模与分析

工作是一个循环：目标 → 计划 → 执行 → 反馈，反馈再进入下一轮。大的循环里套着小的循环：一年的目标、每周的例会、每天早上的消息处理、一份周报。

`work-loop-audit` 读取最近 4 周的工作记录，把任务归入环节、测量时间，找出要靠人记得去推动的环节，排出前 10 个可以交给 Agent 的循环。结果写进工作区，供第二部分接着用。

## 二、工作流

一个循环交给 Agent，要经过三步，每一步都读写同一个工作区：

1. **写成说明**：`loop-spec` 逐轮提问，把一个候选循环写成工作流说明。写到另一个 Agent 不用再问任何问题为止。
2. **运行**：按说明创建定时任务或事件触发；简单的循环直接用定时任务模板。
3. **沉淀**：`loop-retro` 在每轮结束后，把本人的修改意见写回这份说明或对应的标准，下一轮不必再说。写作类的标准用 `my-standards` 单独生成。

## 三、协作礼仪

`agent-etiquette` 在 Agent 起草或阅读消息时生效：按一次来回的四步（发起、接收、回复、结束）约定写法，对外发送的内容一律由本人确认。

## 工作区

三部分共用一个工作区，默认是当前目录下的 `agent-loop/`。文件是唯一的依据：换了会话、换了 Agent，都从这里接着做。

```
agent-loop/
├── NOTES.md            本人的工作环境：用哪些系统、处理哪些渠道、各自怎么称呼
├── LOOPS.md            候选循环：盘点结果，以及每个循环的状态（候选、已写说明、运行中、已放弃）
└── workflows/
    └── <名称>.md       一个循环一份工作流说明；复盘的修改直接写回这里
```

| 技能 | 读 | 写 |
|---|---|---|
| work-loop-audit | `NOTES.md` | `NOTES.md`、`LOOPS.md` |
| loop-spec | `NOTES.md`、`LOOPS.md`、`workflows/` | `workflows/<名称>.md`，更新 `LOOPS.md` 中的状态 |
| loop-retro | `workflows/<名称>.md` | 同一份说明；写作标准写进本人的标准技能 |

## 安装

**Claude Code**

```bash
/plugin marketplace add starding/agent-loop-skills
/plugin install agent-loop@agent-loop-skills
```

或者把 `skills/` 下需要的文件夹复制到 `~/.claude/skills/`。

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
