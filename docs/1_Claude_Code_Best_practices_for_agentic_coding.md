# Claude Code: Best practices for agentic coding
https://www.anthropic.com/engineering/claude-code-best-practices

https://www.anthropic.com/claude-code

## 1. Customize your setup
Claude Code is an agentic coding assistant that automatically pulls context into prompts. This context gathering consumes time and tokens, but you can optimize it through environment tuning.

### a. Create CLAUDE.md files
CLAUDE.md is a special file that Claude automatically pulls into context when starting a conversation. This makes it an ideal place for documenting:

Common bash commands
Core files and utility functions
Code style guidelines
Testing instructions
Repository etiquette (e.g., branch naming, merge vs. rebase, etc.)
Developer environment setup (e.g., pyenv use, which compilers work)
Any unexpected behaviors or warnings particular to the project
Other information you want Claude to remember
There's no required format for CLAUDE.md files. We recommend keeping them concise and human-readable. For example:

```md
# Bash commands
- npm run build: Build the project
- npm run typecheck: Run the typechecker

# Code style
- Use ES modules (import/export) syntax, not CommonJS (require)
- Destructure imports when possible (eg. import { foo } from 'bar')

# Workflow
- Be sure to typecheck when you're done making a series of code changes
- Prefer running single tests, and not the whole test suite, for performance
```

You can place CLAUDE.md files in several locations:

The root of your repo, or wherever you run claude from (the most common usage). Name it CLAUDE.md and check it into git so that you can share it across sessions and with your team (recommended), or name it CLAUDE.local.md and .gitignore it
Any parent of the directory where you run claude. This is most useful for monorepos, where you might run claude from root/foo, and have CLAUDE.md files in both root/CLAUDE.md and root/foo/CLAUDE.md. Both of these will be pulled into context automatically
Any child of the directory where you run claude. This is the inverse of the above, and in this case, Claude will pull in CLAUDE.md files on demand when you work with files in child directories
Your home folder (~/.claude/CLAUDE.md), which applies it to all your claude sessions
When you run the /init command, Claude will automatically generate a CLAUDE.md for you.

### b. Tune your CLAUDE.md files
Your CLAUDE.md files become part of Claude's prompts, so they should be refined like any frequently used prompt. A common mistake is adding extensive content without iterating on its effectiveness. Take time to experiment and determine what produces the best instruction following from the model.

You can add content to your CLAUDE.md manually or press the # key to give Claude an instruction that it will automatically incorporate into the relevant CLAUDE.md. Many engineers use # frequently to document commands, files, and style guidelines while coding, then include CLAUDE.md changes in commits so team members benefit as well.

At Anthropic, we occasionally run CLAUDE.md files through the prompt improver and often tune instructions (e.g. adding emphasis with "IMPORTANT" or "YOU MUST") to improve adherence.

### c. Curate Claude's list of allowed tools
By default, Claude Code requests permission for any action that might modify your system: file writes, many bash commands, MCP tools, etc. We designed Claude Code with this deliberately conservative approach to prioritize safety. You can customize the allowlist to permit additional tools that you know are safe, or to allow potentially unsafe tools that are easy to undo (e.g., file editing, git commit).

There are four ways to manage allowed tools:

Select "Always allow" when prompted during a session.
Use the /permissions command after starting Claude Code to add or remove tools from the allowlist. For example, you can add Edit to always allow file edits, Bash(git commit:*) to allow git commits, or mcp__puppeteer__puppeteer_navigate to allow navigating with the Puppeteer MCP server.
Manually edit your .claude/settings.json or ~/.claude.json (we recommend checking the former into source control to share with your team).
Use the --allowedTools CLI flag for session-specific permissions.

### d. If using GitHub, install the gh CLI
Claude knows how to use the gh CLI to interact with GitHub for creating issues, opening pull requests, reading comments, and more. Without gh installed, Claude can still use the GitHub API or MCP server (if you have it installed).



## 2. Give Claude more tools
Claude has access to your shell environment, where you can build up sets of convenience scripts and functions for it just like you would for yourself. It can also leverage more complex tools through MCP and REST APIs.

### a. Use Claude with bash tools
Claude Code inherits your bash environment, giving it access to all your tools. While Claude knows common utilities like unix tools and gh, it won't know about your custom bash tools without instructions:

Tell Claude the tool name with usage examples
Tell Claude to run --help to see tool documentation
Document frequently used tools in CLAUDE.md

### b. Use Claude with MCP
Claude Code functions as both an MCP server and client. As a client, it can connect to any number of MCP servers to access their tools in three ways:

