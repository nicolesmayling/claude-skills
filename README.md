# Claude skills by Nicole Smayling

Skills I built and use every day as a product marketer. I'm sharing them so other go-to-market people can try them, change them and make them their own.

## techNicole.ai Inbox Brief

A daily chief-of-staff check on your Gmail and Google Calendar. Most inbox summaries only tell you what arrived today. This one keeps a running ledger, so things don't disappear just because they're a day old.

What it does:

- **Carries open items forward.** Anything you still need to do stays on the list until there's evidence it's done, like your reply in the thread or a confirmation email.
- **Tracks both sides of every ask.** It lists what you're waiting on from other people, and it reads your sent mail for what you promised them.
- **Shows what it skipped.** Anything filed as noise that might have been a real person gets one line at the bottom, so you can trust the filter.

It drafts replies for the two most urgent items but never sends, archives or deletes anything without your OK.

### What you need

- Claude with the Gmail connector turned on. Google Calendar is optional but makes the brief better.
- A Gmail inbox. It uses Gmail's search, so it won't work with Outlook as written.
- Memory turned on helps, since the ledger lives there. Without memory, Claude keeps the ledger in a document you can see.

### How to install

- **Claude app:** download the `technicole-ai-inbox-brief` folder, zip it, and add it as a custom skill. Anthropic's help center article on using skills in Claude walks through the steps.
- **Claude Code:** copy the `technicole-ai-inbox-brief` folder into `~/.claude/skills/`.

Then ask Claude to "check my email" or "run the techNicole.ai inbox brief." On the first run it asks a few quick setup questions, like which newsletters count as noise.

**Tip:** the first time it runs, Claude asks to use Gmail and Calendar. Choose the always-allow option for reading your mail and calendar so it doesn't ask every day.

### Run it automatically

Most people get the most out of it as a scheduled task. Ask Claude to "schedule my techNicole.ai inbox brief for 8 AM Monday through Friday," or any days and time you want, and the brief will be waiting for you when you start your day.

### Make it yours

Everything is plain text in `SKILL.md`. Change the noise list, the section order or the tone to fit how you work.

Enjoy! Let me know if you have any feedback.

---

Built by Nicole Smayling, product marketing leader. I write about AI for go-to-market teams as @technicole.ai.
