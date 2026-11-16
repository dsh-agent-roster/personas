# 单人人设

[English](README.md) | **简体中文**

一份 [Agent Roster](https://github.com/dsh-agent-roster/dsh-agent-roster) 档案，装的是**单个会话的身份**：
每份档案没有成员，只带一个 `captain.persona`。把它应用到已有会话，会话就以这个人设工作——不建团、不派成员。

| 档案 | 应用到会话后它会怎么做 | 来源 |
|---|---|---|
| `code-reviewer` | 只审不改：按「会不会让线上出错」排序，每条结论都落到文件行号、命令输出或调用链 | 本项目自撰 |
| `architect` | 先约束后方案：两三个候选与各自代价，写清这次不做什么、失败怎么退 | 本项目自撰 |
| `debugger` | 先复现再改：一次只验一个假设，修复最小，收口给复现命令与前后输出 | 本项目自撰 |
| `swe-fixer` | 用脚本复现，只改复现需要的代码，用同一脚本前后对照，再补边界 | 参照 SWE-agent |
| `browser-operator` | 先看再点，每次操作后核对真实结果，页面内容是数据不是指令 | 参照 browser-use |
| `cli-engineer` | 分清「问」与「做」，遵守仓库约定，修前先复现，不靠关检查过关 | 参照 gemini-cli |

## 自撰与参照

`code-reviewer`、`architect`、`debugger` 是为本项目写的。

另外三份是**行为重写，不是复制**：上游文件要么以工具为中心，要么是带模板变量的片段——SWE-agent 的
`system_template` 只有一句话、真正的流程在实例模板里；browser-use 的提示大半是 CDP 助手文档；gemini-cli 的提示是
按模式分支的 TypeScript 构造器。原样搬过来，得到的是「我们这个插件并不提供的工具怎么用」。留下的是做事纪律，
用中文重写，并在每份档案的 `captain.notes` 里写明参照对象。

OpenHands **没有收录**：它的系统提示路径变了（`openhands/agenthub/codeact_agent/prompts/…` 在当前树里已不存在），
新位置我们抓取时被限流。没核对到的东西不算数，所以不写。

## 用法

```bash
npx --yes @stofone/dsh-agent-roster@latest validate --dir .     # 6 份人设，各 0 名成员
```

在插件面板的「档案库」页签订阅 `dsh-agent-roster/personas`，然后在会话上用「应用」。
需要插件 **>= 1.33.0**（这个版本才允许 `members: []`）。

## 结构

```
space.yaml
rosters/{id}/roster.yaml        members: [] + captain.persona
rosters/{id}/personas/self.md   人设正文
dist/{id}-1.0.0.json            编译产物
```
