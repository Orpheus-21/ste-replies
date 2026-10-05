# ste-replies

`ste-replies` is a skill for Claude Code. The skill makes Claude write its replies in ASD-STE100 Simplified Technical English.

## What it does

The skill gives Claude a set of writing rules. The rules limit sentence length, word choice, and verb forms. The goal is that no sentence has two readings.

The skill applies to every reply. It applies most when the user builds, debugs, or plans something. Code, commands, and error text stay exact.

## Requirements

- Claude Code with support for skills.
- Any operating system that runs Claude Code.

## Install

1. Create the skill directory:

   ```
   mkdir -p ~/.claude/skills/ste-replies
   ```

2. Copy the skill file into the directory:

   ```
   cp SKILL.md ~/.claude/skills/ste-replies/
   ```

3. Start a new Claude Code session. Claude Code reads the skill list at the start of a session.

## Usage

Claude loads the skill when the description in `SKILL.md` matches the task. The description asks for the skill on every reply.

To load the skill at the start of every session, add an instruction to `~/.claude/CLAUDE.md`. Example:

```
At the start of each session, load the `ste-replies` skill with the Skill tool.
```

## Configuration

The skill has no settings. To change a rule, edit `SKILL.md`.

## How it works

The repo holds one file, `SKILL.md`. The file has two parts:

- The front matter. The `name` and `description` fields tell Claude Code when to load the skill.
- The body. The body lists the rules in these sections: core rules, sentence rules, word rules, verb rules, ambiguity control, code and commands, and tone.

The limits in the rules are:

- Procedure sentences have 20 words or fewer.
- Descriptive sentences have 25 words or fewer.
- Paragraphs have 6 sentences or fewer.
- Noun clusters have 3 words or fewer.

The rules follow the spirit of ASD-STE100. They are not the full specification. The full specification and its dictionary come from the ASD-STE100 maintainers.
