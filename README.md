# ats-resume-checker

Check your resume against a specific job posting before you apply, and get back
a checklist of what to fix.

A skill for **Claude Code** and **Cowork**.

## Introduction

Most resumes are read by an **applicant tracking system (ATS)** before a person
ever sees them. The ATS pulls your name, your jobs, your dates and your skills
out of the file and drops them into a database. If it can't read part of your
resume, that part may as well not be there.

This skill checks two things: whether an ATS can read your resume cleanly, and
whether it says what this particular posting is looking for. You get a
**pass / warn / fail** checklist, sorted worst-first, with a specific fix for
each item.

The grading runs in a **sub-agent**: a separate, freshly-started Claude that
sees only your resume, the posting, and the checklist. Never your chat, and never
its own earlier verdict. So you can re-check after edits in the same conversation
and get an honest second opinion.

## Table of Contents

- [Installation](#installation)
- [Quick start](#quick-start)
- [What it checks](#what-it-checks)
- [Which file to give it](#which-file-to-give-it)
- [What the report looks like](#what-the-report-looks-like)
- [Limitations](#limitations)
- [Support](#support)
- [License](#license)

## Installation

### Claude Code

The simplest way is to ask Claude Code to do it:

> Install the skill at https://github.com/kanitthac/ats-resume-checker into my
> personal skills folder.

It will clone the repo for you. You'll be asked to approve the command first.

Or do it yourself:

```bash
git clone https://github.com/kanitthac/ats-resume-checker.git ~/.claude/skills/ats-resume-checker
```

**Start a new session afterwards so the skill loads.**

### Cowork

Download this repository as a ZIP, then upload it at **Customize → Skills**.

## Quick start

Give it two things: **your resume** and **the job posting**.

Ask in your own words. All of these work:

> Check my resume `~/Documents/<company>/resume.docx` against the posting in the same folder

> Review my resume against this posting. Will it get through screening?

> Is `resume.pdf` tailored for this role? `<paste posting>`

If it doesn't pick it up, ask for it by name — "run the ATS resume checker on my
resume against this posting".

It also asks how you want the report laid out — **Table** reads best in an app,
**Bullets** reads best in a terminal. Say which up front ("check my resume, in
bullets") and it won't ask.

A `.docx` or `.pdf` gets you one extra check that plain text can't support. See
[Which file to give it](#which-file-to-give-it).

## What it checks

1. **Layout & Formatting**: can an ATS read your file at all?
2. **Structure & Headings**: are your sections named and ordered the way an ATS
   expects?
3. **Keywords & Optimization**: does your resume use this posting's words? Exact
   matches and near-matches are listed separately. A filter looking for "quality
   assurance" may not find "QA", though a recruiter would count it.
4. **Content Quality**: do your bullets show results, or only duties?
5. **Contact & Length**: is your contact block complete and readable, and is the
   resume the right length?

The exact checks live in [`reviewer-prompt.md`](reviewer-prompt.md), which is the
source of truth for everything that gets graded.

## Which file to give it

**Give it the file you'll actually send.** Markdown and pasted text work fine for
four of the five categories, but the first one can't be checked from text at all:

| | `.docx` / `.pdf` | Markdown / pasted text |
|---|---|---|
| Layout & Formatting | Checked | **Can't be checked** |
| The other four categories | Checked | Checked |

Columns, tables, text boxes, fonts and header placement simply don't exist in
plain text. A table's contents arrive looking exactly like ordinary paragraphs.
So when you paste text, the report says layout was **not checked**. That is not
the same as saying it passed.

One thing only a real file can reveal: a **scanned or photographed PDF**, which
contains no text at all. It looks perfectly normal when you open it, and an ATS
gets nothing out of it at all.

In practice: draft and iterate however you like, then run it once more on the
finished `.docx` or `.pdf` before you send it.

## What the report looks like

Every category gets a verdict:

| Category | Verdict |
|---|---|
| Layout & Formatting | 1 ⚠️ — not checked |
| Structure & Headings | 1 ❌ |
| Keywords & Optimization | 4 / 5 stated requirements met · 1 ❌, 5 ⚠️ |
| Content Quality | 3 ⚠️ |
| Contact & Length | 1 ⚠️ |

Then each ⚠️ and ❌ is listed, worst first, with a specific fix. Each one tells
you whether it risks the **ATS misreading your resume** or only a
**recruiter's impression**. One row, as an example:

| Priority | Area | Problem | How to fix |
|---|---|---|---|
| ⚠️ | Keywords & Optimization | The posting asks for "stakeholder communication" three times. Your resume shows it — "presented quarterly results to the leadership team", "wrote release notes for three product teams" — but the word **communication** never appears anywhere in the document. A filter searching for that phrase finds nothing, even though a person reading it would credit you. | In your Skills line, change "presented quarterly results" to "stakeholder communication: presented quarterly results". One phrase, no new claim. |

## Limitations

This is a **best-practice check, not a real ATS.** It applies well-established
rules and judgment to estimate how your resume will do. It does not run your file
through Workday, Greenhouse, Taleo or iCIMS, all of which read resumes slightly
differently.

Treat the output as strong guidance for getting past the ATS and a
recruiter's first scan. It is not a guarantee.

## Support

If this saved you some time, you can [buy me a coffee](https://buymeacoffee.com/kanitthac).

## License

MIT. See [`LICENSE`](LICENSE).
