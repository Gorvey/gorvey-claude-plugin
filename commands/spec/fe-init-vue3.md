---
description: 初始化分布式 CLAUDE.md 文档系统
---

# 分布式 CLAUDE.md 文档生成系统

这个命令将为项目的每个关键目录创建专门的 CLAUDE.md 文档，实现模块化的知识管理。
注意，这些文档是给后续的workflow /plan和/apply agent调用的，不需要给用户查看上手入门，不需要解释每个功能的作用，只需要让agent在后面抓取成为了记忆文件后，能够按照这个规范，生成一致的，功能性完备的代码！！！，这非常重要

## 执行步骤

1. 扫描 `src/` 目录结构，识别所有需要文档化的关键目录
2. 为每个目录使用 fe-init-agent 子代理，并发式的创建分析并生成专门的 CLAUDE.md 文件

## Sub Agent 执行逻辑

### 每个 Sub Agent 将负责：

1. **目录分析**：深入分析指定目录的结构和内容
2. **功能识别**：识别该目录的核心功能和用途
3. **依赖分析**：分析该目录的依赖关系和被依赖关系
4. **最佳实践提取**：从现有代码中提取最佳实践和使用模式
5. **文档生成**：生成针对该目录的专门 CLAUDE.md 文件

### 目标目录映射

```
src/
├── api/           → src/api/CLAUDE.md (API 接口开发指南)
├── components/    → src/components/CLAUDE.md (全局组件库文档)
├── views/         → src/views/CLAUDE.md (页面开发指南)
├── stores/        → src/stores/CLAUDE.md (状态管理指南)
├── utils/         → src/utils/CLAUDE.md (工具函数库说明)
├── hooks/         → src/hooks/CLAUDE.md (组合式 API 指南)
├── styles/        → src/styles/CLAUDE.md (样式处理方案)
├── routers/       → src/routers/CLAUDE.md (路由配置指南)
└── layouts/       → src/layouts/CLAUDE.md (布局组件指南)
```

## 注意事项

1. **现有项目分析**：深入分析现有代码，提取实际的使用模式
2. **最佳实践**：从现有代码中识别并记录最佳实践
3. **依赖关系**：明确各模块间的依赖关系
4. **一致性**：确保所有文档的风格和规范一致
