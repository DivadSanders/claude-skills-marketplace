# Claude Skills Marketplace
 
**Production-grade Claude skills for founders and builders.**
 
Drop any skill into Claude's context and it instantly gains domain expertise. Get sharper output, less back-and-forth, no generic responses.
 
---
 
## What's a Claude Skill?
 
A skill is a markdown file that loads expert-level behavior into Claude. Think of it as a system prompt written by a specialist, instead of an assistant.
 
**Without a skill:** Claude gives you surface-level advice on writing a landing page.  
**With the copywriting skill:** Claude asks the right questions, follows conversion principles, and structures output the way a senior copywriter would.
 
Upgrade your Claude interacts with you.
 
---
 
## How to Use a Skill
 
**Option 1 — Custom Instructions (loads on every chat)**
1. Open any skill file and download the raw file
2. Go to [Claude Settings → Customize → Create New Skill](https://claude.ai/settings)
3. Upload the skill file. Done! Every new chat now has the skill active.
**Option 2 — Single chat (flexible, no commitment)**
1. Start a new Claude conversation
2. Paste the skill content as your first message
3. Give Claude your actual task on the next message
**Option 3 — Claude Code / Agents**
Drop the `.md` file into your project's `.claude/` or `.agents/` directory. Claude Code picks it up automatically.
 
---
 
## Skills
 
### ✍️ Writing
 
| Skill | What it does |
|-------|-------------|
| [copywriting](skills/writing/copywriting.md) | Write conversion copy for landing pages, pricing pages, and features |
| [copy-editing](skills/writing/copy-editing.md) | Improve existing copy through 7 focused editing sweeps |
| [content-strategy](skills/writing/content-strategy.md) | Plan content that drives traffic and builds authority for your product |
 
### 🎨 Design
 
| Skill | What it does |
|-------|-------------|
| [minimalist-ui](skills/design/minimalist-ui.md) | Build clean, editorial interfaces — warm monochrome, no generic SaaS look |
| [high-end-visual-design](skills/design/high-end-visual-design.md) | Generate agency-level UI with dynamic layout archetypes and cinematic motion |
| [redesign-existing-projects](skills/design/redesign-existing-projects.md) | Audit and upgrade existing codebases to premium quality without rebuilding |
| [design-taste-frontend](skills/design/design-taste-frontend.md) | High-agency frontend output with tunable design variance, motion, and density dials |
 
### ⚡ Productivity
 
| Skill | What it does |
|-------|-------------|
| [full-output-enforcement](skills/productivity/full-output-enforcement.md) | Stop Claude from truncating — get complete, unabridged code and content every time |
| [business-analyst](skills/productivity/business-analyst.md) | Map processes, gather requirements, identify improvements, and calculate ROI |
 
---
 
## Why Use Skills Instead of Just Prompting?
 
Good prompts help, but skills change the baseline.
 
A skill persists across the entire conversation. It shapes how Claude interprets your requests, what it asks before it acts, what it refuses to do, and how it structures its output. You get consistent expert behavior. Not luck.
 
---
 
## Contributing
 
Skills are just markdown files with a standard header. If you've built a skill that reliably improves Claude's output in a specific domain, submit a PR.
 
See [CONTRIBUTING.md](CONTRIBUTING.md) for the format spec and submission process.
 
---
 
## Roadmap
 
- [ ] SEO audit skill
- [ ] Email sequence skill
- [ ] Programmatic SEO skill  
- [ ] Pitch deck skill
- [ ] More founder tools
---
 
Built by [DivadSanders](https://github.com/DivadSanders) · [Star this repo](https://github.com/DivadSanders/claude-skills-marketplace) if it's useful
