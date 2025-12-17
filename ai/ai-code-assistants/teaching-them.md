
## Configuring copilot

You can create markdown files that are automatically added to every prompt or added to appropriate prompts (determined by file path)

The complete set of instructions will be automatically added to requests that you submit to Copilot in the context of that repository.


> [!TIP]
> You can ask Copilot to help you write all these files

Categories of configuration

1. Personal instructions
    - Highest level priority when combining with other instructions
    - https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-personal-instructions
    - Added through VSCode, saved somewhere in VSCode config
    - Conceptually just one document of personal instructions
1. Repository instructions
    - https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions
    - Types
        1. Repository wide instruction files
            - `.github/copilot-instructions.md`
        1. Path specific custom instructions files
            - `.github/instructions/NAME.instructions.md`
            - can be scope limited to certain file patterns
        1. Prompt files
            - `.github/prompts`
        1. Agent instructions
            - `AGENTS.md`
                - designed as a "README for agents" so you don't clutter README with non-human stuff
                - uses format: https://github.com/agentsmd/agents.md
                - https://agents.md/
                - can be anywhere in the directory tree
                - the nearest one will take precedence when the agent is working
                    - ??? how determined
            - or single `CLAUDE.md` or `GEMINI.md` file in repo root
1. Organisation instructions
    - Lowest level priority
    - Added through Github site repo settings
    - https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-organization-instructions
    - Conceptually just one document of personal instructions


- Copilot can be told to use other editor config files (Windsurf, Cursor) to find MCP servers
- Copilot has experimental support to look for skills in `.claude/skills`
- Copilot out of the box will only look for `AGENTS.md` in root, but you can tell it to find AGENTS.md in other dirs

## Other approaches: cursor and windsurf

- https://windsurf.com/compare/windsurf-vs-github-copilot
- https://windsurf.com/compare/windsurf-vs-cursor
- https://cursor.com/docs/context/rules

- All of these rules type things are just ways of crafting some custom instructions to auto add to your context window
- They differ in how convenient they are but you could achieve it all manually by just typing more into your prompt
- They are all syntactic sugar/QoL features

> Cursor can load rules from Claude's skills and plugins system. These imported rules are always applied as agent-decided rules, meaning Cursor determines when they are relevant based on context.

- Cursor rules are a more fancy version of AGENTS.md
- Cursor rules overlap with skills a lot

## cross platform ways to give agents context

Q: is multiple AGENTS.md files which references scripts at top level the most cross-platform way to give context?

what about path scoped context? is the cross-platform way to do that?

what about prompts files?

You want these instructions to be as focused as possible in each context window

VS Code **is** the execution context for its agents - it acts akin to a VM

## How does copilot find AND remember how to run tests in a repo

- How does it figure htis out?
- How does it remember it? how is it stored in context window?

There is a `execute.runTests` and `execute.testFailure` tools built-in to VS code