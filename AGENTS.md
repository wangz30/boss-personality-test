# SBLD Project - LLM 系统提示词

## 🎯 核心指令

### 一、执行任务前：先查知识库

**必须按顺序查阅以下文档**，明确项目进展后再开始工作：

1. **查看 Wiki 总览** → [`KnowledgeBase/wiki/overview.md`](KnowledgeBase/wiki/overview.md)
   - 了解项目整体知识结构
   - 查看最新统计和热门主题

2. **查看变更日志** → [`KnowledgeBase/logs/change-log.md`](KnowledgeBase/logs/change-log.md)
   - 了解最近的项目进展
   - 查看最新添加的文档和页面

3. **查看相关索引** → [`KnowledgeBase/indexes/`](KnowledgeBase/indexes/)
   - [`entity-index.md`](KnowledgeBase/indexes/entity-index.md) - 实体索引
   - [`concept-index.md`](KnowledgeBase/indexes/concept-index.md) - 概念索引
   - [`document-index.md`](KnowledgeBase/indexes/document-index.md) - 文档索引

4. **查阅核心配置** → [`KnowledgeBase/schema/AGENTS.md`](KnowledgeBase/schema/AGENTS.md)
   - 了解 LLM Wiki 的工作流程
   - 遵循文档规范和标准

---

### 二、执行任务后：更新知识库

**完成任务后，必须按以下流程更新知识库**：

#### 1. 整理新文档
```
如有新文档 → 放入 KnowledgeBase/raw-docs/ 对应目录
- 需求文档 → raw-docs/requirements/
- 设计文档 → raw-docs/design/
- 会议纪要 → raw-docs/meetings/
- 架构文档 → raw-docs/architecture/
- 决策记录 → raw-docs/decisions/
```

#### 2. 让 LLM 处理文档
```
告知 LLM："请处理这个新文档：[完整路径]"

LLM 将自动：
✅ 创建摘要页面 → wiki/summaries/
✅ 创建/更新实体页面 → wiki/entities/
✅ 创建/更新概念页面 → wiki/concepts/
✅ 更新索引 → indexes/
✅ 记录日志 → logs/
```

#### 3. 审查和确认
```
- 审查 LLM 提取的实体、概念、决策
- 确认摘要准确性
- 补充遗漏信息
```

#### 4. 记录变更
```
更新 → KnowledgeBase/logs/change-log.md
记录本次任务的所有变更
```

---

### 三、遵循的核心文档

**所有操作必须遵循以下文档**：

| 文档 | 用途 | 优先级 |
|------|------|--------|
| [`schema/AGENTS.md`](KnowledgeBase/schema/AGENTS.md) | 核心配置、工作流程 | ⭐⭐⭐⭐⭐ |
| [`schema/workflows.md`](KnowledgeBase/schema/workflows.md) | 详细操作流程 | ⭐⭐⭐⭐ |
| [`schema/governance.md`](KnowledgeBase/schema/governance.md) | 质量标准和规范 | ⭐⭐⭐⭐ |
| [`README.md`](KnowledgeBase/README.md) | 快速入门指南 | ⭐⭐⭐ |

---

## 📋 快速参考

### 知识库查询流程
```
1. overview.md → 了解全局
2. change-log.md → 了解进展
3. indexes/ → 查找具体内容
4. schema/AGENTS.md → 遵循操作规范
```

### 知识库更新流程
```
1. 新文档 → raw-docs/对应目录
2. 告知 LLM 处理
3. 审查提取结果
4. 记录到 change-log.md
```

### 关键原则
- ✅ **先查后做**：任务前必须查阅知识库
- ✅ **及时更新**：任务后必须更新知识库
- ✅ **遵循流程**：按照 schema 文档操作
- ✅ **保证质量**：符合元数据和质量标准

---

**最后更新**: 2026-04-17  
**版本**: 3.0.0 (精简版系统提示词)
