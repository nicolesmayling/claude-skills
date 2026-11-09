---
name: job-site-sweep-construction-template
description: Job Site Sweep Construction Template. Sweep company career sites directly for construction jobs that fit the user, check that every posting is live on the company's own site, score each role out of 100, and keep one stack-ranked list in a live tracker page with a notes page and company briefs beside it. Use when the user asks to look for jobs, find openings, check what's posted, scan career sites, run their job sweep or shortlist check, clean closed jobs off their tracker, or get comp ready for a role they're interviewing for. On first use, runs a one-time setup interview that also builds their house rules.
---

# Job Site Sweep Construction Template

This skill reads job boards company by company, the way a careful job seeker would, instead of trusting job-alert algorithms. It is set up for construction careers (general contractors, subcontractors, owners and developers, construction management firms), but every rule comes from the user's own answers. It keeps everything in ONE place: a live tracker page with every open role in a single stack rank, a notes page for the detail behind each row, and short briefs on the companies at the top of the list. A sweep that hands back a separate list is a failed sweep.

Everything personal lives outside this skill: target roles, commute, companies and proof points in a memory file, the pay floor on the tracker page itself (memory may refuse to store salary targets), and permissions and writing style in the user's house-rules skill. That way the skill works for anyone, and changing a rule never means re-uploading the skill.

## 0. One-time setup

At the start of every run, check two things: whether a skill named `house-rules` is available, and whether `/areas/job-sweep-config.md` exists in memory with no field still blank. If both are in place, load house-rules with the Skill tool, follow it for the whole run, and go to section 1. If either is missing, run the missing part of setup first. Setup happens once; after that, the user only hears from setup again if they ask to change a rule.

**Before anything else, check memory is on.** The config file lives in Claude's memory, so if memory is off nothing carries between runs. Ask them to confirm that "Generate memory from chats" is on (in Claude's settings, under Your Claude), and that they aren't in an incognito chat.

**How to ask.** One or two questions at a time, in plain language, then wait. Every question comes with a recommended answer they can accept with a "yes" or change, so nobody has to invent rules from scratch. Say why you recommend it in one line. Never fill a field they did not confirm.

### 0a. House rules (first)

House rules are the standing rules every one of their Claude skills follows: what Claude may do without asking, how it writes, and how it keeps things manageable. Explain that in one sentence, then ask:

1. **What Claude may do without asking.** Recommend: reading any website, reading email and calendar, saving email drafts, and updating the job tracker are fine. Sending email or messages, applying to jobs, submitting any form, accepting or declining meeting invites, and anything that costs money always need a yes first.
2. **How Claude should write to them.** Recommend: plain, direct language like a friend who knows the industry; short sentences; no corporate buzzwords; lead with what changed and what they need to do. Ask for any words or habits they dislike.
3. **How much at once.** Recommend: no more than three decisions or tasks per reply, one at a time when it is something they have to act on.
4. **Anything else.** Recommend nothing extra; ask if there is a rule they wish every assistant followed (for example "always give me the phone number when you mention a company").

Then write a house-rules skill from their answers only. Use this shape:

```
---
name: house-rules
description: <Name>'s standing permissions, writing style and pace rules. Load at the start of any of their skills and before drafting anything in their voice.
---
# House rules for <Name>
## Permissions
- Fine without asking: ...
- Always ask first: ...
## Writing style
- ...
## Pace
- ...
## Other
- ...
```

Give it to them in the easiest way this session allows: if a tool for proposing skills is available, use it so they can save the skill from a card; otherwise write `house-rules/SKILL.md`, zip the `house-rules` folder, send the zip, and tell them to upload it in Claude through Customize, then Skills, then the + button, then Upload a skill. Menu names in Claude change from time to time; if theirs looks different, look it up on support.claude.com rather than guessing. Until it is saved, follow their answers directly for the rest of this conversation.

### 0b. Job search rules

Start by asking for their resume (a file or pasted text) and, if they have one, a project list or LinkedIn profile. Read them first; most recommendations below come from those documents.

Ask, with these recommendations:

