# SBLD Project LLM Wiki - Schema Configuration

## 🎯 核心理念

本知识库基于 Karpathy 的 LLM Wiki 架构模式，核心目标是：
- **持久化知识积累**：不是简单的 RAG 检索，而是构建持续进化的知识体系
- **增量式更新**：每次添加新文档时，LLM 自动提取、整合、更新现有知识
- **结构化关联**：文档间自动建立交叉引用，形成知识网络
- **合成与演进**：从原始文档 → 摘要 → 实体/概念页面 → 综合论述，层层提炼

---

## 📁 目录结构

```
KnowledgeBase/
├── raw-docs/              # 原始文档层（不可变，只读）
│   ├── requirements/      # 需求文档
│   ├── design/           # 设计文档
│   ├── meetings/         # 会议纪要
│   ├── research/         # 研究资料
│   └── external/         # 外部参考资料
│
├── wiki/                 # Wiki 核心层（LLM 维护的动态知识）
│   ├── entities/         # 实体页面（人、组织、产品、技术等）
│   ├── concepts/         # 概念页面（理论、方法、模式等）
│   ├── summaries/        # 文档摘要（每篇原始文档对应一个摘要）
│   ├── synthesis/        # 综合论述（跨文档的主题性综合）
│   └── overview.md       # Wiki 总览和导航
│
├── indexes/              # 索引层
│   ├── entity-index.md   # 实体索引
│   ├── concept-index.md  # 概念索引
│   ├── document-index.md # 文档索引
│   └── tag-index.md      # 标签索引
│
├── logs/                 # 日志层
│   ├── ingestion-log.md  # 文档摄入日志
│   ├── change-log.md     # Wiki 变更日志
│   └── query-log.md      # 查询日志
│
├── templates/            # 模板层
│   ├── entity-template.md
│   ├── concept-template.md
│   ├── summary-template.md
│   └── synthesis-template.md
│
└── schema/               # Schema 配置层（本目录）
    ├── AGENTS.md         # 核心配置文件（本文件）
    ├── workflows.md      # 工作流程定义
    └── governance.md     # 治理规范
```

---

## 🔧 LLM 工作流程

### 1. 文档摄入流程 (Ingestion Workflow)

当用户添加新文档到 `raw-docs/` 时：

```
1. 读取原始文档
2. 提取关键信息：
   - 文档类型（需求/设计/会议/研究）
   - 核心实体（人物、技术、产品等）
   - 核心概念（理论、方法等）
   - 关键决策和结论
   - 时间戳和版本
3. 创建摘要页面（wiki/summaries/）
4. 更新或创建实体页面（wiki/entities/）
5. 更新或创建概念页面（wiki/concepts/）
6. 更新索引文件
7. 记录摄入日志
```

### 2. 查询响应流程 (Query Workflow)

当用户提问时：

```
1. 优先检索 Wiki 层（entities/, concepts/, synthesis/）
2. 如 Wiki 中信息不足，检索原始文档摘要
3. 必要时引用原始文档
4. 如发现知识缺口，提示用户是否需要：
   - 添加新文档
   - 创建新的综合论述页面
```

### 3. Wiki 维护流程 (Maintenance Workflow)

每次对话结束时自动执行：

```
1. 检查是否有新的实体需要创建页面
2. 检查是否有实体页面需要更新
3. 检查概念间的关联是否需要加强
4. 更新变更日志
5. 验证索引的完整性
```

---

## 📝 文档规范

### 文件命名规范

- **原始文档**: `YYYYMMDD-类型 - 标题.md`
  - 示例：`20260417-requirements-SBLD-core-features.md`
  
- **实体页面**: `Entity-名称.md`（PascalCase）
  - 示例：`Entity-AuthenticationModule.md`
  
- **概念页面**: `Concept-名称.md`（PascalCase）
  - 示例：`Concept-EventSourcing.md`
  
- **摘要页面**: `Summary-文档标题.md`
  - 示例：`Summary-SBLD-core-features.md`
  
