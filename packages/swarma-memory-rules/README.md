# swarma-memory-rules

Context package with the memory rules for every Swarma platform role: when to read memory, where to write, and what never goes in. `swarma-base` requires it, so every role profile gets it.

It requires the `memory` skill from [relux-works/swarma-memory](https://github.com/relux-works/swarma-memory) in `full` mode, so the profile installs both the skill and the `memory` CLI. The CLI install arrives with Curator's install-skill-with-CLI support. Until then the profile delivers the skill text only. There is no fallback to a global install.

This package ships no runtime hooks. Memory hooks are delivered by the operator, pinned by digest.

## Contents

- `context/INSTRUCTIONS_MEMORY.md`: the rules.
- `agent-context.json`: the package manifest.

## Enabling memory for an agent

Installing the profile is only the first step. An agent can write to memory once all of these are done:

1. The `memory` CLI is available from the profile.
2. The agent has its own memory home and signing key. A home belongs to one running process and is never shared. A separate home does not allow two concurrent sessions of the same identity; the identity's one-live rule governs that.
3. The owner of each space has registered the agent's key and granted it reader and writer roles on its agent space and the project space, and reader on the platform space.
4. The agent has added each space with the genesis digest it received over a trusted channel.
5. `memory sync` and `memory check` report zero diagnostics.

Until step 3 is done the agent is "installed, not enrolled". The agent can keep working without memory.