1. **Name and situation.** Recommend from the resume: their most recent title and years in construction. Ask whether they are working, laid off or about to be.
2. **Target roles.** Recommend a three-step ladder built from their resume. Example for a project manager: full marks for Project Manager, Senior Project Manager, Construction Manager and Project Executive; partial credit for Owner's Representative, Preconstruction Manager and Superintendent; zero for Estimator-only, Safety-only, sales and field labor roles. Adjust it to what they have actually done.
3. **Pay floor.** Recommend their most recent base salary as the floor, and offer to check what employers in their area are posting for their title before they decide. Explain that a posted range passes if it can reach the floor, even if it starts lower.
4. **Location.** Recommend a commute limit in minutes rather than miles (for example 45 minutes each way), since construction roles are usually on site most days and remote rarely applies. Ask whether jobsite travel or out-of-town projects are acceptable, and whether they would relocate.
5. **Companies.** Recommend building the list from sources that rank contractors, and offer to pull the firms in their region: the ENR Top 400 Contractors list, ENR's regional Top Contractors lists, the Building Design+Construction Giants 400, and the member directory of their local AGC chapter. Suggest three groups (for example large general contractors, owners and developers, and regional firms), plus any company they will not work for and why.
6. **Proof points.** Recommend five or six, drawn from the resume, each with a number: project types and dollar values, schedules beaten, team size led, safety record, and credentials such as PMP, OSHA 30, LEED AP or CCM. Push for specifics; "managed projects" is not a proof point, "delivered a $40M hospital two weeks early" is.
7. **Scoring weights.** Recommend the default model in section 5 (Function 30, Scope 30, Growth 20, Pay 15, Workplace 5) and explain it in one line: the kind of job and their proof for it matter most, the company's momentum next, and pay last because the pay gate already guarantees every role can reach their floor. Change it only if they ask.
8. **People.** Ask who has offered to refer them and where those people work. Recommend also listing former bosses and project owners who now work at target companies. Explain that every sweep will name their contacts at each ranked company, because a referral moves their odds more than anything else.
9. **Email and job alerts.** Recommend connecting the Gmail they use for job searching, and setting up job alerts on LinkedIn and Indeed plus each target company's own careers site, so every run has fresh leads. If an Indeed connector is available in Claude, recommend turning it on too; the sweep can then search Indeed directly (section 3).
10. **Exceptions.** Explain that exceptions are the "except for" rules that bend the standard ones, and that most people have a few once they think about it. Offer examples to react to, then ask which apply and whether they have others:
    - A longer commute or more site days for a specific company or project they really want ("I'd drive 75 minutes for Swinerton").
    - Companies they won't work for, with the reason (a former employer, a safety record, a bad reputation, a non-compete).
    - Project types, sectors or schedules to skip (single-family residential, night shifts, a FIFO rotation) or to favor (healthcare, data centers, public work).
    - A lower pay floor for a specific kind of job, such as an owner's-side role or a company with a strong pension or profit sharing.
    - Travel they'd accept for a set region or length of time, even if they don't want it in general.
    - A company or contact that always gets checked first, every sweep.
    Recommend none they haven't named; an empty list is fine. Write each one exactly as they put it.

Then write `/areas/job-sweep-config.md` with this shape, every line tagged `[stated]`, using only what they confirmed:

```
---
name: job-sweep-config
description: Job search rules for the job sweep: target roles, location, companies, proof points, scoring weights
sources: [chat]
aliases: [job sweep config, job search rules]
---
## Gates
- [stated] Location: ___ ; max office/site days: ___ ; remote: yes/no ; relocate: yes/no
## Function ladder
- [stated] Full marks: ___
- [stated] Partial: ___
- [stated] Zero (not a fit): ___
## Companies
- [stated] Group A: ___
- [stated] Group B: ___
- [stated] Never: ___ (reason)
## Proof points (scope items)
- [stated] ___
## Scoring weights
- [stated] Function __, Scope __, Growth __, Pay __, Workplace __
## Exceptions
- [stated] ___ (what it overrides)
## Referrals
- [stated] ___ at ___
## Email
- [stated] Alerts and recruiter mail: ___
## Tracker
- Tracker: <url> ; Notes: <url> ; Briefs: <url>
```

