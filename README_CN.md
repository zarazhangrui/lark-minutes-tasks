[English](README.md) | 中文

# 飞书妙记行动项

一个 AI Agent skill：读取飞书妙记逐字稿，提取行动项，然后直接帮你把事办了。不是生成待办清单，是真的去执行。

## 它能做什么

给它一个妙记链接（或者会议纪要文档链接），它会：

1. 读取完整的逐字稿
2. 扫描你设置的 Wake Word（你在会议中对 agent 说的指令）
3. 提取所有行动项，包括明确说出来的和隐含的
4. 对每一项制定执行方案（约会、起草消息、搜索信息、创建文档等）
5. 展示一个编号列表，你选哪些让 agent 来处理
6. 执行。搞定。

## Wake Word

设一个触发词（随便什么词都行）。开会时说出来，会后 agent 会从逐字稿里把你的指令捞出来。你不需要记住自己在会上说了什么，agent 替你记着。

## 安装

把 `minutes.md` 放到你的 agent 的 commands 目录下：

**Claude Code：**

```bash
cp minutes.md ~/.claude/commands/minutes.md
```

**其他 Agent：**
放到你的 agent 读取 skill/command 定义的目录下即可。

## 前置条件

- 安装并配置好 [Lark CLI](https://github.com/larksuite/cli)（`lark-cli config init`）
- 完成用户授权（`lark-cli auth login --domain all`）

## 使用

```
/minutes https://your-lark-instance.com/minutes/your-minute-token
```

也可以传会议纪要文档的链接：

```
/minutes https://your-lark-instance.com/docx/your-doc-token
```

Agent 会引导你完成后续步骤。

## 支持的行动类型

| 类型     | Agent 怎么做                               |
| -------- | ------------------------------------------ |
| 发消息   | 起草消息内容，复制到剪贴板让你粘贴发送     |
| 约会议   | 查日历空闲时间，创建日程                   |
| 写文档   | 创建飞书文档                               |
| 查信息   | 搜索网页或飞书文档，整理摘要               |
| 试用产品 | 找到链接和安装方式，发给你                 |
| 创建任务 | 在飞书任务里创建待办，设好负责人和截止时间 |
| 读文档   | 拉取文档，读完给你摘要                     |

## License

MIT
