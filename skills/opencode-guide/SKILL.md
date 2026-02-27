---
name: opencode-guide
description: A skill for learning and using OpenCode, an open-source AI coding agent. Use this skill whenever the user wants to learn how to install, configure, or use OpenCode for coding tasks.
---

# OpenCode Guide

A comprehensive guide for using OpenCode, an open-source AI coding agent that provides terminal interface, desktop application, and IDE extensions.

## Features
- Installation instructions for different platforms
- Configuration guidance
- Usage examples and best practices
- Troubleshooting tips

## Installation

### Prerequisites
- A modern terminal emulator (WezTerm, Alacritty, Ghostty, Kitty)
- API key from your preferred LLM provider

### Installation Methods

**Using Installation Script:**
```bash
curl -fsSL https://opencode.ai/install | bash
```

**Using Node.js:**
```bash
npm install -g opencode-ai
# or
bun install -g opencode-ai
# or
pnpm install -g opencode-ai
# or
yarn global add opencode-ai
```

**Using Homebrew (macOS and Linux):**
```bash
brew install anomalyco/tap/opencode
```

**Using Chocolatey (Windows):**
```bash
choco install opencode
```

**Using Scoop (Windows):**
```bash
scoop install opencode
```

**Using Mise:**
```bash
mise use -g github:anomalyco/opencode
```

**Using Docker:**
```bash
docker run -it --rm ghcr.io/anomalyco/opencode
```

## Configuration

OpenCode can be configured using JSON configuration files. The configuration priority order is:
1. Remote configuration (from .well-known/opencode)
2. Global configuration (~/.config/opencode/opencode.json)
3. Custom configuration (OPENCODE_CONFIG environment variable)
4. Project configuration (opencode.json in project root)
5. .opencode directory
6. Inline configuration (OPENCODE_CONFIG_CONTENT environment variable)

### Basic Configuration Example
```json
{
  "$schema": "https://opencode.ai/config.json",
  "theme": "opencode",
  "model": "anthropic/claude-sonnet-4-5",
  "autoupdate": true
}
```

### TUI Configuration
```json
{
  "tui": {
    "scroll_speed": 3,
    "scroll_acceleration": {
      "enabled": true
    },
    "diff_style": "auto"
  }
}
```

### Server Configuration
```json
{
  "server": {
    "port": 4096,
    "hostname": "0.0.0.0",
    "mdns": true,
    "mdnsDomain": "myproject.local",
    "cors": ["http://localhost:5173"]
  }
}
```

## Initialization

1. Navigate to your project directory:
   ```bash
   cd /path/to/project
   ```

2. Run OpenCode:
   ```bash
   opencode
   ```

3. Initialize OpenCode for your project:
   ```
   /init
   ```

This will analyze your project and create an AGENTS.md file in the project root to help OpenCode understand the project structure and coding standards.

## Usage

### Asking Questions
You can ask OpenCode to explain parts of your codebase:
```
How is authentication handled in @packages/functions/src/api/index.ts
```

### Adding Features

#### Creating a Plan
1. Switch to plan mode using Tab key
2. Describe the feature you want to add:
   ```
   When a user deletes a note, we'd like to flag it as deleted in the database. Then create a screen that shows all the recently deleted notes. From this screen, the user can undelete a note or permanently delete it.
   ```

#### Building the Feature
1. Switch back to build mode using Tab key
2. Ask OpenCode to implement the feature:
   ```
   Sounds good! Go ahead and make the changes.
   ```

### Direct Modifications
For simple changes, you can directly ask OpenCode to make modifications:
```
We need to add authentication to the /settings route. Take a look at how this is handled in the /notes route in @packages/functions/src/notes.ts and implement the same logic in @packages/functions/src/settings.ts
```

### Undoing Changes
If you're not satisfied with the changes, you can undo them:
```
/undo
```

You can also redo changes:
```
/redo
```

### Sharing
You can share your conversation with your team:
```
/share
```

## User Consent
Before performing any operations, this skill will ask for your explicit consent. This includes:
- Running commands
- Reading project files
- Making changes to the project

## Examples

**Example 1: Getting Started**
Input: "How do I install OpenCode on Windows?"
Output: "You can install OpenCode on Windows using Chocolatey: `choco install opencode`, Scoop: `scoop install opencode`, or NPM: `npm install -g opencode-ai`."

**Example 2: Configuration**
Input: "How do I configure OpenCode to use a specific model?"
Output: "You can configure the model in your opencode.json file: `{ "model": "anthropic/claude-sonnet-4-5" }`. This can be placed in your project root or global config directory."

**Example 3: Usage**
Input: "How do I ask OpenCode to explain a part of my code?"
Output: "You can simply ask: `How is authentication handled in @packages/functions/src/api/index.ts` and OpenCode will analyze the file and provide an explanation."

## Best Practices
- Provide clear and specific instructions
- Use plan mode for complex features
- Review the plan before implementing
- Use /undo if you're not satisfied with changes
- Share conversations with your team when appropriate
- Keep your configuration files up to date

## Troubleshooting
- **API Key Issues**: Make sure your API key is correctly configured and has sufficient credits
- **Installation Problems**: Check the official documentation for platform-specific issues
- **Performance Issues**: Consider using a more powerful model or optimizing your prompts
- **Configuration Conflicts**: Check the priority order of configuration files to resolve conflicts