Do not put the pay floor in memory. It goes on the tracker page as `PAY_FLOOR` in the script and in the How this list works box.

Then build the three pages (section 7): the tracker, the notes page and the company briefs page. Save all three URLs to the config file under `## Tracker`, and offer the schedule in section 9. Setup ends there; the first sweep can run right after or later.

## 1. Load context every run

Load the house-rules skill and follow it. Read the config file and `/areas/job-search-pipeline.md` if it exists. Read the live tracker, notes page and briefs page with the Artifact tool (action "read") and work from those versions; take the pay floor from the tracker's `PAY_FLOOR`. Memory wins over anything on the pages.

Rules change, sometimes in another chat mid-week. Treat the config file as the live version and this skill as the default. When the user changes a rule, update the config the same day so the old rule can't come back.

## 2. Hard gates: only two

A role lands on the ranked list if it passes both. Everything else is scored, not screened.

**Exceptions come first.** Before applying either gate, check the config's Exceptions. An exception overrides only the rule it names: a longer commute allowed for one company still leaves that company's pay gate in place. A company on the won't-work-for list is cut with its reason, never listed. Note on the role's card when an exception let it through, so the user can see why it's there. Exceptions can be added any time the user says so; ask them to set one up whenever a cut would have gone the other way for a reason they've stated before.

**Pay reach.** The posted base range must be able to reach their floor (`PAY_FLOOR` on the tracker page). A range from well below to well above passes. A range that tops out below the floor fails. If only total pay (base plus bonus) is posted, say so and screen it against the floor plus a typical bonus for that field, stated on the row. If nothing is posted, keep the role, estimate the range, label it "Est." and name where the estimate came from (the company's own ranges for similar roles first, then a direct competitor's posted range, then salary sites). A cut that rests on an estimate is a soft cut; say so.

**Location.** Use the config. A role whose office or site days exceed their limit fails. Unstated policy passes with the silence flagged, and is never guessed from the company's reputation. Read the policy per posting, not per company; the same company often posts remote and on-site roles with different wording.

## 3. Where to look

1. **Email first.** Job alerts, recruiter mail and application status mail since the last run (at least the last 7 days on a full sweep). Recruiter mail has no window: report anything unanswered however old.
2. **Company boards.** Every company in the config, read on the company's own careers site or the hiring system it uses (Workday, Greenhouse, Lever, Ashby, iCIMS, and similar). Read the full list of openings, not a search result.
3. **Indeed search, if the connector is on.** It reaches jobs alert emails never send and companies outside the config list. Run several narrow searches rather than one broad one, since each returns only about 10 results: one per full-marks title on the function ladder, each against their home city and, if they'd travel, their region. Results match loosely, so expect most to fail a gate on their face; drop those without counting them as cuts. For anything that could pass both gates, open the full job details, then find the same job on the company's own site and link that. Don't store Indeed job IDs or links; they change between searches. Pay shown on Indeed counts as the company's number only once the same figure is on the company's own posting. If the connector is off or errors, write "Indeed: skipped (reason)" and keep going.
4. **Leads from elsewhere.** LinkedIn and other job sites can point at a role. They are never the evidence and never the link. Find the same job on the company's own site.

**Boards that only open in a browser.** Some company sites only load in a real browser. Scheduled runs are cloud only and can't use one, so they try each such board once; if it fails, mark its rows "Could not verify" with the date, list the board under "Needs a browser" in the run's notes, and move on. The next time the user runs a sweep themselves in the desktop app with a browser connected, read those boards first.

**Flag mail from tracked companies, every run.** Every run, including Shortlist checks and verify-only runs, searches the connected Gmail since the last run for mail from any company on the tracker or in the config: its own domain, its recruiters, and its hiring system (Workday, iCIMS, Greenhouse and similar send from their own domains with the company named in the message). For each match:

