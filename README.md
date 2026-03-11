# 🚀 SuperCrew

> AI-driven feature lifecycle management for Claude Code

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blue.svg)](https://claude.ai/claude-code)
[![Version](https://img.shields.io/badge/Version-Latest-orange.svg)](https://github.com/steins-z/supercrew)

**SuperCrew** transforms how you build features with Claude Code. It provides a structured, AI-driven workflow that tracks features through their entire lifecycle — from initial requirements gathering through design, implementation, and shipping — using intelligent `.supercrew/tasks/` directories.

---

## ✨ Why SuperCrew?

🎯 **Structured Feature Development**
- Stop losing track of feature requirements and progress
- Follow a proven `todo → doing → ready-to-ship → shipped` lifecycle
- Maintain clear documentation throughout development

🤖 **AI-Native Workflow**
- Claude automatically detects when to activate SuperCrew skills
- Proactive assistance based on your current context and git branch
- No manual skill invocation needed — just describe what you want

👥 **Team Collaboration Ready**
- User-namespaced git branches prevent conflicts
- Standardized file structure for consistent handoffs
- Progress tracking visible to all team members

📊 **Comprehensive Tracking**
- Real-time status dashboards for all features
- Chronological development logs
- Automatic sync between design iterations and implementation

---

## 🚀 Quick Start

### Prerequisites
- Claude Code IDE
- Git repository

### Installation

1. **Register the SuperCrew marketplace and install:**
   ```bash
   /plugin marketplace add steins-z/supercrew
   /plugin install supercrew@supercrew
   ```

2. **Verify installation:**
   Start a new Claude session. SuperCrew will automatically announce when it's active and show a summary of your features.

3. **Create your first feature:**
   ```
   "I want to add dark mode support"
   ```
   SuperCrew will automatically create the feature structure and branch for you!

### Development Installation

For local development or testing:
```bash
/plugin marketplace add /absolute/path/to/supercrew
/plugin install supercrew@supercrew
```

---

## 🔧 How It Works

SuperCrew seamlessly integrates with your Claude Code workflow through smart automation:

🎯 **Session Start Intelligence**

SuperCrew injects context at session start via a `SessionStart` hook that:
- 🔍 Embeds skill routing guidance directly into session context
- 📁 Scans `.supercrew/tasks/` for tracked features
- 🌿 Auto-loads the active feature based on your current git branch
- 📊 Provides a summary table of all features and their statuses

### 🌿 Branch Naming Convention

SuperCrew uses user-namespaced branches for better team collaboration:

| Stage | Branch Pattern | Example |
|-------|----------------|---------|
| Backlog | `user/<username>/backlog-<feature-id>` | `user/steins-z/backlog-dark-mode` |
| Active work | `user/<username>/<feature-id>` | `user/steins-z/dark-mode` |

Username is derived from `git config user.name`, converted to lowercase with hyphens (e.g., "Steins Z" → `steins-z`).

### 🤖 Proactive Skill Triggering

Skills activate using the **1% rule**: if there is even a 1% chance a skill applies, Claude invokes it before responding — including before clarifying questions. When a skill fires, Claude announces it:

> *"Using supercrew:create-task to set up the new feature directory..."*

✨ This means you never need to call skills manually. Just describe what you want.

---

## 📋 The Feature Lifecycle

```
todo → doing → ready-to-ship → shipped
  ↑      │
  └──────┘
```

Each feature lives in `.supercrew/tasks/<id>/` with structured documentation:

| File | 📝 Contents | ⏰ When Created |
|------|-------------|-----------------|
| `meta.yaml` | id, title, status, priority, owner | Feature creation (`todo`) |
| `prd.md` | background, requirements, out of scope | Feature creation (`todo`) |
| `dev-design.md` | design decisions, architecture, implementation notes | Work starts (`doing`) |
| `dev-plan.md` | task checklist with progress tracking | Work starts (`doing`) |
| `dev-log.md` | chronological development log | Work starts (`doing`) |

---

## 🛠️ Skills

| Skill | 🎯 When it activates |
|-------|---------------------|
| `create-task` | User wants to create a new feature — creates backlog branch, `meta.yaml`, and `prd.md` with real content |
| `do-task` | Status transitions — starting work, marking done, shipping. Creates `dev-*` files on `todo → doing` |
| `sync-supercrew` | Syncing design iterations, task updates, and progress logging during development |

---

## 💻 Commands

| Command | 📖 Description |
|---------|----------------|
| `/supercrew:create` | Create a new feature in the backlog |
| `/supercrew:start <id>` | Start working on a feature (creates work branch and dev-* files) |
| `/supercrew:sync` | Sync all .supercrew updates (design, plan, log) |
| `/supercrew:status` | Show all features in a status table |

---

## 💡 Example Usage

Just talk naturally — SuperCrew skills activate automatically based on context.

### 🆕 Creating a Feature
```
"I want to add dark mode support"
"Let's create a new feature for user authentication"
"Start tracking a caching layer feature"
```

### 🚀 Starting Work on a Feature
```
"/supercrew:start dark-mode"
"Start working on the auth feature"
"Begin implementation of dark-mode"
```

### 🔄 During Implementation
```
"I finished the theme toggle component"
"Update the plan - task 3 is done"
"Sync my progress"
"/supercrew:sync"
```

### 📈 Status Updates
```
"This feature is ready to ship"
"Ship it!"
"We need to go back to requirements"
```

### 📊 Checking Status
```
"/supercrew:status"
"Show me all features"
"What's the status of our features?"
```

---

## 📂 File Structure

```
.supercrew/
└── features/
    └── <feature-id>/
        ├── meta.yaml        # Feature metadata (always present)
        ├── prd.md           # Product requirements (always present)
        ├── dev-design.md    # Technical design (created when work starts)
        ├── dev-plan.md      # Task breakdown (created when work starts)
        └── dev-log.md       # Development log (created when work starts)
```

---

## 🔄 Updating

Keep SuperCrew current with the latest features and improvements:

```bash
/plugin update supercrew
```

---

## 🤝 Contributing

We welcome contributions to SuperCrew! Here's how you can help:

### 🐛 Bug Reports & Feature Requests
- Open an issue on [GitHub](https://github.com/steins-z/supercrew/issues)
- Provide clear reproduction steps for bugs
- Describe your use case for feature requests

### 💻 Development Setup
1. Fork the repository
2. Clone your fork locally
3. Install for development:
   ```bash
   /plugin marketplace add /path/to/your/supercrew-fork
   /plugin install supercrew@supercrew
   ```
4. Make your changes
5. Test thoroughly with real Claude Code sessions
6. Submit a pull request

### 📋 Development Guidelines
- Follow the existing code style
- Add tests for new features
- Update documentation for any changes
- Keep commits focused and descriptive

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<sub>**Last updated:** March 12, 2026 (Date stamp: 03120201)</sub>