In project config (available when running Claude Code in that directory)
In global config (available in all projects)
In a checked-in .mcp.json file (available to anyone working in your codebase). For example, you can add Puppeteer and Sentry servers to your .mcp.json, so that every engineer working on your repo can use these out of the box.
When working with MCP, it can also be helpful to launch Claude with the --mcp-debug flag to help identify configuration issues.

### c. Use custom slash commands
For repeated workflows—debugging loops, log analysis, etc.—store prompt templates in Markdown files within the .claude/commands folder. These become available through the slash commands menu when you type /. You can check these commands into git to make them available for the rest of your team.

Custom slash commands can include the special keyword $ARGUMENTS to pass parameters from command invocation.

For example, here's a slash command that you could use to automatically pull and fix a Github issue:

```md
Please analyze and fix the GitHub issue: $ARGUMENTS.

Follow these steps:

1. Use `gh issue view` to get the issue details
2. Understand the problem described in the issue
3. Search the codebase for relevant files
4. Implement the necessary changes to fix the issue
5. Write and run tests to verify the fix
6. Ensure code passes linting and type checking
7. Create a descriptive commit message
8. Push and create a PR

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.
```

Putting the above content into .claude/commands/fix-github-issue.md makes it available as the /project:fix-github-issue command in Claude Code. You could then for example use /project:fix-github-issue 1234 to have Claude fix issue #1234. Similarly, you can add your own personal commands to the ~/.claude/commands folder for commands you want available in all of your sessions.

## 3. Try common workflows

Effective use of Claude Code often follows predictable patterns. These common workflows have proven successful across different types of projects and development scenarios.

### a. Explore, plan, code, commit

This workflow is ideal for new features or when you're unfamiliar with a codebase:

1. **Explore**: Ask Claude to understand the codebase structure, identify relevant files, and explain existing patterns
2. **Plan**: Have Claude create a step-by-step implementation plan
3. **Code**: Implement the solution incrementally, letting Claude handle the heavy lifting
4. **Commit**: Use Claude to create descriptive commit messages and handle git operations

Example interaction:
```
"Help me understand how authentication works in this codebase, then plan and implement a password reset feature."
```

### b. Write tests, commit; code, iterate, commit

Test-driven development with Claude Code:

1. **Write tests first**: Have Claude create comprehensive test cases
2. **Commit tests**: Commit the failing tests to establish the contract
3. **Implement**: Write code to make tests pass
4. **Iterate**: Refine implementation based on test feedback
5. **Final commit**: Commit the working implementation

This approach ensures your code is well-tested and follows expected behavior patterns.

### c. Write code, screenshot result, iterate

Perfect for UI development and visual debugging:

1. **Initial implementation**: Have Claude write the UI code
2. **Screenshot**: Take a screenshot of the result and share it with Claude
3. **Iterate**: Let Claude suggest improvements based on the visual feedback
4. **Repeat**: Continue until the UI meets your requirements

Claude can analyze screenshots to identify layout issues, styling problems, and suggest improvements.

### d. Safe YOLO mode

When you need rapid prototyping with safety guardrails:

1. **Set boundaries**: Define what Claude should and shouldn't modify
2. **Enable aggressive permissions**: Allow file editing and common operations
3. **Review changes**: Use git to track all changes Claude makes
4. **Iterate quickly**: Let Claude make multiple rapid changes with frequent commits

Use this mode when you trust Claude's judgment and want to move quickly, but always maintain git history for rollbacks.

### e. Codebase Q&A

Use Claude as an intelligent codebase documentation and search tool:

- "Explain how the user authentication flow works"
- "Where is the database schema defined?"
- "Show me all the API endpoints that handle user data"
- "What would happen if I changed this configuration?"

Claude can analyze your entire codebase to provide contextual answers.

### f. Use Claude to interact with git

Claude excels at git operations:

- Creating descriptive commit messages based on changes
- Managing branches and merges
- Resolving merge conflicts
- Analyzing git history and identifying patterns
- Automating git workflows

Example: "Create a feature branch, implement the feature, and create a PR with proper commit messages."

### g. Use Claude to interact with GitHub

With the gh CLI, Claude can handle full GitHub workflows:

- Creating and managing issues
- Opening pull requests with proper descriptions
- Reviewing code and adding comments
- Managing project boards and milestones
- Analyzing repository metrics and activity

### h. Use Claude to work with Jupyter notebooks

Claude has native support for Jupyter notebooks:

- Reading and understanding existing notebooks
- Creating new cells with code and markdown
- Running analysis and visualizations
- Debugging notebook issues
- Converting between notebook formats

## 4. Optimize your workflow

Fine-tuning your interactions with Claude Code can dramatically improve productivity and output quality.

### a. Be specific in your instructions

