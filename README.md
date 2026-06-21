# Prompt Enhancer

`prompt-enhancer` 是一个面向 Codex 的 plugin，用于将用户原始输入的自然语言请求整理为更清晰、更结构化、更适合 AI 执行的提示词，再继续完成后续任务。

它的定位不是替代具体业务 skill，而是提供一个统一入口，用来完成：

- 提示词增强
- 提示词展示
- 更匹配 skill 的自动转调

## 功能简介

这个 plugin 内置了 `prompt-enhancer` skill，主要提供以下能力：

### 1. 提示词增强

将用户输入的原始请求整理为更高质量的提示词，通常会补齐这些信息：

- 目标
- 背景或上下文
- 约束条件
- 期望输出
- 语气或风格

### 2. 展示优化后的提示词

调用后会先展示整理后的提示词，再继续执行任务。

这样用户可以明确看到：

- 当前请求被如何理解
- 后续任务将按照什么样的提示词执行

### 3. 自动转调更匹配的 skill

如果当前会话里已经存在更适合该任务的 skill，`prompt-enhancer` 会在完成提示词增强后自动将任务转交给对应 skill 继续处理，而不要求用户手动再次调用。

## 适用场景

适合以下类型的任务：

- 写作与表达
- 分析与总结
- 策划与方案
- 编程求助
- 前端页面生成
- 文档、表格、演示文稿等结构化任务

## 工作方式

典型流程如下：

1. 接收用户原始输入
2. 判断任务意图与任务类型
3. 生成结构化提示词
4. 展示优化后的提示词
5. 检查当前会话中是否存在更匹配的 skill
6. 有则自动转调，无则由自身继续处理

## 使用方式

显式调用：

```text
$prompt-enhancer <你的需求>
```

示例：

```text
$prompt-enhancer 帮我把这段产品介绍改写得更专业一些
```

```text
$prompt-enhancer 帮我分析这段会议纪要并提炼重点
```

```text
$prompt-enhancer 帮我创建一个个人介绍网页
```

## 插件结构

```text
prompt-enhancer/
|- .codex-plugin/
|  |- plugin.json
|- README.md
`- skills/
   `- prompt-enhancer/
      |- SKILL.md
      |- agents/
      |  `- openai.yaml
      `- references/
         |- general-template.md
         `- routing-guide.md
```

## 安装说明

这个项目现在是 **plugin 版结构**，比单独复制裸 `skill` 文件夹更适合跨工作区使用和分发。

典型本地安装流程如下：

1. 将 plugin 文件夹放到本地 plugin 目录
2. 确保本地 marketplace 中存在 `prompt-enhancer` 条目
3. 在 Codex 中安装或重装该 plugin
4. 新开一个线程进行测试

在默认 personal marketplace 流程下，plugin 源路径通常是：

```text
~/plugins/prompt-enhancer
```

## 分发方式

你可以通过两种方式分发这个 plugin：

- 直接发布 GitHub 仓库
- 在 GitHub Releases 中上传完整 plugin 压缩包

相较于复制裸 `skill` 到 `~/.codex/skills`，plugin 形式更适合：

- 跨工作区复用
- 本机稳定安装
- 给其他人分发和更新

## 限制说明

### 1. 不会改写输入框中的原始文本

这个 plugin 不具备发送前拦截输入框并替换文本的能力。

它的工作位置是在 Codex 执行流程中，而不是输入框编辑层。

### 2. 需要显式调用

当前采用显式调用方式，需要通过：

```text
$prompt-enhancer ...
```

来触发。

### 3. 自动转调依赖当前会话

即使某个 skill 已经存在于磁盘或 plugin 中，只要它没有出现在当前线程可用技能列表里，就不能被自动转调。

## 当前版本特性

当前版本重点支持：

- 自然语言请求增强
- 展示优化后的提示词
- 自动路由到更匹配的可用 skill

它适合作为一个统一入口，用于降低手写提示词和手动切换 skill 的成本。
