# GatherKit

**GatherKit** is an open-source collection of command-line tools that
gather project context for AI-assisted software development.

Today's AI assistants are remarkably capable, but they still depend on
developers to provide the right context. GatherKit automates the
repetitive task of gathering source code, documentation, configuration
files, and other project information into a consistent format, allowing
you to spend less time preparing context and more time solving problems.

> **GatherKit doesn't perform AI---it prepares projects so today's AI
> assistants can understand software projects more effectively.**

------------------------------------------------------------------------

## Why GatherKit?

While developing my open-source VR framework, **AetherCircle**, I found
myself repeatedly performing the same steps before asking an AI
assistant for help:

-   Gather relevant source files
-   Collect supporting documentation
-   Include project configuration
-   Explain recent changes
-   Describe the overall project structure

The process was repetitive, time-consuming, and easy to overlook.

Rather than repeating the same manual steps for every conversation, I
built GatherKit to automate the workflow.

------------------------------------------------------------------------

## Current Gatherers

### CodeGather

**CodeGather** gathers Swift source files into a single timestamped
document suitable for sharing with an AI assistant.

Version 0.1 supports:

-   Swift projects
-   macOS
-   zsh

Future versions will support additional programming languages,
configurable file selection, and customizable output formats.

------------------------------------------------------------------------

## Vision

GatherKit begins with **CodeGather**, but the larger goal is a family of
small, focused tools that gather different kinds of project context for
different kinds of AI conversations.

  -----------------------------------------------------------------------
  Gatherer                              Purpose
  ------------------------------------- ---------------------------------
  **CodeGather**                        Gather source code

  **DocGather**                         Gather project documentation

  **ProjectGather**                     Gather source, documentation, and
                                        configuration into a complete
                                        project context

  **ChangeGather**                      Gather only files changed since a
                                        commit or branch

  **ReviewGather**                      Gather everything needed for a
                                        code review

  **SymbolGather**                      Gather every definition and
                                        reference for a symbol
  -----------------------------------------------------------------------

Additional gatherers will be added as new workflows emerge.

------------------------------------------------------------------------

## Philosophy

Most discussions about AI-assisted software development focus on
**prompt engineering**---how developers communicate with AI.

GatherKit focuses on the other half of the conversation:

> **How can a software project communicate more effectively with AI?**

AI development tools are improving rapidly. Many already integrate with
Git repositories, IDEs, issue trackers, and documentation systems. As
these capabilities mature, much of what GatherKit does today may
eventually become built into our development environments.

Until then, GatherKit provides a lightweight, repeatable workflow for
preparing project context for today's AI assistants.

------------------------------------------------------------------------

## Installation

Clone the repository:

``` bash
git clone https://github.com/magesteve/GatherKit.git
cd GatherKit
chmod +x CodeGather
```

Run directly:

``` bash
./CodeGather
```

Or install it as a command available from anywhere:

``` bash
sudo cp CodeGather /usr/local/bin/CodeGather
```

Then, from the root of any supported Swift project:

``` bash
CodeGather
```

------------------------------------------------------------------------

## Roadmap

-   [x] CodeGather
-   [ ] DocGather
-   [ ] ProjectGather
-   [ ] ChangeGather
-   [ ] ReviewGather
-   [ ] SymbolGather
-   [ ] Homebrew installation
-   [ ] Windows PowerShell support
-   [ ] Linux support

------------------------------------------------------------------------

## Contributing

Ideas, bug reports, feature requests, and pull requests are welcome.

GatherKit is intentionally designed to remain lightweight, portable, and
easy to understand.

------------------------------------------------------------------------

## License

GatherKit is released under the MIT License.

See the LICENSE file for details.

------------------------------------------------------------------------

## Related Article

**Teaching Your Project to Talk to AI**

This article explains the motivation behind GatherKit, how it fits into
modern AI-assisted software development, and why project context may
become as important as prompt engineering.
