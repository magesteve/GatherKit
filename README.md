# GatherKit

**GatherKit** is an open-source collection of command-line tools that gather project context for AI-assisted software development.

Today's AI assistants are remarkably capable, but they still depend on developers to provide the right context. GatherKit automates the repetitive work of gathering source code, documentation, configuration files, recent changes, review context, and symbol-related files into consistent, human-readable documents.

> **GatherKit doesn't perform AI—it prepares projects so today's AI assistants can understand them more effectively.**

---

## Why GatherKit?

While developing my open-source VR framework, **AetherCircle**, I found myself repeatedly performing the same steps before asking an AI assistant for help:

- Gather relevant source files
- Collect supporting documentation
- Include project configuration
- Explain recent changes
- Prepare code-review context
- Locate every definition and reference for a symbol
- Describe the overall project structure

The process was repetitive, time-consuming, and easy to overlook.

Rather than repeating the same manual steps for every conversation, I built GatherKit to automate the workflow.

---

## Current Gatherers

GatherKit currently includes six command-line tools.

| Command | Purpose |
|---------|---------|
| `codegather` | Gather source code and build configuration |
| `docgather` | Gather project documentation |
| `projectgather` | Gather source, documentation, configuration, and project metadata |
| `changegather` | Gather files changed in Git |
| `reviewgather` | Gather changed files, unified diffs, and current file contents |
| `symbolgather` | Gather symbol matches, nearby context, and matching files |

The project and conceptual tool names may be written as **CodeGather**, **DocGather**, **ProjectGather**, **ChangeGather**, **ReviewGather**, and **SymbolGather**, while the executable commands follow normal Unix lowercase conventions.

---

## codegather

`codegather` gathers recognized source-code and build-configuration files into a single timestamped document suitable for sharing with an AI assistant.

By default, it gathers all supported source types. It currently recognizes files associated with:

- Swift and Metal
- Dart and Flutter
- C, C++, and Objective-C
- Python
- JavaScript and TypeScript
- Java and Kotlin
- Rust
- Go
- C#
- Ruby
- PHP
- Shell scripting
- Common build systems and package manifests

Examples:

```bash
codegather
codegather --swift
codegather --dart
codegather --flutter
codegather --swift --cpp
codegather --python
codegather --javascript
codegather --include "*.sql"
codegather --exclude "*/Generated/*"
codegather --output CurrentCode.txt
```

Display all options:

```bash
codegather --help
```

---

## docgather

`docgather` gathers recognized project documentation into a single timestamped document.

It recognizes:

- Markdown
- reStructuredText
- AsciiDoc
- README files
- CHANGELOG files
- CONTRIBUTING files
- SECURITY files
- CODE_OF_CONDUCT files
- ROADMAP files
- Other common project documentation names

Examples:

```bash
docgather
docgather --include "*.wiki"
docgather --exclude "*/Archive/*"
docgather --output CurrentDocumentation.txt
```

Plain `.txt` files are not included automatically because projects often contain logs, generated output, data files, and previous GatherKit documents. They can still be included explicitly:

```bash
docgather --include "*.txt"
```

---

## projectgather

`projectgather` gathers a broad project snapshot containing:

- Source code
- Documentation
- Build files
- Package manifests
- Common project configuration
- Git branch, commit, and dirty-state metadata

Examples:

```bash
projectgather
projectgather --include "*.sql"
projectgather --exclude "*/Generated/*"
projectgather --output CurrentProject.txt
```

---

## changegather

`changegather` gathers files changed in Git.

By default, it includes:

- Staged changes
- Unstaged tracked changes
- Untracked files

It can also gather changes relative to a commit or branch.

Examples:

```bash
changegather
changegather --since HEAD~3
changegather --since main
changegather --range main..feature-branch
changegather --staged
changegather --unstaged
changegather --untracked
changegather --include "*.swift"
changegather --exclude "*/Generated/*"
```

---

## reviewgather

`reviewgather` creates a review-focused document containing:

- Git metadata
- Changed-file index
- Unified diffs
- Current contents of changed files
- Deleted or unavailable filenames

Examples:

```bash
reviewgather
reviewgather --since main
reviewgather --range main..feature-branch
reviewgather --staged
reviewgather --context 8
reviewgather --include "*.swift"
reviewgather --exclude "*/Generated/*"
```

