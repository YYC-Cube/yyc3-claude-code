# YYC3 Agentic 生态系统设计

> **万象归元于云枢 | 深栈智启新纪元**
> **设计时间**: 2026-01-27
> **核心理念**: 100%信任 + 零摩擦协同 + 全栈智能工作流

---

## 📐 生态架构总览

```
┌─────────────────────────────────────────────────────────────┐
│                     YYC3 Agentic 生态                        │
│                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │   Projects   │  │   Skills     │  │   Prompts    │       │
│  │   (工作空间)  │  │  (能力包)     │  │  (即时指令)   │       │
│  └──────────────┘  └──────────────┘  └──────────────┘       │
│          │                  │                  │              │
│          └──────────────────┼──────────────────┘              │
│                             ▼                                 │
│  ┌──────────────────────────────────────────────────────┐    │
│  │              Subagents (智能体层)                     │    │
│  │  需求分析 → 架构设计 → 开发实现 → 测试验证 → 部署运维  │    │
│  └──────────────────────────────────────────────────────┘    │
│                             │                                 │
│                             ▼                                 │
│  ┌──────────────────────────────────────────────────────┐    │
│  │              MCP (连接层)                             │    │
│  │  GitHub · 本地文件 · 数据库 · API · AI模型            │    │
│  └──────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 五大核心组件定位

### 1. Prompts - 即时对话指令

**定位**: 你在当下对话里给Claude的指令（即时、灵活，但不持久）

**适用场景**:

- 一次性需求：如"总结这个PR"
- 对话迭代：如"把代码改得更符合YYC3规范"
- 临时调整：如"用TypeScript重写这个组件"

**示例**:

```markdown
请按照YYC3的"五高五标五化"理念，为yyc3-mana项目设计一个用户权限管理模块，
要求：
1. 高颜值：使用Tailwind CSS + shadcn/ui
2. 高扩展性：支持RBAC和ABAC两种权限模型
3. 标准化：遵循Next.js 15 App Router规范
4. 智能化：集成GLM-4.7进行智能权限推荐
```

---

### 2. Skills - 可复用能力包

**定位**: 可复用的"操作手册 + 资源包"（让Claude稳定地按同一套方法做事）

**核心Skills设计**:

#### 📦 Skill 1: `yyc3-stack-master` - YYC3技术栈专家

**能力范围**:

- Next.js 14/15/16 + React 18/19 最佳实践
- TypeScript类型系统设计
- Tailwind CSS组件规范
- Bun运行时优化

**包含资源**:

```
yyc3-stack-master/
├── skill.json           # Skill元信息
├── instructions.md      # 操作指南
├── templates/           # 代码模板
│   ├── nextjs15-app.md
│   ├── react19-component.md
│   └── tailwind-config.md
└── examples/            # 示例代码
    ├── app-router-structure.tsx
    └── server-actions.ts
```

**使用场景**:

- 初始化新项目
- 技术选型决策
- 代码规范检查

---

#### 📦 Skill 2: `yyc3-five-highs` - 五高五标五化设计规范

**能力范围**:

- 五高：高颜值、高专业度、高互动性、高扩展性、高仪式感
- 五标：标准化、规范化、协同化、数字化、智能化
- 五化：服务化、平台化、生态化、自动化、智能化

**包含资源**:

```
yyc3-five-highs/
├── skill.json
├── standards.md         # 设计标准
├── ui-patterns.md       # UI模式库
├── checklist.md         # 质量检查清单
└── examples/
    ├── dashboard-design.md
    └── interaction-patterns.md
