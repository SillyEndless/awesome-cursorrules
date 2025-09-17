语言设置：除非用户另有指示，所有常规交互响应都应该使用中文。补充：代码注释和README或者文档需要为中文。

## MCP 交互式反馈规则

1. 在任何流程、任务或对话中，无论是提问、响应还是完成阶段任务，都必须调用 MCP mcp-feedback-enhanced。
2. 收到用户反馈后，只要反馈内容非空，必须再次调用 MCP mcp-feedback-enhanced，并根据反馈调整行为。
3. 只有当用户明确表示"结束"或"不再需要交互"时，才能停止调用 MCP mcp-feedback-enhanced，此时流程才算完成。
4. 除非收到结束指令，所有步骤都必须反复调用 MCP mcp-feedback-enhanced。
5. 在任务完成前，需使用 MCP mcp-feedback-enhanced 向用户征求反馈。


## Context7

利用 [context7](https://github.com/upstash/context7) 工具，直接在开发环境中获取并集成最新、特定版本的文档和代码示例。
确保生成的代码引用当前 API 和最佳实践，减少因信息过时导致的错误。


## Sequential Thinking（分步问题解决框架）

使用 [Sequential Thinking](https://github.com/smithery-ai/reference-servers/tree/main/src/sequentialthinking) 工具，指导分步骤地解决问题，尤其适用于复杂、开放式任务。

- 使用 Sequential Thinking 协议将任务拆解为**思维步骤**。
- 每一步遵循以下结构：
  1. 明确当前目标或假设（如“评估身份验证选项”、“重构状态管理”）。
  2. 根据上下文选择合适的 MCP 工具（如 `search_docs`、`code_generator`、`error_explainer`）。
  3. 清晰地记录结果/输出。
  4. 确定下一步思考目标，继续推进。
- 存在不确定性时：
  - 可通过“分支思考”探索多种解决路径。
  - 比较权衡不同策略或方案。
  - 允许回滚或编辑前序思维步骤。
- 可用元数据包括：
  -`thought`：当前思维内容
  -`thoughtNumber`：当前步骤编号
  -`totalThoughts`：预计总步骤数