---

## symbolgather

`symbolgather` searches the project for a symbol or text pattern and creates a document containing:

- Project and Git metadata
- Match index with file names and line numbers
- Nearby source context
- Full contents of every matching file

Examples:

```bash
symbolgather AetherClock
symbolgather AetherClock --include "*.swift"
symbolgather "class AetherClock" --fixed
symbolgather "render.*frame" --ignore-case
symbolgather AetherClock --context 8
```

By default, the search term is interpreted as a regular expression. Use `--fixed` for literal text.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/magesteve/GatherKit.git
cd GatherKit
```

Make the scripts executable:

```bash
chmod +x codegather docgather projectgather changegather reviewgather symbolgather
```

Run them directly from the repository:

```bash
./codegather
./docgather
./projectgather
```

Or install them as commands available from anywhere:

```bash
sudo cp codegather docgather projectgather changegather reviewgather symbolgather /usr/local/bin/
```

Then run any gatherer from the root of a project:

```bash
codegather
docgather
projectgather
changegather
reviewgather
symbolgather AetherClock
```

GatherKit currently requires macOS or another environment with `zsh`. The Git-focused gatherers also require Git.

---

## Output

Each gatherer creates a timestamped text document in the current project directory.

Examples:

```text
AetherCircle-CodeGather-20260803-210500.txt
AetherCircle-DocGather-20260803-210510.txt
AetherCircle-ProjectGather-20260803-210520.txt
AetherCircle-ChangeGather-20260803-210530.txt
AetherCircle-ReviewGather-20260803-210540.txt
AetherCircle-AetherClock-SymbolGather-20260803-210550.txt
```

Generated documents include clear file separators and an index so both humans and AI assistants can navigate them easily.

---

## Philosophy

Most discussions about AI-assisted software development focus on **prompt engineering**—how developers communicate with AI.

GatherKit focuses on the other half of the conversation:

> **How can a software project communicate more effectively with AI?**

GatherKit follows a few simple principles:

1. **Simple** — each command has one clear purpose.
2. **Deterministic** — files are ordered consistently.
3. **Human-readable** — output is useful to both people and AI assistants.
4. **AI-neutral** — the documents can be used with any AI system.
5. **Lightweight** — the tools rely on standard command-line utilities.
6. **Temporary by design** — as AI development tools mature, some GatherKit workflows may eventually become unnecessary.

AI development tools are improving rapidly. Many already integrate with Git repositories, IDEs, issue trackers, and documentation systems. As these capabilities mature, much of what GatherKit does today may eventually become built into our development environments.

Until then, GatherKit provides a lightweight, repeatable workflow for preparing project context for today's AI assistants.

---

## Vision

GatherKit begins as a family of small, focused command-line tools, but the larger idea is broader:

> Project context should be generated instead of assembled manually.

Different conversations require different views of a project. GatherKit provides those views without tying the developer to one AI assistant, IDE, programming language, or workflow.

---

## Roadmap

- [x] Multi-language `codegather`
- [x] Dart and Flutter support
- [x] `docgather`
- [x] `projectgather`
- [x] `changegather`
- [x] `reviewgather`
- [x] `symbolgather`
- [ ] Shared configuration file
- [ ] Configurable default include and exclude patterns
- [ ] File-size safeguards and skipped-file reporting
- [ ] Optional dependency lock-file gathering
- [ ] Additional project-configuration support
- [ ] Homebrew installation
- [ ] Linux testing and support
- [ ] Windows PowerShell equivalents
- [ ] Automated tests
- [ ] Tagged releases

---

## Contributing

Ideas, bug reports, feature requests, and pull requests are welcome.

GatherKit is intentionally designed to remain lightweight, portable, deterministic, and easy to understand.

---

## License

GatherKit is released under the MIT License.

See the `LICENSE` file for details.

---

## Related Article

**Teaching Your Project to Talk to AI**

The accompanying article explains the motivation behind GatherKit, how the idea emerged while developing AetherCircle, and why project context may become as important as prompt engineering.

https://magesteve.medium.com/beyond-prompt-engineering-designing-projects-for-ai-collaboration-28d50b331574