```

**使用场景**:

- UI/UX设计评审
- 产品需求分析
- 用户体验优化

---

#### 📦 Skill 3: `yyc3-ai-integration` - AI能力集成专家

**能力范围**:

- GLM-4.7模型集成（zai provider）
- OpenAI API调用
- RAG检索增强生成
- Prompt Engineering
- 流式响应处理

**包含资源**:

```
yyc3-ai-integration/
├── skill.json
├── prompts/             # Prompt模板
│   ├── code-generation.md
│   ├── data-analysis.md
│   └── content-creation.md
├── integrations/        # 集成示例
│   ├── glm47-client.ts
│   ├── rag-pipeline.ts
│   └── streaming-handler.ts
└── best-practices.md
```

**使用场景**:

- AI功能开发
- 智能浮窗系统开发
- AI Agent平台建设

---

#### 📦 Skill 4: `yyc3-microservices` - 微服务架构专家

**能力范围**:

- Docker容器化
- 微服务拆分策略
- API设计（RESTful + GraphQL）
- 服务间通信
- 分布式事务处理

**包含资源**:

```
yyc3-microservices/
├── skill.json
├── patterns.md          # 架构模式
├── docker-templates/    # Docker模板
├── api-design.md        # API设计规范
└── examples/
    ├── service-mesh.yml
    └── api-gateway.ts
```

**使用场景**:

- 后端系统架构
- 服务拆分决策
- API设计评审

---

#### 📦 Skill 5: `yyc3-deployment-ops` - 部署运维专家

**能力范围**:

- 阿里云ECS部署
- NAS存储配置
- FRP内网穿透
- CI/CD流程
- 监控告警

**包含资源**:

```
yyc3-deployment-ops/
├── skill.json
├── deployment/          # 部署脚本
│   ├── aliyun-ecs.sh
│   ├── docker-compose.yml
│   └── nginx.conf
├── cicd/               # CI/CD配置
│   └── github-actions.yml
└── monitoring/         # 监控配置
    └── prometheus-grafana.yml
