# Gorvey Claude Plugin

基于Claude的前端开发工作流插件，提供智能化的前端开发辅助功能。

## 项目简介

这是一个专为前端开发设计的Claude插件，集成了多个实用工具和命令，帮助开发者提高开发效率，实现规范化的前端开发流程。

## 功能特性

- 🔧 **分布式文档系统**：为项目各目录生成专门的CLAUDE.md文档
- 📋 **智能规划系统**：基于用户需求生成详细的开发计划
- 🛠️ **自动化实现**：按照规划自动完成开发任务
- 🌐 **API代码生成**：基于YApi接口文档自动生成API代码
- 📦 **Sub Agent支持**：模块化的代理系统处理不同任务

## 插件组件

### 1. Sub Agent - fe-init-agent
负责为项目的特定目录生成专门的CLAUDE.md文档，实现模块化的知识管理。

**功能**：
- 深入分析目录结构和代码实现
- 识别设计模式和最佳实践
- 提取典型的使用模式
- 生成结构化的开发指南

### 2. 命令系统

#### `/gorvey-plugins:fe-init-vue3` - 初始化分布式文档系统
为项目的每个关键目录创建专门的CLAUDE.md文档，包括：
- `src/api/` - API接口开发指南
- `src/components/` - 全局组件库文档
- `src/views/` - 页面开发指南
- `src/stores/` - 状态管理指南
- `src/utils/` - 工具函数库说明
- `src/hooks/` - 组合式API指南
- `src/styles/` - 样式处理方案
- `src/routers/` - 路由配置指南
- `src/layouts/` - 布局组件指南

#### `/gorvey-plugins:plan` - 创建开发计划
根据用户需求生成详细的开发提案和任务列表。

**工作流程**：
1. 收集用户需求和功能规格
2. 生成`spec/plan/<change-id>/prd.md`产品需求文档
3. 创建`spec/plan/<change-id>/tasks.md`任务清单
4. 整合项目规范和最佳实践

**PRD模板包含**：
- 用户需求分析
- 关联页面文件
- 页面布局线框图
- 可用接口列表
- 需要使用的组件
- 注意事项

#### `/gorvey-plugins:apply` - 执行开发任务
按照生成的计划自动完成开发工作。

**执行流程**：
1. 读取PRD和任务清单确认范围
2. 按需加载相关规范文档
3. 按顺序完成各个任务
4. 实时更新任务完成状态
5. 确保所有验收标准达标

#### `/gorvey-plugins:gen-api-code` - API代码生成
基于YApi接口文档自动生成API代码。

**参数**：
- `yapi-url`：YApi接口文档地址
- `api-path`：接口文件存放位置
- `type-path`：TypeScript类型文件存放位置（TS项目）

**特性**：
- 支持JavaScript和TypeScript项目
- 遵循项目API规范
- 自动处理接口类型定义

## 项目结构

```
gorvey-claude-plugin/
├── .claude-plugin/                 # Claude插件配置
│   └── marketplace.json           # 插件市场配置
├── my-plugin/                     # 插件核心功能
│   ├── agents/                    # Sub Agent
│   │   └── fe-init-agent.md      # 文档生成代理
│   └── commands/                  # 命令定义
│       ├── fe-init-vue3.md       # 初始化文档系统
│       ├── plan.md                # 创建开发计划
│       ├── apply.md               # 执行开发任务
│       └── gen-api-code.md        # API代码生成
├── package.json                   # 项目配置
└── README.md                     # 项目说明
```

## 使用指南

### 1. 初始化项目文档
```bash
/gorvey-plugins:fe-init-vue3
```
为项目创建完整的分布式文档系统。

### 2. 创建开发计划
```bash
/gorvey-plugins:plan
```
根据新功能需求生成详细的开发计划。

### 3. 执行开发任务
```bash
/gorvey-plugins:apply
```
按照计划自动完成开发工作。

### 4. 生成API代码
```bash
/gorvey-plugins:gen-api-code [yapi-url] [api-path] [type-path]
```
基于接口文档自动生成API代码。

## 工作流程

1. **文档初始化**：使用`fe-init-vue3`建立项目规范
2. **需求分析**：使用`plan`创建开发计划
3. **自动实现**：使用`apply`执行开发任务
4. **API集成**：使用`gen-api-code`快速集成接口

## 技术特性

- **模块化设计**：每个功能独立封装，便于维护
- **智能规范识别**：自动读取和应用项目规范
- **并发处理**：支持多任务并行处理
- **类型安全**：完整的TypeScript支持
- **错误处理**：完善的错误检查和用户提示

## 开发理念

- **规范化**：确保代码风格和结构一致
- **自动化**：减少重复性工作，提高效率
- **智能化**：基于上下文提供精准的辅助
- **可扩展**：支持自定义规范和工作流

## 作者

[@gorvey](https://github.com/gorvey)

## 相关链接

- [Claude官方文档](https://docs.anthropic.com/claude)
- [问题反馈](https://github.com/gorvey/gorvey-claude-plugin/issues)