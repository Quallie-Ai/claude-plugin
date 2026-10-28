# Quallie.Ai plugin for Claude

Build qualitative research reports with Claude, together. Claude works from the
interviews, clips and analyses in your Quallie.Ai project and writes the report
straight into Quallie.Ai, where your team can read, edit and share it.

## What it does

Claude does not write the whole report in one go. It works with you through four
checkpoints, and waits for your answer at each one:

1. **Intake.** Claude asks about the project, the audience and the kind of report you need.
2. **Findings.** Claude explores your Quallie.Ai interviews with you and agrees the key findings.
3. **Outline.** Claude proposes the pages and sections. Nothing is written until you approve it.
4. **Build page by page.** Claude builds one page, shows it to you, and asks before starting the next.

Along the way Claude sets up the report's look: it starts from one of your
workspace's report templates if you have one, or proposes colours and fonts
from a brand example you share.

## Requirements

- A Quallie.Ai account.
- The Quallie.Ai connector added to Claude, and signed in to your Quallie.Ai account.
- MCP access allowed for the project in your Quallie.Ai workspace settings.

## Install

The public repository for this plugin is `quallie-ai/claude-plugin`. The
commands below use that name.

**Claude Code**

```
/plugin marketplace add quallie-ai/claude-plugin
/plugin install quallie@quallie
```

**Cowork and claude.ai**

Open Customize, then Plugins, then Add marketplace, and enter the repository
above. Then install the Quallie.Ai plugin from it.

## Usage

Run `/quallie:build-report`, or just ask Claude to build a report from one of
your Quallie.Ai projects.

## Your logo

Claude cannot upload files to Quallie.Ai. Upload your logo yourself in the
Quallie.Ai app, in the report's theme panel.

## Licence

MIT. See [LICENSE](LICENSE). Copyright (c) 2026 Quallie.Ai Ltd.