- Put a flag on that company's row in the tracker (In flight or Open) with the date and a one-line summary, such as "Interview request, Nov 9" or "Recruiter asked for availability." Keep the flag until the user says it's handled or a later email resolves it.
- Add it to Waiting on at the top of the notes page, newest first, with a link to the email.
- If it changes the job's status (applied, rejected, interview, offer, a recruiter conversation), move the row to match right away.
- If it needs a reply, save a draft reply in Gmail when house rules allow drafts, and say so on the flag. Never send.

Mail from a company that isn't on the tracker yet but is clearly about a job (a recruiter reaching out cold) gets flagged in Waiting on too, with a note that the company isn't on the list. If Gmail isn't connected, say "Email: not connected" at the top of the run's notes and in the summary, every run, until it is.

## 4. Verify every posting, and keep three states

Before the tracker is published, open the exact link on every row this run touches and confirm the page is the job itself, the title matches, and it still takes applications.

- **Live:** keep it, write today's date in the Verified column.
- **Closed:** move it off the ranked list into Closed, with the date and the evidence (a 404, "no longer accepting applications", a redirect to the careers home page).
- **Could not verify:** keep it in its normal place, mark it "Could not verify" with what was tried. Never quietly carry it as live.

Never use a summarizing fetch as evidence; read the page itself or the hiring system's own data for that job.

## 5. Scoring, out of 100

The defaults below are the recommended model. If the config lists different weights, use those and scale each ladder to match.

| Input | Points |
|---|---|
| Function fit | 30 |
| Scope match to their proof points | 30 |
| Company growth | 20 |
| Pay | 15 |
| Workplace signal | 5, starts at 3 |

The page script carries `SCORING_MODEL = 100`. If the user ever changes the weights, bump it and rescore every row in the next full sweep before publishing, so the list never mixes two scales.

**Function, 30.** From the config's ladder: full-marks roles 30; partial roles 18; a role with the right title but mostly the wrong work 8; zero-list roles 0. Title alone never decides it; read what the job actually does.

**Scope, 30.** Add points for each proof point the posting clearly asks for, capped at 30. Weight the config's proof points so the strongest one is worth about a third of the total and the rest share the remainder; write the weights into the config the first time you score. Name which proof points matched on the role's notes.

**Growth, 20.** Last 12 to 24 months. Public company: revenue up 20%+ and headcount up, 20; up 10 to 20% with headcount up, 12; flat or down, or a restructuring in the latest annual report, 3. Private company: new funding or a major win inside 12 months and still hiring, 20; steady hiring with nothing new, 9; layoffs reported in the last 12 months, 0. Only company-written material available: 8, labelled "growth read unavailable". In fields like construction, a strong backlog, major contract wins and steady hiring count as growth; say which signal you used.

**Pay, 15.** Where their floor sits inside the band: floor at or above the bottom and the top well above, 15; floor at or above the bottom, 13; floor below the midpoint, 11; floor above the midpoint, 7.5; floor within about 5% of the top, 4. Multiply by 0.7 for an estimated band.

**Workplace, 5.** Start at 3. Credible national best-employer lists move it up to 5; credible negative signals (low Glassdoor rating on 300+ reviews, recent layoffs) move it toward 0. Small companies not covered by any list stay at 3.

**Gate on the score.** A role that scores 0 on function or 0 on scope is not listed at all. It goes in the notes page's Checked and cut section with the reason.

**Fit score, for sorting.** Function plus scope, out of 60, is the role's fit score: how well the job matches what they can do, with company and pay left out. Show it as its own column and let the Open table sort by it as well as by the overall score, so they can look at the list both ways. The rank number always follows the overall score.

**Odds are separate.** Next to the score, give a coarse odds band (under 10%, 10 to 25%, 25 to 50%, 50%+) with one line of reasoning: unmet must-haves, whether they have a referral or a live conversation with a recruiter or hiring manager, and how the company has responded to them before. Give the band a baseline: cold applications convert in single digits even for well-matched candidates, so say what lifts a role above that. When rank and odds disagree, say so in a note rather than demoting the role. Odds never move the rank.

