# agent-loop-skills

「我如何把工作交给 Agent」分享的配套技能集合。分享的思路是：工作是一个循环（目标 → 计划 → 执行 → 反馈）；先看清自己的时间花在循环的哪个环节，再把可复用的部分沉淀成 Agent 可读取的上下文，让循环越转越轻；人与 Agent 共同参与沟通时，遵守同一套礼仪。

技能是写给 Agent 的工作方法说明。每个技能是一个文件夹，核心是其中的 `SKILL.md`。

## 技能列表

| 技能 | 用途 | 对应分享 |
|---|---|---|
| [work-loop-audit](skills/work-loop-audit/SKILL.md) | 读取最近 4 周的工作记录，按循环环节盘点，排出前 10 个可以交给 Agent 的事项 | 上篇 · 分析篇 |
| [loop-spec](skills/loop-spec/SKILL.md) | 为一个循环写工作流说明，补齐连接、标准、做法、触发、记忆、确认六类要素 | 中篇 · 六类要素 |
| [loop-retro](skills/loop-retro/SKILL.md) | 一轮结束后，把本人的修改意见沉淀为标准、做法、触发或记忆 | 中篇 · 沉淀与复利 |
| [my-standards](skills/my-standards/SKILL.md) | 从本人的消息和文档归纳写作标准，生成自己的规范类技能 | 中篇 · 标准 |
| [agent-etiquette](skills/agent-etiquette/SKILL.md) | 按一次来回的四步约定 Agent 起草与阅读消息的礼仪 | 下篇 · 礼仪篇 |

模板：[定时任务描述](templates/scheduled-task.md)

建议的使用顺序：`work-loop-audit` → 选一项用 `loop-spec` 落地 → 每轮结束用 `loop-retro` 沉淀；`my-standards` 和 `agent-etiquette` 在起草消息时生效。

## 安装

**Claude Code**

```bash
/plugin marketplace add <仓库地址>
/plugin install agent-loop@agent-loop-skills
```

或者把 `skills/` 下需要的文件夹复制到 `~/.claude/skills/`。

**其他 Agent 工具**：把对应 `SKILL.md` 的正文作为项目说明或自定义指令粘贴进去即可。

## 数据与合规

- 盘点类技能只读，不发送、不修改任何内容。
- 客户姓名、账户、持仓、联系方式只记类别，不写进结果和消息。
- 接入含客户数据的系统前，以所在公司合规部门的意见为准。
- 对外发送的内容一律由本人确认。

## 致谢

`loop-spec` 借鉴了 Matt Pocock 的 [loop-me](https://github.com/mattpocock/skills/tree/main/skills/in-progress/loop-me)（MIT）中的提问方法与 Trigger、Checkpoint、Push right、Brief 等概念。

## 许可证

MIT
