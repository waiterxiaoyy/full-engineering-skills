# Full Engineering Skills

**全流程工程实践工具箱：把目标说清，把判断留下，把实现做实。**

7 个可按需组合的 AI 编程助手 Skills，覆盖需求澄清、方案决策、行为规格、全栈实现、持续交付、问题排查和任务交接。每个 Skill 都是一份可阅读、可修改的工作约定；小改动不必走完整套流程。

## 选择 Skill

| 遇到的问题 | Skill | 主要产物 |
|---|---|---|
| 目标存在，但范围和规则尚不明确 | [requirements-grilling](skills/requirements-grilling/SKILL.md) | 已确认需求、反例和待决问题 |
| 需要保存术语、约束和方案取舍 | [domain-decisions](skills/domain-decisions/SKILL.md) | CONTEXT 和 ADR |
| 需要明确什么行为才算完成 | [behavior-spec](skills/behavior-spec/SKILL.md) | 行为规格、验收矩阵和切片依赖 |
| 需要贯通前后端并尽早得到反馈 | [vertical-slice-build](skills/vertical-slice-build/SKILL.md) | 最小完整路径、测试和交付证据 |
| 任务明确，希望在授权范围内持续推进 | [afk-delivery](skills/afk-delivery/SKILL.md) | 执行验证循环、退出条件和交付结果 |
| 问题难定位，需要确认修复有效 | [evidence-debugging](skills/evidence-debugging/SKILL.md) | 复现、根因和回归证据 |
| 会话变长或需要跨会话继续工作 | [context-handoff](skills/context-handoff/SKILL.md) | 当前状态、未决事项和下一步 |

## 安装

需要 Git、Node.js 和 npm/npx。在目标项目目录运行：

```bash
npx skills add https://github.com/waiterxiaoyy/full-engineering-skills.git --list
npx skills add https://github.com/waiterxiaoyy/full-engineering-skills.git --agent codebuddy --skill '*' -y
```

按需替换 `--agent` 的目标，例如 `codex`、`cursor` 或 `claude-code`；具体名称以安装器当前帮助为准。安装器能够识别客户端，不等于所有客户端中的执行效果均已验证。

只安装一个 Skill：

```bash
npx skills add https://github.com/waiterxiaoyy/full-engineering-skills.git --agent codex --skill requirements-grilling -y
```

支持插件系统的 CodeBuddy Code CLI 也可整套安装：

```bash
codebuddy plugin marketplace add https://github.com/waiterxiaoyy/full-engineering-skills.git
codebuddy plugin install full-engineering-skills@full-engineering-skills
```

手动安装时，将 `skills/` 下需要的文件夹复制到目标助手的 Skills 目录，并保留其中的 `references/`。项目已有同名 Skill 时先比较内容，保留定制。

## 用法

```text
读取当前项目说明，使用 requirements-grilling 对齐本次需求。
先查已有资料和代码，需要我判断的问题分批提出，保存已确认要求与待决问题。
```

```text
按已确认规格，使用 afk-delivery 和 vertical-slice-build 完成当前依赖满足的切片。
复用已有能力，在关键边界先运行失败测试，再实现并复验。
交付对应验收结果、证据位置和剩余事项。
```

```text
使用 evidence-debugging 排查问题：先建立能捕获症状的检查，再定位和修复。
修复后重跑原场景，保存回归证据。
```

## 模板

- [项目说明](templates/BRIEF.md)
- [开发与验收台账](templates/S-LEDGER.md)
- [任务交接](templates/HANDOFF.md)

模板按需复制到项目，安装 Skill 不会自动将模板写入业务目录。

## 使用边界

Skills 提供工作指导，不替代业务判断或实际验证。它们不附带浏览器、数据库或部署工具，也不扩大用户授权。访问入口、环境和权限由目标项目提供；不要把业务数据、账号或凭据写入 Skill。

`afk-delivery` 管持续执行的边界和退出条件，`vertical-slice-build` 管跨层改动的实现与验证；可以组合使用。项目已有等价文档时继续沿用，避免为流程重复维护材料。
