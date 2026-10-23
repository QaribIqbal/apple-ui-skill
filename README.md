# Apple UI skill (apple-hig-bible)

A design skill for AI coding agents. It makes the agent design and build UI the Apple way, on any platform (iOS, Android, Flutter, React/web, SwiftUI):

- the full Apple Human Interface Guidelines condensed into a rulebook (all 158 pages, with links to the live pages);
- motion and glass recipes: spring press feedback, transitions, a Wallet-style card stack, translucent floating bars, sheets and undo toasts.

It does **not** impose colours, fonts or layouts. Each app keeps its own design; the skill makes it follow Apple's rules and feel native.

Repo: https://github.com/QaribIqbal/apple-ui-skill

## What's inside

```
apple-hig-bible/
  SKILL.md                         entry point: when to use it, order of authority, quick checklist, topic map
  references/motion-and-glass.md   how to build the animations and translucent bars
  references/getting-started.md    design principles, per-platform notes
  references/foundations.md        accessibility, color, typography, layout, materials, motion, writing...
  references/patterns.md           onboarding, loading, feedback, modality, search, settings...
  references/components-core.md    lists, tabs, sheets, pickers, text fields, toggles...
  references/components-actions-system.md   buttons, menus, toolbars, widgets, notifications...
  references/inputs.md             gestures, keyboards, pointers...
  references/technologies.md       Apple Pay, Sign in with Apple, Maps, Siri...
```

## Install from this repo (recommended)

Point an agent at this repo, or run:

```bash
git clone --depth 1 https://github.com/QaribIqbal/apple-ui-skill.git /tmp/apple-ui-skill

# Claude Code (global)
cp -R /tmp/apple-ui-skill/apple-hig-bible ~/.claude/skills/

# Cursor (global, this machine)
mkdir -p ~/.cursor/skills && cp -R /tmp/apple-ui-skill/apple-hig-bible ~/.cursor/skills/

# OpenAI Codex CLI (global)
mkdir -p ~/.codex/skills && cp -R /tmp/apple-ui-skill/apple-hig-bible ~/.codex/skills/
```

One-liner for Claude Code:

```bash
git clone --depth 1 https://github.com/QaribIqbal/apple-ui-skill.git /tmp/apple-ui-skill && cp -R /tmp/apple-ui-skill/apple-hig-bible ~/.claude/skills/
```

### Per-project

```bash
git clone --depth 1 https://github.com/QaribIqbal/apple-ui-skill.git /tmp/apple-ui-skill
cp -R /tmp/apple-ui-skill/apple-hig-bible <project>/.claude/skills/   # or .cursor/skills/
```

For Cursor / Windsurf / Cline without a skills folder, copy to `docs/apple-hig-bible/` and add to the agent rules file:

> For any UI design or build work, read `docs/apple-hig-bible/SKILL.md` first and follow it. Open the reference files its topic map points to.

## Using it

Say "use the apple-hig-bible skill" (or just ask for something Apple-like or minimal). Give the agent your app's own colours and fonts. It applies the HIG rules and the motion and glass recipes on top of them.

Source of truth: https://developer.apple.com/design/human-interface-guidelines
