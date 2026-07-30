# GatherKit

**GatherKit** is an open-source collection of command-line utilities that prepare software projects for AI collaboration.

Today's AI assistants are remarkably capable, but they still rely on developers to provide the right context. GatherKit automates the repetitive task of gathering source code, documentation, configuration files, and other project information into a consistent format, allowing you to spend less time preparing context and more time solving problems.

GatherKit doesn't perform AI—it prepares projects so today's AI assistants can understand them more effectively.

---

## Why GatherKit?

While developing the open-source **AetherCircle** framework, I found myself repeatedly performing the same steps before asking an AI assistant for help:

- Gathering relevant source files
- Collecting related documentation
- Including project configuration
- Explaining recent changes
- Describing the overall project structure

The process was repetitive, time-consuming, and easy to forget.

GatherKit was created to automate that workflow.

---

## Current Utilities

### CodeGather

Collects source files into a single timestamped document suitable for sharing with an AI assistant.

Future versions will support multiple languages, project metadata, and customizable output formats.

---

## Planned Utilities

| Utility | Purpose |
|---------|---------|
| **CodeGather** | Gather source code |
| **DocGather** | Gather project documentation |
| **ProjectGather** | Gather an entire project context |
| **ChangeGather** | Gather only files changed since a commit |
| **ReviewGather** | Gather everything needed for code review |
| **SymbolGather** | Gather definitions and references for a symbol |

Additional tools will be added as new workflows emerge.

---

## Philosophy

Most discussions about AI-assisted software development focus on **prompt engineering**—how developers communicate with AI.

GatherKit focuses on the other half of the conversation:

> **How can a project communicate more effectively with AI?**

The goal isn't to replace IDE integrations or future AI capabilities. As development tools continue to evolve, many of GatherKit's features may eventually become unnecessary.

Until then, GatherKit provides a simple, repeatable workflow for preparing project context for today's AI assistants.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/magesteve/GatherKit.git
cd GatherKit
chmod +x CodeGather
```

You can run it directly:

```bash
/path/to/GatherKit/CodeGather
```

To make it available as a normal terminal command:

```bash
sudo cp CodeGather /usr/local/bin/CodeGather
```

Then, from the root of a Swift project:

```bash
CodeGather
```
---

## Contributing

Ideas, bug reports, feature requests, and pull requests are always welcome.

GatherKit is intentionally designed to remain lightweight, portable, and easy to understand.

---

## License

GatherKit is released under the MIT License.

See the LICENSE file for details.

---

## Related Article

**Teaching Your Project to Talk to AI**

The accompanying article explains the motivation behind GatherKit, how it fits into modern AI-assisted development, and why project context is becoming as important as prompt engineering.
