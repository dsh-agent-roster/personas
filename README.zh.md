# 单人人设

[English](README.md) | **简体中文**

一份 [Agent Roster](https://github.com/dsh-agent-roster/dsh-agent-roster) 档案，装的是**单个会话的身份**：
每份档案没有成员，只带一个 `captain.persona`。把它应用到已有会话，会话就以这个人设工作——不建团、不派成员。

| 档案 | 应用到会话后它会怎么做 |
|---|---|
| `code-reviewer` | 只审不改：按「会不会让线上出错」排序，每条结论都落到文件行号、命令输出或调用链 |
| `architect` | 先约束后方案：两三个候选与各自代价，写清这次不做什么、失败怎么退 |
| `debugger` | 先复现再改：一次只验一个假设，修复最小，收口给复现命令与前后输出 |

## 这不是迁移

本组织里其它档案来自上游仓库；这三份是**为本项目写的**，不是从某处复制的。我们看过的上游单 agent 系统提示
（SWE-agent 的 `system_template`、OpenHands 的 Jinja 模板、gemini-cli 的 TypeScript 提示构造器）要么只有一句
框架话，要么是带模板变量的片段——逐字搬过来，反而不如自己写一份完整的人设。

## 用法

```bash
npx --yes @stofone/dsh-agent-roster@latest validate --dir .     # 3 份人设，各 0 名成员
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
