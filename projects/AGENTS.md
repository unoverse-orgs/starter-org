# Projects

This folder holds the org's projects: what we build for this company, and why. Each project is a
living spec, written by people and Agents together. A change is a pull request, and merged means
approved. A plan (a project's spec, decisions, epics and stories) is merged by the reviewing Agent once it
has passed it, and only when it did not write it (`merge_plan`); a person of this org merges
everything else.

## The layout

```
projects/
  <project>/
    spec.md              purpose, users, scope, what we will not build, the epic list
    decisions/
      0001-<slug>.md     one decision each
    epics/
      E01-<slug>/
        epic.md          the value it brings, its requirements R1..Rn, done when
        stories/
          E01-S01-<slug>.md
          retired/       stories no longer wanted, never deleted
```

A project starts from the org's identity (who the company is) and Spatial (what its customers
need). What to build comes out of those two, as an idea a person says yes to.

## A story

One file per story. Its name is its id and a few words.

```markdown
---
id: E01-S02
epic: E01
title: See one call
covers: [R2]
after: [E01-S01]
kind: component
---
## Story
As a relationship manager, I want to see one logged call
so that I know what the customer asked for.

## Words
- A logged call: one phone or video call a relationship manager saved, with its date, who was
  on it, and its notes (up to 2,000 words).
- A need: one thing the customer asked for, found in the notes, in one sentence.

## Example
A call on 3 March with a treasury lead, 40 minutes, notes of 900 words. One need found: "Pay
suppliers in three currencies from one account."

## Check
- C1: GIVEN the example call WHEN I open it THEN I see 3 March, the treasury lead, and the one need.
- C2: GIVEN a call with no need found WHEN I open it THEN it says "No need found in this call".
- C3: GIVEN a call with 2,000 words of notes WHEN I open it THEN the notes wrap and the need still shows first.
- C4: GIVEN the call cannot be read WHEN I open it THEN it says it could not be opened, and nothing else.
  how: reviewed in Studio, light and dark, narrow and wide

## Not in this story
Finding the needs in the notes (E01-S01). Answering the customer (E02-S01).
```

| Field | What it holds |
|---|---|
| `id` | `E<epic>-S<story>`, never reused |
| `epic` | the epic it belongs to |
| `covers` | the epic's requirements it meets |
| `after` | stories that must be done first |
| `kind` | the asset to build: component, app, template, atom, style, task, pipeline, skill, prompt block, node, Agent or identity; or the work to do: research, plan, copy or review (below) |

## The bar for a story

A story is written so a Builder builds it without asking, and a Reviewer checks it without
guessing. From Addy Osmani's planning-and-task-breakdown (MIT): small vertical slices, each with
acceptance criteria and a way to verify it. A story passes only when it has all seven:

1. **One thing a person does.** One behaviour, built by one Builder, checked by one Reviewer. A
   story whose "I want" joins two actions, or that needs more than five checks, is two stories.
2. **Every word is defined.** Each thing it names says what it is: its form, its size, where it
   comes from ("a draft: one email body, 80 to 150 words, written from the brief"; "a source: one
   brief point or one uploaded document, by its title"). A word a Builder would have to guess fails.
3. **A worked example.** Real-shaped data the story is built and checked with: what goes in and
   what the person then sees. Types only, never a customer's or a person's name.
4. **Checks anyone can run.** GIVEN, WHEN, THEN on the example's data, each one a person who did
   not write it can mark pass or fail without asking. For anything a person sees: the full case,
   the empty case, a long case and the error case, each with what the person sees.
5. **What it does not do,** and which story does: "sending to sign-off is E02-S01".
6. **It stands on done work only.** Every check can be run once the stories in `after` are done;
   none needs a story that comes later.
7. **"So that" is a result a person can see,** not a feeling.

A story missing one is sent back before anyone builds it.

## A work card

Not all work builds an asset. Research, a plan, copy and a review produce a document, and they are
cards on the board like any story, so the board holds every piece of work (owner, 2026-11-23: "we
should be driven by the board").

| Kind | It produces |
|---|---|
| research | what was found, in one file per subject, from sources it names |
| plan | a decision the next cards build on: a brief, a site plan, a choice of action |
| copy | the words of a page or a message, written where they are kept (a row, an article, the identity) |
| review | a verdict on finished work, against its written checks |

A work card has the same front matter as a story, and a lighter bar. It passes when it has all four:

1. **One piece of work, as a story.** As a ..., I want ..., so that ..., with a result a person can see.
2. **What it produces, and where.** Each file it writes, by its path in the project's folder (research
   in `discovery/`), and what each file holds.
3. **Checks anyone can run.** GIVEN, WHEN, THEN on what it produced: what is in the file, how much,
   from which sources. Up to five.
4. **What it does not do,** and which card does.

```markdown
---
id: E01-S02
epic: E01
title: What people search for
covers: [R2]
after: []
kind: research
---
## Story
As the org's marketing lead, I want the searches people make for what we offer, and the questions
they ask AI assistants, so that every page is planned for a search someone makes.

## Produces
- `discovery/searches.md`: each search and question, grouped by the kind of page that answers it,
  with how often it is made when a source gives it, and the source.

## Check
- C1: GIVEN searches.md WHEN I read it THEN every search names the kind of page that answers it.
- C2: GIVEN a search with a figure WHEN I read it THEN the figure names its source.

## Not in this card
Choosing the pages (E01-S05).
```

A work card is done when its pull request is merged: the person, or the reviewing Agent for a plan, accepts it.

## The rules

1. **No status in these files.** Whether a story is ready, in progress or in review lives in its
   task, never here. One copy only.
2. **A new project comes in one pull request; after that, one story change per pull request.**
   The first pull request of a project may carry its spec, its decisions, its epics and all their
   stories together. After that, each change to a story's file is its own pull request. An Agent
   changes these files only by pull request, and never merges its own: the reviewing Agent merges a plan it passed
   and did not write, and a person merges the rest.
3. **Every story meets the bar above**, before anyone builds it.
4. **Ids are never reused.** A story no longer wanted moves to `retired/` and says what replaced it.
5. **A decision is never edited.** A new decision replaces it and names the one it replaces.
6. **No keys, tokens or passwords**, and nothing about another org.
7. **No names of customers, prospects or people.** A spec describes types: "Gulf banks",
   "retailers", "a marketing lead". Never a company, a person, a vendor in a customer's stack,
   or a quote from them. Where evidence matters, say how many needs back a point, never whose.
   These files are in Git, and Git keeps everything; a name written once stays in its history.
