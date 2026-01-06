---
title: "Agent Skills: The Missing Layer"
date: 2025-01-06
draft: false
summary: "How Agent Skills help AI stay professional and controllable without blowing up the context window."
lang: "en"
translation: "/blogs/2026-01-agent-skills-cn/"
translation_label: "中文版"
---

<img src="/assets/data/2026-01-agent-skills-cn.png" alt="Agent Skills Architecture" style="max-width: 100%; width: 720px; display: block; margin: 0 auto 2rem auto; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">

Agent Skills have been picking up serious momentum lately. Claude led the charge, and now mainstream tools like VS Code and Cursor are jumping on board. 

**In this post, I'll share what I've learned about Agent Skills.**

Anthropic introduced Agent Skills in October 2025, and by December, it became an open standard. In just a few months, what started as an experimental feature grew into a universal framework for AI Agents. But why would something that looks like glorified documentation get the whole industry excited? Simple: it solves a real problem. How to make AI more capable and reliable without stuffing the context window until it breaks.

## 1. What Are Agent Skills?

Think of an Agent Skill as an instruction manual for LLMs. It has three basic components:

- Name: A unique identifier so the model knows what to look for
- Description: A quick summary that helps the model decide whether to use it
- Content: The actual logic, including workflows, constraints, examples, and output formats

There are also two powerful extensions:

- Reference
    - What it is: On-demand knowledge
    - How it works: Loads external docs only when needed
    - Why it matters: Enables modular, branching workflows instead of linear execution

- Script
    - What it is: A black-box execution unit
    - How it works: The model calls it; the script runs in a sandbox
    - Why it matters: Almost zero token cost. The model just gets the result

**What makes Reference special is its ability to define trigger conditions, turning simple workflows into composable, reusable pipelines.**

**Script, on the other hand, keeps heavy computation out of the context entirely. The model only sees inputs and outputs, not the code.**

## 2. The Secret Sauce: Progressive Disclosure on Context

Agent Skills avoid context overload through smart, staged loading:

1. Static awareness: Only names and descriptions are loaded upfront. This uses minimal tokens to expose to model to more skills.
2. Dynamic activation: Full content gets injected only when a task actually needs to use the skill.
3. On-demand expansion: Reference and Script will be leveraged as needed. Making the model to expand to more possibilities.

## 3. Agent Skills + MCP = The Full Picture

In practice, Agent Skills work hand-in-hand with MCP (Model Context Protocol):

- MCP handles the fixed workflows and tools, e.g. how to connect to GitHub, reading from databases, etc.
- Agent Skills handle the processing logic, output formats, automation triggers among related skills and scripts.

**Put simply: MCP moves the data and information, Agent Skills direct the action. MCP is like a polished toolkit; Agent Skills are more like a flexible playbook, defining workflows, conditionals, and business rules for the model to follow.**

## Looking Ahead: What's Next for Agents (Early 2026)

Agent Skills are just the beginning. As the ecosystem matures, three areas stand out:

1. **Context and Memory**: Today's agents are still boxed in by context limits. We need smarter memory systems, deciding what to keep, what to forget, and how to balance speed with accuracy. This includes long-term state, versioning, and retrieval strategies.

2. **Agent-to-Agent Protocols**: One agent can only do so much. When multiple agents collaborate, we need stable communication, conflict resolution, and task coordination. Think of it as HTTP for AI, a standard A2A protocol.

3. **Self-Evolving Skills**: The most exciting frontier is agents that learn on the job, creating new skills, refining old ones, and combining them into more powerful capabilities. That's when agents stop being tools and start becoming true collaborators.

---

*These are my early thoughts on Agent Skills. Happy to hear yours.*
