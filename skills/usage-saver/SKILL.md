---
name: "usage-saver"
description: "Make Claude usage last longer: fresh chats, right model, fewer connectors, lean context, caveman/RTK/ccusage. Use in long chats, near plan limits, or when asked how to use less."
---

# Save usage

Every token in a conversation is sent again on every turn. Most usage is input (history, file reads, tool outputs, connector tool definitions), not Claude's replies. Shrink what Claude reads first; shorter replies help a little.

## Biggest levers
1. Fresh chat per task. When a task is done, suggest a new chat and give a 5 line summary to paste in.
2. Right model: strong model for planning, hard bugs, reviews; Sonnet or Haiku for routine edits, summaries, renames. Lower effort for simple asks.
3. Turn off unused connectors (Gmail, Drive, Shopify, 21st...). Each one adds tool definitions to every turn.
4. Keep project instructions and preferences short; put rare detail in files read on demand.
5. Attach a file once and refer to it; never paste the same log or code twice.

## While working
- Search narrow before wide; read only the part of a file you need.
- Big outputs (logs, JSON, test runs) go to a file; read back only the lines that matter.
- Don't repeat back code or output the user can already see.
- In Claude Code: /compact or /clear between unrelated tasks; write progress to a log so a fresh session can resume.

## Tools
- caveman (JuliusBrussee/caveman, MIT/Apache): short replies, shrinks tool output, auto model picking, cache warming. Claude Code: `/plugin marketplace add JuliusBrussee/caveman` then `/plugin install caveman@caveman`. claude.ai: Customize > Plugins > Add marketplace `JuliusBrussee/caveman`; in chat type `/caveman`. Short replies alone save about 20 to 30% of output, a small part of the bill; the input parts matter more.
- RTK (rtk-ai/rtk): filters shell output in Claude Code. Use it or caveman's output shrinking, not both.
- ccusage: `npx ccusage@latest` shows where Claude Code tokens went.
- claude-task-master: splits big builds into short sessions.

When the user asks how to cut usage, lead with the biggest levers, then tools, and be honest about how much each saves.