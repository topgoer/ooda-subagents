# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

OODA Subagents is a strategic AI agent framework that implements the military OODA (Observe-Orient-Decide-Act) decision-making loop for systematic problem-solving in software development. This provides four specialized Claude Code agents that work sequentially through complex problems with military-grade strategic thinking.

## Architecture

The system follows a linear pipeline architecture where each agent hands off to the next:

1. **Observe** (`/.claude/agents/observe.md`) → Gathers comprehensive information without interpretation
2. **Orient** (`/.claude/agents/orient.md`) → Analyzes and contextualizes findings using domain knowledge  
3. **Decide** (`/.claude/agents/decide.md`) → Evaluates options and provides justified recommendations
4. **Act** (`/.claude/agents/act.md`) → Implements the chosen approach with precision

## Installation and Usage

This framework is designed to be installed as a git submodule or copied into other projects:

```bash
# As git submodule
git submodule add https://github.com/al3rez/ooda-subagents.git .claude

# Manual installation
# Copy the agents/ directory to target project's .claude/ directory
```

## Agent Tool Specialization

- **Observe**: Read, Grep, Glob, LS, Bash, WebSearch, WebFetch (broad information gathering)
- **Orient**: Read, Grep, Glob, WebSearch, WebFetch (analysis and synthesis)
- **Decide**: Read, WebSearch, WebFetch (research and evaluation)
- **Act**: Read, Write, Edit, MultiEdit, Bash, Grep, Glob, LS, TodoWrite (implementation)

## Key Patterns

**Sequential Processing**: Each agent must complete its phase before the next begins. Respect agent boundaries - don't make decisions in Observe phase, don't implement in Decide phase.

**Military Precision**: Be systematic, thorough, and strategic. Use cross-referencing in Observe, apply domain knowledge in Orient, generate 3+ options in Decide, and follow conventions precisely in Act.

**Progressive Tool Narrowing**: Tools become more focused as you move through the pipeline - from broad information gathering to specific implementation tools.

## Development Notes

- No build, test, or lint commands required (pure agent configuration)
- Self-contained framework with no external dependencies
- Works with any codebase size and technology stack
- Built by AstroMVP for AI-first product development

## Visual Reference

`ooda.png` demonstrates the complete OODA loop workflow in action, showing the systematic progression from observation through implementation.