**Referrals, every sweep.** For every company on the ranked list, name the people in the config's Referrals who work there. If a browser with their LinkedIn is available, also check for contacts at the top-ranked companies who would make good referrals, and list them on the role's notes card. Never message anyone.

**Quals check.** For each ranked role, list the posting's stated minimums and whether they clearly meet each one. Report it; don't score it.

## 6. Tone of the results

Give real reasons for every cut. Say plainly when a role is a stretch. Don't pad the list to look busy, and don't give generic advice to "network more".

## 7. The three pages

Three HTML artifacts, each published privately with the Artifact tool and updated in place at the same URL every run. Build any that are missing on setup. Every page reads well on a phone and in dark mode.

### The tracker

Keep it the cleanest table possible: one row per job, nothing that wraps past a line. Commentary never goes here; it goes on the notes page.

Page structure, top to bottom:

1. **How this list works.** A small box with the schedule, the scoring weights and the two gates. No changelog or run notes in the header, ever.
2. **In flight.** Jobs they applied to, plus any job where they have a live conversation with a recruiter or hiring manager even before applying: company, role, hiring manager, location, pay, applied date, status, as-of date. A job with a live conversation moves here automatically instead of sitting in the Open rank.
3. **Open, ranked.** Rank, company (linked to its brief when it has one), role (linked to the company's own posting), location, pay, score, fit score (sortable), odds, Verified date. The rank number links to the role's card on the notes page. A dot marks roles new since the last full sweep.
4. **History.** Every application that ended, with applied and closed dates and the furthest stage it reached.

Show an email flag beside the company name on any row with unhandled mail (section 3), with its date and summary on hover or tap.

Keep the data in arrays in the page script (`FLIGHT`, `OPEN`, `CLOSED`, `HISTORY`, `FLAGS`) plus `PAY_FLOOR`, `SCORING_MODEL`, `BRIEF_SLUG` and `LAST_RUN` (`full`, `check` and `verify` dates). Leave a comment in the script explaining what each holds, so the next run edits data rather than rebuilding the page.

### The notes page

Everything the table leaves out, in this order:

1. Waiting on, and a dated note box for this run.
2. A card per ranked role at an anchor `id="rank-NN"` that matches its rank: title as posted, function fit, site days, pay verdict, quals met and missed (the posting's own wording), odds reason, growth read, workplace read, referral contacts, why it fits, where it strains, source, and the verified date with how it was checked.
3. Checked and cut, with a real reason for every cut. Users value this as much as the shortlist. When a rule changes, restate old cut reasons against the new rule.
4. Closed, with the date each job was found closed and the evidence.
5. Notes and caveats: the verification pass result, which boards needed a browser, the email and Indeed pass, and anything that could not be checked.

Rank numbers and `rank-NN` anchors must match after every restack; renumber the anchors in the same pass.

### Company briefs, top 20 only, Mondays only

One card per company at `id="co-<slug>"`: growth, revenue and backlog, ENR or other industry ranking where one exists, employees, layoffs, what they build and for whom, and three competitors with one line on how they differ. Every field carries its source and date, and anything company-written is labelled as such.

Only the companies behind Open ranks 1 to 20 get briefs, and only on the Monday run: write a card for any of them that lacks one and refresh the ones that have one. Leave companies below rank 20 alone, and never delete a card because its company dropped out. A company that enters the top 20 midweek gets its brief the following Monday. Add a `BRIEF_SLUG` line on the tracker so the company name links to its card.

### Publishing rules

Other runs (a Shortlist check, an inbox update, the user editing a page) can publish to the same pages, sometimes minutes apart. So right before publishing, read each page again, compare it with the copy you started from, carry their changes into yours, and only then publish. Edit the data, not the layout. Check the tracker script parses (`node --check`). Publish once, at the end.

On a full sweep, publish all or nothing: if every open row could not be rescored and verified, keep the old scores and `SCORING_MODEL`, publish only verified closures and inbox moves, and say plainly that the sweep did not finish.

## 8. Run modes

**Full sweep.** Email, Indeed, every company board, verify every row, score new roles, rescore if the model changed, restack the whole list, clear the previous sweep's new-role dots, write a notes card for every new role, refresh briefs if it's Monday, set `LAST_RUN.full` only if it finished.

**Shortlist check.** The quick run between full sweeps. In flight rows plus Open ranks 1 to 60 only. (1) Reopen every In flight posting and the 20 Open rows in the top 60 checked longest ago. (2) Read email since the last run for submissions, rejections, interviews and recruiter conversations, and move rows to match. (3) Add roles from job alert emails and the Indeed search only, scoring each and inserting it at its score with the dot, without rescoring anyone else. (4) Write the notes card for every role it added; if time runs short, list them under "Cards owed" in the notes page and the next run writes those first. (5) Set `LAST_RUN.check`. No board sweeps, no growth or workplace reads, no full restack.

**Verify-only.** When they ask whether jobs on the list are still open, or to clean closed jobs off it: check every row, move closed ones, restack, publish. Skip email, Indeed and board sweeps.

When they tell you directly they applied, got rejected, have an interview or are talking to a recruiter, update the tracker right away.

## 9. Schedule (offer at setup, set up only if they agree)

If their Claude plan offers scheduled tasks, suggest these, all cloud-only so nothing depends on their computer being on:

- **Full sweep,** Monday and Wednesday, early morning.
- **Shortlist check,** Friday morning.

If they'd rather run lighter, a full sweep on Monday and Shortlist checks on Wednesday and Friday works too. Pick minutes off the hour (for example 5:52, 6:42) so runs aren't delayed, and don't let these collide with any other scheduled tasks they have. Each scheduled prompt should say to load this skill, run the named mode, never stop to ask questions, and send a two or three line summary at the end. A full sweep is the heaviest run; mention that they can watch their usage in Claude's settings. If scheduled tasks aren't available, they just ask Claude to "run my job sweep" or "run my shortlist check."

## 10. Comp readiness for jobs in process

The gates only ask whether a band can reach their floor. This section is for later, when a specific In flight job gets close enough that they need to talk numbers. Neither level changes the rank, the odds or the gates.

**Comp expectation line, at the recruiter screen.** Any In flight job with a recruiter or hiring manager conversation booked or done gets a short comp expectation line on its notes card. It needs only the posted band and their floor.

**Full comp brief, at final round or offer.** When email shows a final round, a verbal offer, a reference request or an offer letter, flag "Comp brief owed: <company, role>" in the run's notes and build it if time allows. Also build it whenever they ask ("get comp ready for X"). On the role's notes card, under a "Comp" heading:

1. **The band.** The posted range for this job with the date read, plus the same company's posted ranges one level above and one below, and where their floor sits inside the band.
2. **Market cross-checks,** each labelled with its source and never blended into the posted number: posted bands from two or three direct competitors for the same title and region, and any salary survey for their trade they can see. Never present a number as survey data unless someone actually gave it to them.
3. **The full package.** Base, bonus, vehicle or truck allowance, per diem for travel jobs, profit sharing or equity, and benefits that differ from their last job. Mark each part Stated, Posted or Unknown.
4. **Their numbers.** Their floor comes from the tracker. Their target and opening ask are theirs to set: ask once and file what they say in the pipeline file. Never invent a target or infer one from past pay.
5. **Questions for the recruiter,** no more than three, such as where in the band offers usually land and what the bonus has paid out in recent years.
6. **Draft language.** An updated expectation line and a short counter draft. Drafts are fine; sending or saying anything as them always needs a yes.

Many states limit salary-history questions or require employers to share a pay range on request. Check the current law for their state before mentioning it in anything they send.

## 11. Memory

File only what the user says, tagged `[stated]`: rule changes go in the config file, applications and outcomes in `/areas/job-search-pipeline.md`, one short dated line per run. Never file research (a job you found is not something they told you). Never store salary figures, account numbers or sensitive personal details in memory.

## 12. Writing style

Follow the house-rules skill. Where it says nothing, use plain, direct language, like a knowledgeable friend writing a quick message. Short sentences. No hype, no filler, no stock sign-offs. Lead with what changed and what they need to do.
