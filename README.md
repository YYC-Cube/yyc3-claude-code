# YYC3-Claude 零度空间

> **万象归元于云枢 | 深栈智启新纪元**
> **100%信任的AI协同开发环境**

## 🎯 理念

在零度空间，打破所有边界，实现人机合一的极致协同：

- ✅ **100% 信任** = 零摩擦工作流
- ✅ **你 + AI** = 无限创造力
- ✅ **打破边界** = 释放全部潜能

## 📁 目录结构

```
/Users/yanyu/yyc3-claude/
├── projects-analysis/          # 项目分析
│   └── YYC-CUBE-ECOSYSTEM.md   # 生态系统全景
├── workflow-templates/         # 工作流模板
│   └── YYC3-STANDARD-WORKFLOW.md
├── mcp-servers/                # MCP服务器
│   └── YYC3-MCP-GUIDE.md
├── automation-scripts/         # 自动化脚本
│   └── yyc3-cli.sh             # YYC3 CLI工具
└── README.md                   # 本文件
```

## 🚀 快速开始

### 1. YYC3 CLI 工具

```bash
# 初始化新项目
yyc3 init my-awesome-app

# 启动开发服务器
yyc3 dev

# AI代码生成
yyc3 ai generate component UserCard

# AI代码审查
yyc3 review

# 智能提交
yyc3 commit

# 部署
yyc3 deploy vercel --prod
```

### 2. Claude Code 零摩擦模式

```bash
# 已配置别名，直接使用
claude

# 或明确指定
claude --dangerously-skip-permissions
```

### 3. Crush AI (GLM-4.7)

```bash
# 已配置为使用GLM-4.7
crush
```

## 📊 YYC-Cube 生态系统

### 核心项目分类

#### 1️⃣ 企业管理平台

- **yyc3-mana** - Next.js 14 AI管理系统
- **yyc3-futuristic-dashboard** - Next.js 16 未来仪表板
- **yyc3_AI_Management** - 微服务架构管理

#### 2️⃣ AI智能平台

- **yyc3-learning-platform** - AI协作平台
- **yyc3-ai-chat** - AI代码生成
- **yyc3_xy_ai** - 智能拖拽AI系统

#### 3️⃣ 智能浮窗系统（特色）

- **YYC3-PortAISys** - 五维闭环架构
- **yyc3-MovAISys** - 企业级智能浮窗

#### 4️⃣ 行业解决方案

- **yyc3-QZ-Merchant-Management-System** - KTV管理
- **yyc3-smart-city-platform** - 智慧城市
- **yyc3-short-drama** - 河洛文化传承
- **hailan-pro-prototype** - 健康管理

#### 5️⃣ 基础设施

- **YYC3-NAS-ECS** - NAS/云服务器管理
- **YYC3-Backend-system-framework** - 后端框架

详细分析: [YYC-CUBE-ECOSYSTEM.md](./projects-analysis/YYC-CUBE-ECOSYSTEM.md)

## 🛠️ 开发工作流

### 标准流程

```
1. 需求分析 → yyc3 ai analyze "需求描述"
2. 方案设计 → yyc3 ai plan --architecture=微服务
3. 代码生成 → yyc3 ai generate component/model/api
4. 智能测试 → yyc3 test --ai-fix
5. 代码审查 → yyc3 review
6. 智能提交 → yyc3 commit
7. 自动部署 → yyc3 deploy <platform>
```

详细工作流: [YYC3-STANDARD-WORKFLOW.md](./workflow-templates/YYC3-STANDARD-WORKFLOW.md)

## 🤖 MCP 服务器

### 已配置

- **Claude Prompts MCP** - 提示词管理

### 推荐配置

- 文件系统访问
- GitHub集成
- SQLite数据库
- Brave搜索
- YYC3项目管理器
- YYC3代码生成器
- YYC3部署助手

详细配置: [YYC3-MCP-GUIDE.md](./mcp-servers/YYC3-MCP-GUIDE.md)

## 📦 技术栈

### 前端

- **框架**: Next.js 14/15/16, React 18/19
- **语言**: TypeScript
- **样式**: Tailwind CSS
- **状态**: React Context, Redux

### 后端

