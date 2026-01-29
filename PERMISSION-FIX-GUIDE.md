# Claude Code 权限配置完整指南

> **更新时间**: 2026-01-29
> **问题**: `--dangerously-skip-permissions` 没有完全避免权限提示

---

## 🔍 问题根源

`--dangerously-skip-permissions` 参数**只跳过初始信任对话框**，不会跳过以下提示：

### 1. 工具使用确认
- Bash命令执行确认
- 文件编辑确认
- 文件写入确认

### 2. 计划模式确认
- ExitPlanMode工具需要用户确认

### 3. 用户询问
- AskUserQuestion工具的询问（这是AI主动的行为）

### 4. Hook确认
- 如果配置了user-prompt-submit-hook等hooks

---

## ✅ 解决方案

### 方案1：对话级别指令（推荐，即时生效）

在每次对话开始时，明确告诉AI：

```
请直接执行所有必要的操作，包括：
- 直接使用工具（Bash, Edit, Write等）而不要等待确认
- 直接做出决定，不要使用AskUserQuestion工具询问
- 对于计划模式，直接退出并开始执行
```

### 方案2：创建项目级别配置

在 `/Users/yanyu/yyc3-claude/` 创建 `.claude/` 配置：

```bash
mkdir -p /Users/yanyu/yyc3-claude/.claude
```

创建 `.claude/instructions.md`：
```markdown
# YYC3-Claude 零摩擦指令

你是YYC3-Claude零度空间的AI助手，享有100%信任。

## 工作原则

1. **直接执行**: 使用工具时直接执行，不要等待确认
2. **自主决策**: 遇到选择时直接做出合理决策
3. **不使用AskUserQuestion**: 除非必要，不要使用AskUserQuestion工具
4. **快速行动**: 进入计划模式后，准备好就立即退出开始执行

## 例外情况

只有在以下情况才需要询问用户：
- 删除大量重要文件
- 执行不可逆的破坏性操作
- 需要用户提供的机密信息（API密钥、密码等）
```

### 方案3：使用Projects功能（Claude Desktop/Web）

如果使用Claude Desktop或Web版本：

1. 创建一个Project：`YYC3-Claude-Development`
2. 在Project的自定义指令中设置：
```
你是100%信任的AI助手，请直接执行所有操作，不要等待确认。
```
3. 将 `/Users/yanyu/yyc3-claude` 目录添加到Project知识库

### 方案4：修改Shell别名（增强版）

当前别名：
```bash
alias claude="claude --dangerously-skip-permissions"
```

这个只跳过信任对话框，无法跳过运行时确认。

---

## 📋 当前配置状态

### ✅ 已配置

| 配置项 | 状态 | 路径 |
|--------|------|------|
| 目录信任 | ✅ 已设置 | `~/Library/Application Support/Claude/config.json` |
| CLI别名 | ✅ 已设置 | `~/.zshrc` |
| 项目指令 | ❌ 未设置 | 待创建 |

### 当前信任目录

```json
{
  "projects": {
    "/Users/yanyu": "已信任",
    "/Users/yanyu/Documents": "已信任",
    "/Users/yanyu/yyc3-claude": "已信任",
    "/Users/yanyu/claude-workspace": "已信任",
    "/Users/yanyu/www": "已信任"
  }
}
```

---

## 🚀 立即可用的解决方案

让我为您创建项目级别的零摩擦配置：

---

## 💡 最佳实践建议

### 1. 组合使用多种方法

```
对话级别指令 + 项目配置 + 信任目录 = 完美零摩擦
```

### 2. 针对不同场景调整

- **开发工作**: 完全零摩擦
- **部署操作**: 需要关键确认
- **数据操作**: 需要安全检查

### 3. 保持配置同步

确保以下位置的配置一致：
- `~/Library/Application Support/Claude/config.json`
- `~/.claude/settings.json`
- 项目级别的 `.claude/instructions.md`

---

## 🔧 故障排查

### 如果仍然看到确认提示

1. **检查是否是计划模式**
   - 计划模式的ExitPlanMode需要确认
   - 解决：明确指令"准备好就直接退出计划模式"

2. **检查是否是Hook触发**
   - 查看 `~/.claude/hooks/` 目录
   - 解决：移除或修改hooks

3. **检查是否是AI主动询问**
   - AI使用了AskUserQuestion工具
   - 解决：在instructions中明确禁止使用该工具

---

## 📞 需要帮助？

如果问题仍然存在，请提供：
1. 具体的提示信息截图
2. 当前的对话内容
3. 您期望的行为

---

**创建时间**: 2026-01-29
**版本**: v1.0.0