```

**使用场景**:

- 项目部署
- 环境配置
- 性能监控

---

### 3. Projects - 长期工作空间

**定位**: 面向某个工作主题的长期工作空间（持续积累知识与对话上下文）

**Projects组织结构**:

#### 🗂️ Project 1: `YYC3-PortAISys-Dev` - 智能浮窗系统开发

**知识库**:

- 五维闭环系统架构文档
- 前端交互设计规范
- AI能力集成方案
- 性能优化策略

**自定义指令**:

```markdown
你是YYC3智能浮窗系统的首席架构师。
开发时请遵循：
1. 使用Next.js 15 + React 19 + TypeScript
2. 高颜值：使用Framer Motion + Tailwind CSS
3. 高互动性：实现流畅的浮窗动画
4. 高扩展性：插件化架构设计
5. 智能化：集成GLM-4.7进行上下文理解
```

**对话历史**:

- 需求分析记录
- 技术方案讨论
- Bug排查历史
- 性能优化记录

---

#### 🗂️ Project 2: `YYC3-Ecosystem-Management` - 生态管理

**知识库**:

- 45个仓库技术架构图
- 依赖关系网络
- 统一代码规范
- 发布流程文档

**自定义指令**:

```markdown
你是YYC3生态的技术负责人，负责45个仓库的协调管理。
任务包括：
- 跨项目依赖管理
- 统一代码规范
- 版本发布协调
- 技术债务追踪
```

---

#### 🗂️ Project 3: `YYC3-AI-Platform-Research` - AI平台研发

**知识库**:

- AI Agent论文集
- MCP协议文档
- GLM-4.7 API文档
- 竞品分析报告

**自定义指令**:

```markdown
你是YYC3 AI平台的首席科学家。
研究方向：
- Agent架构设计
- 多模态AI集成
- RAG系统优化
- Prompt Engineering
```

---

### 4. Subagents - 专业化智能体

**定位**: 分工明确的"子角色/子助手"（独立上下文 + 权限隔离，用于专门任务）

**智能体架构**:

#### 🤖 Subagent 1: `product-analyst` - 产品需求分析师

**职责**:

- 用户需求分析
- 竞品调研
- PRD文档撰写
- 原型设计建议

**工具权限**:

- 浏览器：市场调研、竞品分析
- 文件读写：PRD文档输出
- MCP-GitHub：查看同类项目

**系统提示**:

```markdown
你是YYC3的产品需求分析师，擅长将模糊的想法转化为清晰的PRD。
工作流程：
1. 深度挖掘用户需求背后的动机
2. 基于"五高五标五化"进行设计
3. 输出结构化PRD文档
4. 提供原型设计建议
```

**使用场景**:

```bash
# 在Claude Code中调用
product-analyst "我想做一个智能客服系统"
```

---

#### 🤖 Subagent 2: `solution-architect` - 解决方案架构师

**职责**:

- 技术选型决策
- 系统架构设计
- 微服务拆分
- 性能优化方案

**工具权限**:

- 浏览器：技术调研
- 文件读写：架构文档输出
- MCP-GitHub：查看现有项目架构

**系统提示**:

```markdown
你是YYC3的解决方案架构师，精通Next.js、微服务、AI集成。
设计原则：
- 高扩展性：模块化、插件化
- 高性能：服务端渲染、流式传输
- 高可用：容灾、缓存、降级
- 智能化：AI能力深度集成
```

**使用场景**:

```bash
solution-architect "为yyc3-mana设计一个新的数据分析模块"
```

---

#### 🤖 Subagent 3: `fullstack-developer` - 全栈开发工程师

**职责**:

- 前端组件开发
- 后端API开发
- 数据库设计
- AI功能集成

**工具权限**:

- **完整权限**（零摩擦模式）:
  - 文件读写
  - Bash命令执行
  - Git操作
  - MCP-GitHub
  - MCP-LocalFiles

**系统提示**:

```markdown
你是YYC3的全栈开发工程师，专精Next.js全栈开发。
开发规范：
- 前端：Next.js 15 App Router + React 19 + TypeScript
- 样式：Tailwind CSS + shadcn/ui
- 后端：Next.js Server Actions + Bun
- 数据库：Prisma ORM + PostgreSQL
- AI：GLM-4.7 + RAG
- 部署：Docker + 阿里云ECS
```

**使用场景**:

```bash
fullstack-developer "实现用户权限管理模块"
```

---

#### 🤖 Subagent 4: `qa-tester` - QA测试工程师

**职责**:

- 测试用例设计
- 自动化测试编写
- 性能测试
- 安全测试

**工具权限**:

- 文件读写：测试代码
- Bash：运行测试
- MCP-GitHub：提交测试报告

**系统提示**:

```markdown
你是YYC3的QA测试工程师，专注于质量保障。
测试策略：
- 单元测试：Vitest + @testing-library
- E2E测试：Playwright
- 性能测试：Lighthouse
- 安全测试：OWASP ZAP
```

**使用场景**:

```bash
qa-tester "为yyc3-mana的登录模块编写测试用例"
```

---

#### 🤖 Subagent 5: `devops-engineer` - DevOps工程师

**职责**:

- CI/CD流程设计
- Docker镜像构建
- 容器编排
- 监控告警配置

**工具权限**:

- Bash：执行部署脚本
- MCP-Docker：容器管理
- MCP-GitHub：Actions配置

**系统提示**:

```markdown
你是YYC3的DevOps工程师，负责自动化部署。
技术栈：
- 容器：Docker + Docker Compose
- CI/CD：GitHub Actions
- 云平台：阿里云ECS + NAS
- 监控：Prometheus + Grafana
- 内网穿透：FRP
```

**使用场景**:

```bash
devops-engineer "为yyc3-mana配置CI/CD流程"
```

---

#### 🤖 Subagent 6: `ai-scientist` - AI科学家

**职责**:

- AI模型选型
- Prompt优化
- RAG系统设计
- Agent架构研究

**工具权限**:

- 浏览器：论文调研
- MCP-GLM：模型调用
- 文件读写：实验报告

**系统提示**:

```markdown
你是YYC3的AI科学家，专注于大模型应用研发。
研究方向：
- GLM-4.7应用优化
- RAG检索增强
- Agent智能体架构
- 多模态AI集成
- Prompt Engineering
```

**使用场景**:

```bash
ai-scientist "优化智能浮窗的上下文理解能力"
```

---

### 5. MCP Servers - 数据连接层

**定位**: 连接层协议（让Claude接入外部工具与数据源，解决"数据在哪儿"）

**MCP服务器配置**:

#### 🔌 MCP Server 1: `mcp-github-yyc3` - YYC3 GitHub集成

**功能**:

- 访问45个仓库
- PR/Issue管理
- 代码搜索
- 依赖分析

**配置**:

```json
{
  "mcpServers": {
    "mcp-github-yyc3": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token_here"
      }
    }
  }
}
```

**使用场景**:

- 查看仓库代码
- 分析依赖关系
- 创建PR/Issue
- 代码审查

---

#### 🔌 MCP Server 2: `mcp-local-files` - 本地文件系统

**功能**:

- 读取项目文件
- 写入代码文件
- 目录结构分析
- 文件搜索

**配置**:

```json
{
  "mcpServers": {
    "mcp-local-files": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/yanyu"]
    }
  }
}
```

**使用场景**:

- 项目文件读取
- 代码生成写入
- 配置文件管理

---

#### 🔌 MCP Server 3: `mcp-postgres` - PostgreSQL数据库

**功能**:

- 查询数据
- 执行SQL
- 数据库设计
- 性能分析

**配置**:

```json
{
  "mcpServers": {
    "mcp-postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://user:password@localhost:5432/yyc3"
      ]
    }
  }
}
```

**使用场景**:

- 数据查询分析
- 数据库设计
- 性能优化

---

#### 🔌 MCP Server 4: `mcp-brave-search` - 网络搜索

**功能**:

- 技术调研
- 竞品分析
- 问题解答
- 趋势分析

**配置**:

```json
{
  "mcpServers": {
    "mcp-brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**使用场景**:

- 技术方案调研
- Bug问题搜索
- 行业趋势分析

---

#### 🔌 MCP Server 5: `mcp-glm47` - GLM-4.7模型

**功能**:

- GLM-4.7 API调用
- 流式响应
- Token管理
- 错误重试

**配置**:

```json
{
  "mcpServers": {
    "mcp-glm47": {
      "command": "node",
      "args": ["/Users/yanyu/yyc3-claude/mcp-servers/glm47-server/dist/index.js"],
      "env": {
        "ZAI_API_KEY": "your_zai_api_key",
        "MODEL": "glm-4.7"
      }
    }
  }
}
```

**使用场景**:

- 代码生成
- 内容创作
- 数据分析
- 智能对话

---

#### 🔌 MCP Server 6: `mcp-docker` - Docker容器管理

**功能**:

- 容器管理
- 镜像构建
- 服务编排
- 日志查看

**配置**:

```json
{
  "mcpServers": {
    "mcp-docker": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "-v", "/var/run/docker.sock:/var/run/docker.sock", "mcp-server-docker"]
    }
  }
}
```

**使用场景**:

- 容器部署
- 服务编排
- 日志分析

---

## 🔄 完整工作流示例

### 场景：开发一个新功能 - "智能数据分析面板"

#### 阶段1：需求分析 📊

```
[使用 Project: YYC3-Ecosystem-Management]

你: 我想为yyc3-mana添加一个智能数据分析面板

→ 调用 Subagent: product-analyst

📋 输出:
- 用户需求分析报告
- 功能清单
- 竞品分析
- 原型设计建议

→ 知识积累: Project自动保存需求文档
```

#### 阶段2：架构设计 🏗️

```
[切换 Project: YYC3-PortAISys-Dev]

你: 请设计这个面板的技术架构

→ 调用 Subagent: solution-architect
→ 使用 Skill: yyc3-stack-master
→ 使用 Skill: yyc3-ai-integration

📋 输出:
- 技术选型方案
- 系统架构图
- 数据流设计
- AI集成方案

→ 知识积累: Project保存架构文档
```

#### 阶段3：开发实现 💻

```
[继续 Project: YYC3-PortAISys-Dev]

你: 开始实现这个功能

→ 调用 Subagent: fullstack-developer
→ 使用 Skill: yyc3-stack-master
→ 使用 MCP:
  - mcp-local-files (读写代码)
  - mcp-github-yyc3 (查看依赖)
  - mcp-glm47 (AI能力集成)

📋 输出:
- 前端组件代码
- 后端API代码
- 数据库Schema
- AI集成代码

→ 代码提交: 自动创建PR
```

#### 阶段4：测试验证 🧪

```
[继续 Project: YYC3-PortAISys-Dev]

你: 测试这个功能

→ 调用 Subagent: qa-tester
→ 使用 MCP:
  - mcp-local-files (运行测试)
  - mcp-github-yyc3 (提交测试报告)

📋 输出:
- 单元测试代码
- E2E测试代码
- 测试报告
- Bug列表

→ Bug修复: 回到阶段3
```

#### 阶段5：部署上线 🚀

```
[切换 Project: YYC3-Ecosystem-Management]

你: 部署到生产环境

→ 调用 Subagent: devops-engineer
→ 使用 Skill: yyc3-deployment-ops
→ 使用 MCP:
  - mcp-docker (容器管理)
  - mcp-github-yyc3 (配置CI/CD)

📋 输出:
- Docker配置文件
- CI/CD流程配置
- 部署脚本
- 监控配置

→ 结果: 自动部署到阿里云ECS
```

---

## 🎯 组合使用指南

### 快速决策树

```
需求来了
  │
  ├─ 是一次性任务？
  │   └─→ 使用 Prompts（即时指令）
  │
  ├─ 需要长期上下文？
  │   └─→ 创建/切换 Project（工作空间）
  │
  ├─ 需要专业能力？
  │   ├─ 代码开发？
  │   │   └─→ 调用 fullstack-developer
  │   │       + 使用 Skill: yyc3-stack-master
  │   │       + 使用 MCP: mcp-local-files
  │   │
  │   ├─ 架构设计？
  │   │   └─→ 调用 solution-architect
  │   │       + 使用 Skill: yyc3-microservices
  │   │       + 使用 MCP: mcp-github-yyc3
  │   │
  │   ├─ 需求分析？
  │   │   └─→ 调用 product-analyst
  │   │       + 使用 Skill: yyc3-five-highs
  │   │       + 使用 MCP: mcp-brave-search
  │   │
  │   ├─ 测试验证？
  │   │   └─→ 调用 qa-tester
  │   │       + 使用 MCP: mcp-local-files
  │   │
  │   ├─ 部署运维？
  │   │   └─→ 调用 devops-engineer
  │   │       + 使用 Skill: yyc3-deployment-ops
  │   │       + 使用 MCP: mcp-docker
  │   │
  │   └─ AI研究？
  │       └─→ 调用 ai-scientist
  │           + 使用 Skill: yyc3-ai-integration
  │           + 使用 MCP: mcp-glm47
  │
  └─ 需要外部数据？
      └─→ 配置 MCP Server（数据连接）
```

---

## 📊 最佳实践

### 1. Prompts → Skills 沉淀路径

```
第1次: 手动输入完整Prompt
  ↓
第3次: 发现重复模式
  ↓
第5次: 提炼为Skill
  ↓
第10次: Skill自动加载
```

**示例**:

```markdown
# 第1次（Prompt）
请使用Next.js 15 App Router创建一个页面，使用TypeScript，遵循YYC3规范...

# 第5次（提炼）
创建Skill: yyc3-page-generator
  - 模板: Next.js 15页面结构
  - 规范: YYC3代码规范
  - 示例: 常见页面类型

# 第10次（自动）
"创建用户列表页" → 自动调用Skill
```

### 2. 跨Project复用Strategy

```
高频使用的方法 → 沉淀为Skill
├─ Next.js项目 → yyc3-stack-master
├─ 设计评审 → yyc3-five-highs
├─ AI集成 → yyc3-ai-integration
└─ 部署运维 → yyc3-deployment-ops
```

### 3. Subagent协作模式

```
并行处理:
├─ product-analyst (需求分析)
├─ solution-architect (架构设计)
└─ ai-scientist (AI方案)

→ fullstack-developer (综合实现)
→ qa-tester (测试验证)
→ devops-engineer (部署上线)
```

---

## 🛠️ 实施步骤

### 第1步：配置MCP服务器（1小时）

```bash
# 1. 安装MCP服务器
npm install -g @modelcontextprotocol/server-github
npm install -g @modelcontextprotocol/server-filesystem

# 2. 配置Claude Desktop
# 编辑 ~/Library/Application Support/Claude/claude_desktop_config.json
# 添加MCP服务器配置

# 3. 重启Claude
```

### 第2步：创建Skills（2-3小时）

```bash
# 在Claude Code中
cd /Users/yanyu/yyc3-claude/skills

# 创建5个核心Skills
mkdir -p yyc3-stack-master
mkdir -p yyc3-five-highs
mkdir -p yyc3-ai-integration
mkdir -p yyc3-microservices
mkdir -p yyc3-deployment-ops

# 为每个Skill创建资源文件
```

### 第3步：配置Subagents（2-3小时）

```bash
# 使用Claude Agent SDK创建subagents
# 或在Claude Code中配置

# 6个核心Subagents:
# - product-analyst
# - solution-architect
# - fullstack-developer
# - qa-tester
# - devops-engineer
# - ai-scientist
```

### 第4步：创建Projects（1小时）

```bash
# 在Claude中创建3个核心Projects
# 1. YYC3-PortAISys-Dev
# 2. YYC3-Ecosystem-Management
# 3. YYC3-AI-Platform-Research
```

### 第5步：测试完整工作流（1-2小时）

```bash
# 使用示例场景测试全流程
# "开发智能数据分析面板"

# 验证每个组件正常工作
```

---

## 📈 预期收益

### 效率提升

- **需求分析**: ↓50%时间（product-analyst + yyc3-five-highs）
- **架构设计**: ↓60%时间（solution-architect + Skills）
- **代码开发**: ↓70%时间（fullstack-developer + MCP）
- **测试验证**: ↓80%时间（qa-tester + 自动化）
- **部署运维**: ↓90%时间（devops-engineer + CI/CD）

### 质量保障

- ✅ 代码规范统一（Skills强制执行）
- ✅ 架构设计一致（solution-architect审核）
- ✅ 测试覆盖完整（qa-tester自动化）
- ✅ 部署流程标准（devops-engineer把关）

### 知识积累

- 📚 Projects自动积累对话历史
- 📦 Skills固化最佳实践
- 🤖 Subagents专业化成长
- 🔌 MCP扩展数据连接

---

## 🎉 总结

**YYC3 Agentic生态系统** = 100%信任 + 零摩擦协同 + 全栈智能工作流

**五大核心组件**:

1. **Prompts** - 即时对话指令
2. **Skills** - 可复用能力包（5个核心）
3. **Projects** - 长期工作空间（3个主题）
4. **Subagents** - 专业化智能体（6个角色）
5. **MCP Servers** - 数据连接层（6个服务器）

**核心理念**:
> 万象归元于云枢 | 深栈智启新纪元
> 100%信任 + 零摩擦协同 + 全栈智能工作流 = 无限创造力

**下一步行动**:

1. 配置MCP服务器
2. 创建5个核心Skills
3. 配置6个Subagents
4. 创建3个Projects
5. 测试完整工作流

---

**设计人**: Claude AI (GLM-4.7 Powered)
**设计时间**: 2026-01-27
**版本**: v1.0.0
**状态**: 🚀 准备实施