- **综合论述**: `Synthesis-主题.md`
  - 示例：`Synthesis-Authentication-patterns.md`

### 元数据规范（Frontmatter）

所有 Wiki 页面必须包含以下元数据：

```markdown
---
type: entity|concept|summary|synthesis
created: YYYY-MM-DD HH:MM:SS
updated: YYYY-MM-DD HH:MM:SS
version: 1.0.0
tags: [tag1, tag2, tag3]
related: [Entity-Name1, Concept-Name2]
source: [raw-docs/path/to/source.md](file:///raw-docs/path/to/source.md)
status: draft|review|stable|deprecated
---
```

### 交叉引用规范

使用 Markdown 链接建立文档间关联：

```markdown
- 实体引用：[Entity-名称](entities/Entity-名称.md)
- 概念引用：[Concept-名称](concepts/Concept-名称.md)
- 摘要引用：[Summary-标题](summaries/Summary-标题.md)
- 综合引用：[Synthesis-主题](synthesis/Synthesis-主题.md)
```

---

## 🏷️ 分类体系

### 文档类型（Document Types）

- `requirements` - 需求文档
- `design` - 设计文档
- `architecture` - 架构文档
- `meeting` - 会议纪要
- `research` - 研究资料
- `decision` - 决策记录（ADR）
- `tutorial` - 教程文档
- `external` - 外部资料

### 实体类型（Entity Types）

- `Person` - 项目成员、利益相关者
- `Organization` - 团队、部门、外部组织
- `Product` - 产品、功能模块
- `Technology` - 技术栈、工具、框架
- `System` - 子系统、服务
- `Event` - 重要事件、里程碑

### 概念类型（Concept Types）

- `Pattern` - 设计模式、架构模式
- `Principle` - 设计原则、指导方针
- `Method` - 方法、流程
- `Theory` - 理论、模型
- `Standard` - 标准、规范

### 优先级标签（Priority Tags）

- `priority-critical` - 关键
- `priority-high` - 高优先级
- `priority-medium` - 中优先级
- `priority-low` - 低优先级

### 状态标签（Status Tags）

- `status-proposed` - 已提议
- `status-approved` - 已批准
- `status-implemented` - 已实现
- `status-deprecated` - 已废弃

---

## 🔐 权限管理

### 访问级别

| 级别 | 权限 | 适用对象 |
|------|------|----------|
| `read` | 只读 | 所有项目成员 |
| `write` | 创建/编辑 Wiki 页面 | 核心团队成员 |
| `admin` | 删除文档、修改 Schema | 项目管理员 |
| `system` | LLM 自动维护 | LLM Agent |

### 文档可见性

- `public` - 对所有项目成员可见（默认）
- `team` - 仅对特定团队可见
- `private` - 仅对管理员可见

### 实现方式

在文档元数据中标注：

```markdown
---
visibility: public|team|private
access_level: read|write|admin
allowed_teams: [team1, team2]
---
```

---

## 📊 版本控制

### Wiki 页面版本

每次更新 Wiki 页面时：

1. 递增版本号（语义化版本：major.minor.patch）
2. 在页面底部添加版本历史：

```markdown
## Version History

- v1.0.0 (2026-04-17) - Initial version
- v1.1.0 (2026-04-18) - Added related entities
```

### 变更日志

在 `logs/change-log.md` 中记录：

```markdown
## 2026-04-17

- [CREATE] [Entity-AuthenticationModule](entities/Entity-AuthenticationModule.md)
- [UPDATE] [Concept-CQRS](concepts/Concept-CQRS.md) - Added implementation details
- [LINK] Linked [Entity-UserManagement](entities/Entity-UserManagement.md) to [Synthesis-Auth-Flow](synthesis/Synthesis-Auth-Flow.md)
```

---

## 🔄 质量保证

### 自动检查项

LLM 在每次更新 Wiki 时必须验证：