Vague requests lead to generic solutions. Instead of:
❌ "Make this code better"

Try:
✅ "Optimize this function for performance, add error handling, and improve readability with better variable names"

Specific instructions help Claude understand your priorities and constraints.

### b. Give Claude images

Claude can analyze screenshots, diagrams, and visual content to:

- Debug UI issues by examining screenshots
- Implement designs from mockups
- Analyze charts and diagrams
- Understand visual requirements

Simply drag and drop images into your Claude Code session.

### c. Mention files you want Claude to look at or work on

Help Claude focus by explicitly mentioning relevant files:

```
"Look at src/components/UserProfile.tsx and src/hooks/useAuth.ts, then implement a logout feature"
```

This reduces context-gathering time and ensures Claude examines the right files.

### d. Give Claude URLs

Claude can access URLs to:

- Read documentation and API specs
- Analyze external resources
- Understand requirements from tickets or issues
- Reference examples and tutorials

Include relevant URLs in your requests for better context.

### e. Course correct early and often

Don't let Claude go down the wrong path. If you notice issues:

- Stop and redirect immediately
- Provide specific feedback about what's wrong
- Clarify your requirements
- Ask Claude to explain its approach before continuing

Early course correction saves time and prevents compound errors.

### g. Use checklists and scratchpads for complex workflows

For complex tasks, ask Claude to:

1. Create a checklist of steps
2. Update the checklist as work progresses
3. Use a scratchpad to track important information
4. Document decisions and trade-offs

This helps maintain focus and ensures nothing is forgotten.

### h. Pass data into Claude

Claude can work with various data formats:

- Paste CSV data for analysis
- Share JSON configurations for processing
- Include log files for debugging
- Provide API responses for integration work

Directly including data in your prompts gives Claude concrete examples to work with.

## 5. Use headless mode to automate your infra

Claude Code's headless mode enables automation and integration with existing development infrastructure.

### a. Use Claude for issue triage

Automate issue processing:

```bash
# Example: Automatically analyze and label new issues
claude --headless "Analyze the latest GitHub issues, categorize them by type and priority, and add appropriate labels"
```

Claude can:
- Read issue descriptions and comments
- Classify issues by type (bug, feature, etc.)
- Assess priority and complexity
- Add labels and assign to appropriate team members
- Generate initial investigation notes

### b. Use Claude as a linter

Create custom linting workflows:

```bash
# Check code style and best practices
claude --headless "Review all Python files in src/ directory for code style, security issues, and best practices. Create a report with specific recommendations."
```

Claude can identify:
- Code style violations
- Security vulnerabilities
- Performance anti-patterns
- Architectural inconsistencies
- Documentation gaps

## 6. Uplevel with multi-Claude workflows

Advanced patterns that use multiple Claude sessions for complex workflows.

### a. Have one Claude write code; use another Claude to verify

Implement a review process:

1. **Writer Claude**: Implements features and writes code
2. **Reviewer Claude**: Reviews code for issues, suggests improvements
3. **Integration**: Combine feedback to create robust solutions

This mimics pair programming and catches issues that single-session development might miss.

### b. Have multiple checkouts of your repo

Work on multiple features simultaneously:

- Each Claude session works in its own repository checkout
- Parallel development on different features
- Independent testing and validation
- Coordinated integration when ready

### c. Use git worktrees

Leverage git worktrees for efficient multi-session development:

```bash
# Create worktrees for different features
git worktree add ../feature-auth feature/authentication
git worktree add ../feature-ui feature/ui-redesign

# Run Claude in each worktree
cd ../feature-auth && claude
cd ../feature-ui && claude
```

This allows multiple Claude sessions to work on different branches simultaneously.

### d. Use headless mode with a custom harness

Build sophisticated automation:

```python
# Example: Custom orchestration script
import subprocess
import json

def run_claude_task(task_description, context_files=None):
    cmd = ["claude", "--headless", task_description]
    if context_files:
        cmd.extend(["--files"] + context_files)
    
    result = subprocess.run(cmd, capture_output=True, text=True)
    return json.loads(result.stdout)

# Orchestrate complex workflows
analysis = run_claude_task("Analyze codebase for refactoring opportunities")
implementation = run_claude_task(f"Implement refactoring: {analysis['recommendations']}")
testing = run_claude_task("Create tests for refactored code", implementation['modified_files'])
```

This enables sophisticated automation workflows tailored to your specific needs.

## Acknowledgements

These best practices have been developed through extensive use of Claude Code across various projects, languages, and development environments. The patterns described here represent collective wisdom from both Anthropic's internal teams and the broader Claude Code community.

Special thanks to the engineering teams who have shared their workflows and helped refine these recommendations through practical application.