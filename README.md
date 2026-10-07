# Codebase Documentation AI Skill

A robust, modular prompt architecture and instruction set for AI agents to create, audit, update, and maintain software documentation based strictly on **code evidence**. 

Unlike generic writing assistants, this skill forces the AI to act as a rigorous technical writer and auditor. It prioritizes technical truth, traceability, and operational safety over mere polish.

## 🌟 Key Features

* **Evidence-Based Generation:** Forces the AI to trace actual code paths, inspect configurations, and read tests before making claims. No hallucinations or assumed APIs.
* **Modular Architecture:** Uses a central `SKILL.md` router that conditionally loads specific reference files (e.g., `audit-checklist.md`, `style-and-quality.md`) to save context window and focus the AI on the task at hand.
* **Safety First:** Strict operational boundaries. The AI is instructed *never* to execute arbitrary documentation code, authorize deployments, or alter runtime semantics just to make the documentation look correct.
* **Environment-Aware:** Designed to leverage advanced Model Context Protocol (MCP) tools like `codebase-memory-mcp` for AST/graph navigation or external dependency resolvers, with graceful fallbacks to standard text search if those tools are unavailable.
* **Docs-as-Code Focused:** Aligns with standard engineering practices, including Diátaxis architecture, C4 models, and Architectural Decision Records (ADRs).

## 📂 Repository Structure

The skill is divided into a main entry point and a directory of specialized references:

```text
.
├── CONTRIBUTING.md
├── CLA.md
├── LICENSE
├── README.md
├── plugin.json                           # Antigravity Plugin manifest
├── agents/
│   └── openai.yaml                       # Agent configuration profiles
└── skills/
    └── ai-codebase-documentation/
        ├── SKILL.md                      # The main entry point and routing instructions
        └── references/
            ├── audit-checklist.md            # Framework for comprehensive docs auditing
            ├── code-comments-and-examples.md # Rules for docstrings and code-adjacent docs
            ├── evidence-and-discovery.md     # Strategy for finding truth in the codebase
            ├── information-architecture.md   # Guidance on Diátaxis, READMEs, and ADRs
            ├── maintenance-and-change-impact.md # Syncing docs with code diffs
            ├── sources.md                    # External provenance and inspiration
            ├── style-and-quality.md          # Technical writing standards
            ├── templates.md                  # Standardized markdown formats for outputs
            └── tooling-and-validation.md     # Safe use of CI/generators/testing tools
```

## 🚀 How to Use

This project is structured as a **Plugin** for advanced LLMs and coding agents (like Antigravity, Cursor, or GitHub Copilot workspaces).

### For Antigravity & Plugin-Compatible Agents
1. **Install as a Plugin:** Clone this repository directly into your `plugins/` directory (e.g., `.gemini/config/plugins/ai-codebase-documentation/`).
2. The agent will automatically detect `plugin.json` and load the associated skills and subagents natively.

### For Cursor, Copilot, & General Usage
1. **Clone the repository** into your workspace.
2. **Set the context:** Point your AI directly to the `SKILL.md` file when requesting documentation work. 
   * *Example prompt:* "Review the recent changes in `src/auth.ts`. Read `skills/ai-codebase-documentation/SKILL.md` to understand how to audit and update the related documentation, and apply the changes."
3. **Let the router work:** The AI will read `SKILL.md`, determine the scope of your request, and autonomously load the necessary files from the `references/` folder.

### Tooling Compatibility

This skill is highly adaptable. It natively understands and attempts to use advanced codebase navigation tools (like `search_graph` or `trace_path`) if your agent supports them. If not, the instructions automatically direct the AI to fall back to standard file reads and grep searches.

## 🤝 Contributing

Contributions are welcome! If you have improvements for the audit checklists, new templates, or better ways to prevent AI hallucinations in technical documentation, please open an issue or submit a pull request.

Please review our [Contributing Guidelines](CONTRIBUTING.md). When you open a Pull Request, our CLA Assistant will prompt you to review and sign the [Contributor License Agreement](CLA.md).

## 📜 License

This project is open-sourced under the [GPL-3.0-or-later License](LICENSE).

**Commercial/Non-GPL Licensing:** We offer a commercial/non-GPL licensing model. If your organization requires a commercial license, extended support, or cannot comply with the strictly copyleft requirements of the GPLv3, please contact the project owner [CesarJER](https://github.com/CesarJER) to discuss commercial licensing, custom integrations, or dedicated support.