- [ ] 元数据完整（type, created, updated, version, tags）
- [ ] 交叉引用有效（链接的目标文件存在）
- [ ] 标签使用规范（使用预定义的标签体系）
- [ ] 版本號正确递增
- [ ] 变更已记录到日志

### 人工审查触发条件

以下情况需要标记为需要人工审查：

- 删除实体或概念页面
- 修改核心架构决策
- 标记文档为 deprecated
- 创建新的综合论述页面

使用标记：

```markdown
> ⚠️ **REVIEW REQUIRED**: This change requires team review.
> Reason: [说明原因]
```

---

## 🚀 可扩展性设计

### 水平扩展

当某个分类的文档超过 50 篇时，自动创建子分类：

```
entities/
├── people/
├── technologies/
├── products/
└── organizations/
```

### 垂直深化

当某个主题的知识足够丰富时，创建专题 Wiki：

```
wiki/specializations/
└── authentication-wiki/
    ├── overview.md
    ├── entities/
    ├── concepts/
    └── synthesis/
```

### 外部集成

预留接口支持：

- GitHub Issues 同步
- Slack 讨论归档
- 会议录音转文字
- 外部 API 数据源

---

## 📖 使用示例

### 示例 1：添加新文档

用户操作：
```
将新的需求文档放入 raw-docs/requirements/
告诉 LLM："请处理这个新文档"
```

LLM 响应：
1. 读取文档
2. 创建摘要页面
3. 识别并创建/更新 3 个实体页面
4. 识别并创建/更新 2 个概念页面
5. 更新索引
6. 记录日志
7. 向用户确认关键提取内容

### 示例 2：查询知识

用户提问：
```
"我们的认证模块是如何设计的？"
```

LLM 响应：
1. 检索 [Entity-AuthenticationModule](entities/Entity-AuthenticationModule.md)
2. 检索相关概念 [Concept-CQRS](concepts/Concept-CQRS.md), [Concept-EventSourcing](concepts/Concept-EventSourcing.md)
3. 检索综合论述 [Synthesis-Auth-Patterns](synthesis/Synthesis-Auth-Patterns.md)
4. 综合回答，并附上相关链接

### 示例 3：知识维护

LLM 主动提示：
```
我注意到以下知识缺口：
1. 提到了 3 次 "Event Store"，但没有对应的概念页面
2. [Entity-UserManagement](entities/Entity-UserManagement.md) 已 2 周未更新，但相关文档增加了 5 篇

建议：
- 创建 Concept-EventStore 页面？
- 更新 Entity-UserManagement 页面？
```

---

## 🎯 成功指标

衡量 Wiki 健康度的指标：

- **覆盖率**: 80% 的原始文档有对应的摘要页面
- **关联度**: 平均每个实体页面有 5+ 个交叉引用
- **更新频率**: Wiki 页面每周至少更新一次
- **查询满意度**: 用户查询能在 Wiki 中找到答案的比例 > 70%
- **知识复用**: 新文档引用现有 Wiki 页面的比例 > 50%

---

## 📞 与 LLM 协作的最佳实践

### 你应该做的：

✅ 提供高质量的原始文档（清晰、结构化）
✅ 及时确认 LLM 提取的关键信息
✅ 定期浏览 Wiki，发现错误或遗漏
✅ 提出综合性的问题，促进知识合成

### 你不应该做的：

❌ 直接编辑 Wiki 页面（让 LLM 维护）
❌ 在 raw-docs 目录外存储文档
❌ 删除带有时间戳的日志文件
❌ 绕过 Schema 规范创建文档

---

## 📚 参考资源

- [Karpathy 的 LLM Wiki 原始构想](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- [Obsidian 知识库最佳实践](https://help.obsidian.md/)
- [Zettelkasten 方法](https://zettelkasten.de/)
- [Building a Second Brain](https://buildingasecondbrain.com/)

---

**最后更新**: 2026-04-17
**版本**: 1.0.0
**维护者**: SBLD Team & LLM Agent
