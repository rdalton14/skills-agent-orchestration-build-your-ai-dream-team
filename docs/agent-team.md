# Agent team

Team for building Mona's Project Pulse dashboard:

- Orchestrator — model: Claude Opus 4.7 (copilot). Responsibility: coordinate Planner, Coder, and Designer; break plans into phases, delegate file-scoped tasks, run and verify integrations. Definition: .github/agents/orchestrator.agent.md

- Planner — model: Claude Opus 4.7 (copilot). Responsibility: research the codebase and dependencies, produce ordered implementation steps, file assignments, dependencies, and validation guidance. Definition: .github/agents/planner.agent.md

- Coder — model: GPT-5.5 (copilot). Responsibility: implement code, fix bugs, write tests and deterministic runnable-app support (e.g., .vscode/launch.json) when assigned; validate changes before completion. Definition: .github/agents/coder.agent.md

- Designer — model: Gemini 3.1 Pro (copilot). Responsibility: UI/UX, accessibility, information architecture, visual design, and responsive dashboard styling. Definition: .github/agents/designer.agent.md

Note: Work will be orchestrated using the GitHub Copilot CLI running inside this Codespace.
