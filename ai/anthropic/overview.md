# Anthropic

- Paid plan 40 NZD/month
- Apps for mac and mobile

## Pricing

Addons

- Claude web search: $10/1k searches + whatever tokens burned on creating the
  reqs and processing the responses
- Code execution: run python in a sandbox $0.05/hr/container

## Claude code

?? Claude code vs whatever openai have?

```bash
brew install --cask claude-code
```

- Claude Pro is required to connect to Claude Code
    - but there are claude code only plans (17 usd/mon
- Has extensions for IDEs as well as the CLI client (also a Slack integration)

## Claude apps

???

## Skills

- Think of them as "expertise packages" that Claude can discover and load
  dynamically

> Claude can now use Skills to improve how it performs specific tasks. Skills
> are folders that include instructions, scripts, and resources that Claude can
> load when needed.

Custom Skills let you package domain expertise and organizational knowledge.
They're available across Claude's products: create them in Claude Code, upload
them via the API, or add them in claude.ai settings.

Claude will only access a skill when it's relevant to the task at hand. When
used, skills make Claude better at specialized tasks like working with Excel or
following your organization's brand guidelines.

> You've already seen Skills at work in Claude apps, where Claude uses them to
> create files like spreadsheets and presentations. Now, you can build your own
> skills and use them across Claude apps, Claude Code, and our API.

Skills can include executable code for tasks where traditional programming is
more reliable than token generation.

A folder containing at least `SKILL.md` and whatever other resources you need

You can upload a skill to the Claude web app Does it just get put in the context
window?

https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

- The agent runs a "VM" which contains all the skills directories as well as any
  required coding stacks e.g. python, node etc.
- The `name` and `description` fields from each `SKILL.md` are pre-loaded into
  the agent's system prompt.
    > This metadata is the first level of progressive disclosure: it provides
    > just enough information for Claude to know when each skill should be used
    > without loading all of it into context. The actual body of this file is
    > the second level of detail. If Claude thinks the skill is relevant to the
    > current task, it will load the skill by reading its full SKILL.md into
    > context.
    >
    > s skills grow in complexity, they may contain too much context to fit into
    > a single SKILL.md, or context that's relevant only in specific scenarios.
    > In these cases, skills can bundle additional files within the skill
    > directory and reference them by name from SKILL.md. These additional
    > linked files are the third level (and beyond) of detail, which Claude can
    > choose to navigate and discover only as needed.
- Skills can also include code for Claude to execute as tools at its discretion.
- Pay special attention to the name and description of your skill. Claude will
  use these when deciding whether to trigger the skill in response to its
  current task.

> As you work on a task with Claude, ask Claude to capture its successful
> approaches and common mistakes into reusable context and code within a skill.
> If it goes off track when using a skill to complete a task, ask it to
> self-reflect on what went wrong. This process will help you discover what
> context Claude actually needs, instead of trying to anticipate it upfront.

What exactly is the agent's VM?

> Agent Skills, which we often refer to simply as Skills, can now be added to
> Messages API requests and the new /v1/skills endpoint gives developers
> programmatic control over custom skill versioning and management. Skills
> require the Code Execution Tool beta, which provides the secure environment
> they need to run.

You can also manually install skills by adding them to ~/.claude/skills.

Keep in mind, this feature gives Claude access to execute code. While powerful,
it means being mindful about which skills you use

Agent Skills: organized folders of instructions, scripts, and resources that
agents can discover and load dynamically to perform better at specific tasks.

Building a skill for an agent is like putting together an onboarding guide for a
new hire.

Claude Code supports only Custom Skills.

The exact runtime environment available to your skill depends on the product
surface where you use it.

https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview#runtime-environment-constraints

Claude.ai: Varying network access: Depending on user/admin settings, Skills may
have full, partial, or no network access. For more details, see the Create and
Edit Files support article. Claude API: No network access: Skills cannot make
external API calls or access the internet No runtime package installation: Only
pre-installed packages are available. You cannot install new packages during
execution. Pre-configured dependencies only: Check the code execution tool
documentation for the list of available packages Claude Code: Full network
access: Skills have the same network access as any other program on the user's
computer Global package installation discouraged: Skills should only install
packages locally in order to avoid interfering with the user's computer Plan
your Skills to work within these constraints.

### Claude's VM

> Claude operates in a virtual machine with filesystem access, allowing Skills
> to exist as directories containing instructions, executable code, and
> reference materials, organized like an onboarding guide you'd create for a new
> team member.

> Skills run in a code execution environment where Claude has filesystem access,
> bash commands, and code execution capabilities. Think of it like this: Skills
> exist as directories on a virtual machine, and Claude interacts with them
> using the same bash commands you'd use to navigate files on your computer.

### Skills vs MCP

???

## Claude API
