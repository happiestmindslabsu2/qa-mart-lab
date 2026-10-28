# QA Mart Testcase Kit

An Agent Plugins 1.0 package for designing, creating, extending, and reviewing manual QA test cases for QA Mart. It has no MCP server, hooks, or external dependencies.

## Components

| Component | Purpose |
|---|---|
| `skills/manual-test-case-creation` | End-to-end testcase design and review workflow |
| `com.github.copilot/agents/manual-test-case.agent.md` | User-invocable testcase specialist |
| `references/` | Canonical rules, testcase template, and instruction references |

The instruction files in `references/` are bundled as guidance only. Plugins do not install workspace instructions as first-class components. The project versions remain in `.github/copilot-instructions.md` and `.github/instructions/`.

## Local Registration

Enable plugins and add this folder to VS Code settings, replacing the example path with its absolute path:

```json
{
  "chat.plugins.enabled": true,
  "chat.pluginLocations": {
    "/absolute/path/to/qa-mart-testcase-kit": true
  }
}
```

Then check Extensions > `@agentPlugins` and Chat > Open Customizations for the `manual-test-case-creation` skill and `Manual Test Case Agent`.