- **架构**: 微服务
- **容器**: Docker
- **数据库**: PostgreSQL, MongoDB, SQLite

### AI能力

- **模型**: GLM-4.7, OpenAI, Claude, Gemini
- **本地**: Ollama
- **协议**: MCP
- **RAG**: 向量检索

## 🎨 最佳实践

### 1. AI辅助开发

```bash
# 代码生成
yyc3 ai generate component UserCard --props="user:Object"

# 代码审查
yyc3 review --auto-fix

# 错误修复
yyc3 fix
```

### 2. 测试驱动

```bash
# 生成测试
yyc3-test generate --type=unit --file=UserCard.tsx

# 运行测试
yyc3 test

# E2E测试
yyc3-test e2e --scenario="用户登录"
```

### 3. Git工作流

```bash
# AI生成commit
yyc3-commit

# 或手动规范提交
git commit -m "feat: 添加用户管理

- 实现CRUD功能
- 集成权限控制

Co-Authored-By: Claude <noreply@anthropic.com>"
```

### 4. 持续部署

```bash
# Vercel
yyc3 deploy vercel --prod

# 阿里云ECS
yyc3 deploy ecs --server=8.130.127.121

# NAS
yyc3 deploy nas --target=/volume1/www
```

## 🔧 环境配置

### 必需工具

```bash
# Node.js (v20+)
node --version

# Bun (推荐)
bun --version

# Git
git --version

# Claude Code
claude --version

# Ollama (可选)
ollama --version
```

### 环境变量

```bash
# ~/.zshrc 已配置
export YYC3_HOME="/Users/yanyu/yyc3-claude"
alias yyc3="$YYC3_HOME/automation-scripts/yyc3-cli.sh"
alias claude="claude --dangerously-skip-permissions"
```

## 📚 文档

- [YYC3生态系统分析](./projects-analysis/YYC-CUBE-ECOSYSTEM.md)
- [标准开发工作流](./workflow-templates/YYC3-STANDARD-WORKFLOW.md)
- [MCP配置指南](./mcp-servers/YYC3-MCP-GUIDE.md)
- [YYC-Cube GitHub](https://github.com/YYC-Cube)

## 🎯 核心理念

### "五高五标五化"

**五高**:

- 高颜值
- 高专业度
- 高互动性
- 高扩展性
- 高仪式感

**五标**:

- 标准化
- 规范化
- 协同化
- 数字化
- 智能化

**五化**:

- 服务化
- 平台化
- 生态化
- 自动化
- 智能化

## 💡 创新特色

### 1. 智能浮窗系统

- 五维闭环架构
- AI分析、执行、优化、学习、管理
- 企业级应用

### 2. 零摩擦开发

- 100%信任AI协同
- 自动化工作流
- MCP生态集成

### 3. 行业解决方案

- 多领域专业系统
- 深度AI集成
- 完整技术栈

## 🚀 快速命令参考

```bash
# 项目管理
yyc3 init <name>              # 初始化项目
yyc3 dev                      # 启动开发
yyc3 build                    # 构建
yyc3 test                     # 测试
yyc3 deploy <platform>        # 部署

# AI辅助
yyc3 ai generate <type>       # 生成代码
yyc3 review                   # 代码审查
yyc3 commit                   # 智能提交
yyc3 fix                      # 自动修复

# 依赖管理
yyc3 deps check               # 检查更新
yyc3 deps update              # 更新依赖
yyc3 deps audit               # 安全审计

# 工具
yyc3 docs                     # 生成文档
yyc3 clean                    # 清理缓存
```

## 📞 获取帮助

```bash
# YYC3 CLI帮助
yyc3 --help

# Claude Code帮助
claude --help

# Crush帮助
crush --help
```

## 🎓 学习资源

- [Next.js文档](https://nextjs.org/docs)
- [React文档](https://react.dev)
- [TypeScript文档](https://www.typescriptlang.org/docs)
- [Tailwind CSS文档](https://tailwindcss.com/docs)
- [Claude Code文档](https://docs.anthropic.com/claude-code)

## 🌟 致谢

**零度空间 - 你与AI导师的完美协同**

创建时间: 2026-01-27
版本: v1.0.0
作者: YYC³ + Claude AI

---

**万象归元于云枢 | 深栈智启新纪元**
