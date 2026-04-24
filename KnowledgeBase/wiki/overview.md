# SBLD Project Wiki - 知识总览

> **最后更新**: 2026-04-17  
> **版本**: 1.0.0  
> **维护者**: SBLD Team & LLM Agent

---

## 🎯 Wiki 导航

### 快速入口

- 📊 [实体索引](../indexes/entity-index.md) - 所有实体页面
- 💡 [概念索引](../indexes/concept-index.md) - 所有概念页面
- 📝 [文档摘要](../indexes/document-index.md) - 所有文档摘要
- 🏷️ [标签索引](../indexes/tag-index.md) - 按标签浏览
- 📜 [变更日志](../logs/change-log.md) - 最近更新

---

## 📁 Wiki 结构

```
wiki/
├── overview.md           # 本文件 - 总览和导航
├── entities/             # 实体页面
│   ├── Entity-名称 1.md
│   └── Entity-名称 2.md
├── concepts/             # 概念页面
│   ├── Concept-名称 1.md
│   └── Concept-名称 2.md
├── summaries/            # 文档摘要
│   ├── Summary-文档 1.md
│   └── Summary-文档 2.md
└── synthesis/            # 综合论述
    ├── Synthesis-主题 1.md
    └── Synthesis-主题 2.md
```

---

## 📊 当前状态

### 统计信息

| 类型 | 数量 | 最近更新 |
|------|------|---------|
| 实体页面 | 0 | - |
| 概念页面 | 0 | - |
| 文档摘要 | 0 | - |
| 综合论述 | 0 | - |

> 📝 **注**: 统计数据由 LLM 自动维护，可能略有延迟

### 热门主题

*待积累足够文档后自动生成*

### 最新页面

*待创建页面后自动更新*

---

## 🔍 如何使用

### 对于新用户

1. **浏览总览**: 从本页面了解 Wiki 结构
2. **查看实体**: 访问 [实体索引](../indexes/entity-index.md) 了解关键实体
3. **学习概念**: 访问 [概念索引](../indexes/concept-index.md) 学习核心概念
4. **阅读摘要**: 访问 [文档摘要](../indexes/document-index.md) 快速了解文档内容

### 对于贡献者

1. **添加文档**: 将文档放入 `raw-docs/` 对应目录
2. **通知 LLM**: 告诉 LLM 处理新文档
3. **审查提取**: 确认 LLM 提取的信息准确
4. **补充完善**: 在对话中补充 LLM 可能遗漏的信息

### 对于查询者

1. **直接提问**: 向 LLM 提出具体问题
2. **追溯来源**: 查看回答中的引用链接
3. **深度阅读**: 点击链接查看详细信息
4. **反馈缺口**: 告诉 LLM 知识缺口在哪里

---

## 🎓 Wiki 使用指南

### 文档层级

```
原始文档 (raw-docs/)
    ↓ 读取
文档摘要 (summaries/)
    ↓ 提取
实体/概念页面 (entities/, concepts/)
    ↓ 综合
综合论述 (synthesis/)
```

### 链接规范

所有 Wiki 内部链接使用相对路径：

```markdown
# 从 overview.md 出发
- [实体页面](entities/Entity-名称.md)
- [概念页面](concepts/Concept-名称.md)
- [文档摘要](summaries/Summary-名称.md)
- [综合论述](synthesis/Synthesis-主题.md)

# 从 entities/ 出发
- [返回总览](../overview.md)
- [其他实体](Entity-其他.md)
- [相关概念](../concepts/Concept-名称.md)
```

### 标签使用

使用预定义的标签体系：

```markdown
#通用标签
#项目 #架构 #需求 #设计 #会议

#优先级标签
#priority-critical #priority-high #priority-medium #priority-low

#状态标签
#status-proposed #status-approved #status-implemented #status-deprecated
```

---

## 📋 知识领域

### 核心领域

*待文档积累后自动分类*

### 支持领域

*待文档积累后自动分类*

### 外部参考

*待文档积累后自动整理*

---

## 🔄 更新机制

### 自动更新

LLM 会在以下情况自动更新 Wiki：

- ✅ 添加新文档时
- ✅ 回答复杂问题时
- ✅ 检测到知识缺口时
- ✅ 定期维护时

### 手动触发

你可以要求 LLM：

- "请更新所有实体页面"
- "为最近文档创建综合论述"
- "检查并修复断开的链接"
- "生成知识图谱"

---

## 📞 与 LLM 协作

### 最佳实践

#### ✅ 推荐

- 提供结构化的原始文档
- 及时确认 LLM 的提取结果
- 定期浏览 Wiki 发现错误
- 提出综合性问题促进知识合成

#### ❌ 避免

- 直接编辑 Wiki 页面（让 LLM 维护）
- 在 `raw-docs/` 外存储文档
- 删除日志文件
- 绕过 Schema 规范

### 常用指令

```
# 文档处理
"请处理这个新文档：[路径]"
"为最近添加的文档创建摘要"

# 知识查询
"我们的认证模块是如何设计的？"
"列出所有与 CQRS 相关的决策"

# 知识维护
"更新所有过期的实体页面"
"检查是否有断开的链接"
"为最近文档创建综合论述"

# 质量检查
"生成 Wiki 健康度报告"
"哪些文档还没有摘要？"
```

---

## 📈 健康度指标

### 覆盖率

- [ ] 80% 的原始文档有对应摘要
- [ ] 每个实体有 5+ 个交叉引用
- [ ] 每周至少更新一次

### 质量

- [ ] 查询命中率 > 70%
- [ ] 知识复用率 > 50%
- [ ] 用户满意度高

---

## 🎯 下一步

### 待办事项

- [ ] 添加第一批文档到 `raw-docs/`
- [ ] 让 LLM 处理文档并创建 Wiki 页面
- [ ] 审查 LLM 提取的信息
- [ ] 建立综合论述

### 长期目标

- [ ] 形成完整的知识图谱
- [ ] 建立自动更新机制
- [ ] 与外部工具集成（GitHub、Slack 等）
- [ ] 培养团队使用习惯

---

## 📚 相关资源

### 内部资源

- [Schema 配置](../schema/AGENTS.md) - 核心配置文件
- [工作流程](../schema/workflows.md) - 详细工作流程
- [治理规范](../schema/governance.md) - 质量管理规范

### 外部资源

- [Karpathy 的 LLM Wiki 构想](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- [Obsidian 知识库](https://help.obsidian.md/)
- [Zettelkasten 方法](https://zettelkasten.de/)

---

## 💬 反馈与建议

如有任何问题或建议，请：

1. 在对话中向 LLM 提出
2. 记录到 [会议纪要](../raw-docs/meetings/)
3. 创建 [综合论述](synthesis/) 讨论改进

---

> **提示**: 此页面由 LLM 维护，统计数据会定期更新。如发现信息不准确，请告知 LLM 修正。
