---
name: story-explainer
description: Turn any complex thing — an article, a GitHub issue or PR, a design doc, a chat thread, a tutorial, a paper, a codebase concept — into an animated, story-told explanation (boxes, arrows, beats, and UML-style sequence, state, component or flow diagrams where they fit) that gives a high-level understanding without telling everything. Use this whenever the user hands over a link, file or pasted text and says things like "explain this to me", "storytell it", "I don't get it", "make me understand", "I'm lost / overwhelmed / scared of this", "explain it like I'm new", "walk me through it so I can follow", or wants a presentation to explain a topic to a colleague. Also use it when they ask for "the big picture", "a mental model", or "enough to not be scared of it". Not for exhaustive summaries, reference docs or step-by-step tutorials.
---

# Story explainer

The promise: after ninety seconds the viewer is no longer scared of the thing, is not overwhelmed, and
is curious enough to open the source and dig. That is a different job from summarising. A summary
tries to lose nothing. A story deliberately leaves most of it out and keeps the few parts a
person needs to build a mental model they can hang the rest on later.

The output is an animated film of beats (boxes, arrows, a few words on screen) rendered as a
Motion artifact, with a fallback to a click-to-advance page. The user watches; they do not read.
The reader to design for is a junior who joined today and will sit in the meeting where this is
shown. They should be able to follow it AND form an opinion at the end.

## 1. Read the source, all of it

Fetch the whole thing before deciding anything. Half-read sources produce confident wrong stories.

- A URL: the `web-fetch` agent or WebFetch. Follow one level of links only when the page itself is
  thin (an issue that says "see the design doc").
- A GitHub issue, PR or discussion: `gh issue view <n> --comments` / `gh pr view` (the comments
  often hold the real story: the pushback, the thing that was wrong the first time).
- A pasted thread, an email, a transcript: read it as given; the chronology is the story's spine.
- A file: Read it. A PDF: by pages.
- A concept in the user's codebase: explore the code first (an Explore agent for breadth), because
  the story must show how it works here, not how the textbook says it should.

Write raw notes to a scratch file as you go (actors, dates, numbers, names, the sentence where the
problem is stated, the sentence where the answer is stated). Never show these notes to the user.

## 2. Find the story before you find the pictures

Answer these in one line each. If you cannot, you have not understood the source yet; read again.

1. **Who wants what, and what hurts.** A person, a team, a system. The pain in plain words.
2. **How it works today.** The concrete mechanism, as it actually is, including the ugly part.
3. **The obvious first answer.** What anyone would try first. (Sources rarely say this; infer it.
   It makes the real answer land, because the viewer thought of it too.)
4. **The twist.** What you learn when you look closer: the hidden constraint, the second case,
   the thing that breaks the first answer.
5. **The shape of the real answer.** One picture. If you need two, you have two stories.
6. **Why it holds, and what it costs.** The reason it is right, and the trade-off nobody hides.
7. **Three doors.** Three precise places in the source where a curious viewer should go next
   (a section, a file, a comment, a figure). These go in your reply, not on screen.

If the source is an open question (a proposal, a debate), the "real answer" beat shows the options
side by side, named plainly, and the end card names the choice still to be made, as a statement
("two roads, one to pick"), never as a question. Never settle in the film what the source left open.

## 3. The budget

What makes a story land is what you leave out. Hold to this, or the viewer gets a lecture with arrows.

- **At most seven named things** across the whole film (components, people, concepts). Everything
  else is "the rest" or is not mentioned. Before you write a scene, list the seven and keep the list
  beside you; when a scene wants an eighth name, it gets a plain description instead ("the one who
  holds the pen", not "candidate"). Protocols and specs are where this slips, because every term
  feels load-bearing. It is not: the viewer will meet the rest in the source.
- **One metaphor**, chosen from the subject's own world, kept from first beat to last. A wiring mess
  is a patch panel; a queue is a kitchen pass; a cache is a corner shop; a consensus protocol is a
  committee that must agree before writing in the ledger. Pick what the subject's own people would
  say, never a generic "journey" or "puzzle pieces".
- **As many beats as the topic needs, and no more.** A small idea is seven beats; a design review
  with five findings and two decisions may be sixteen. The count comes from the story, never from
  a target. Each beat is eight to sixteen seconds and has ONE subject and ONE thing that happens
  to it; if a beat needs two things to happen, split it. The only hard limit is the player's:
  a film over 300 seconds will not load, so past about twenty beats, cut or make two films.
- **New names arrive one at a time.** A beat may introduce at most one new named thing, and only
  when the beat is about it. The seven-things cap above is for a short film; a longer film earns
  more names, but never two in one beat and never one the story does not use again.
- **Words on screen are captions, not prose.** A title line of at most eight words, a tag of at most
  five. Real identifiers from the source are welcome, one or two per beat, in a mono face, because
  they are the handles the viewer will grep for later.
- **Plain words for judgments.** "remembers nothing", "fires twice", "nobody can see it all" beat
  "stateless", "duplicate emission", "lack of observability". The jargon can sit in a tag next to it.
- **No bullet slides.** If a beat is a list, draw the list as objects that arrive one by one.

## 4. The beat template

Use this arc by default; drop or merge beats to fit the source, never pad to nine.

| # | Role | What is on screen | Words |
|---|------|-------------------|-------|
| 1 | The knock | The actor arrives and asks for the thing. Title visible at frame 0. | title + one line of pain |
| 2 | Today | The current mechanism drawn honestly, the ugly part marked. | "today" + tags |
| 3 | First idea | The obvious fix, drawn as if it works. | "first idea" |
| 4 | Look closer | A sweep, a zoom, a count: the twist appears. | one number or one word |
| 5… | Findings | One finding per beat, as many beats as there are findings, each a concrete mechanism ending with what it breaks. | "what we found, one/two/…" |
| 8 | The shape | The real answer as one picture; the messy picture straightens into it. | the three moves / the rule |
| 9 | Why | Why it holds: at most three cards, one rising after another, nothing else on screen. | "why this one" |
| 10 | The door | An end card alone: the name of the thing and one line that states the takeaway (the rule, the shape, or the choice still open). Held three seconds or more. | the one line |

Beats 9 and 10 are separate on purpose: every time they were merged, the closing scene stacked
cards, an order strip and a closing line into one frame and became a slide. If the source has
an order of steps worth showing, it is its own beat too, before the why.

**The film never ends on a question.** No "questions?", no "ideas, holes?", no "what do you
think?" on the end card or anywhere in the last beat. The viewer is in a room where asking is
their call; a card that asks for it reads as a slide. End on the thing itself: its name and the
one line a viewer should carry out of the room. An open source ends on the choice stated, not asked.

The metaphor enters in beat 1 and is still on screen in beat 10. A metaphor that appears in the
middle is decoration; one that frames the knock and the door is how the viewer remembers the thing.

A worked example with every beat's actual on-screen content is in `references/worked-example.md`.
Read it once before your first film; it shows how little text a beat carries.

## 4b. UML, in the film's own style

Engineers already read four or five diagram shapes without thinking. Use them when the beat's
mechanism is one of these, because a familiar shape costs the viewer nothing to decode:

| The beat shows | Draw | How it animates |
|----------------|------|-----------------|
| who talks to whom, in what order | a **sequence diagram**: lifelines for the actors, horizontal arrows top to bottom, a note box on a lifeline for what is stored or decided, an `alt` box for a branch | arrows draw one after another, top to bottom; the note pops when its arrow lands |
| what a thing can be, and how it moves between those | a **state diagram**: rounded states, labelled transitions, a filled dot for the start, a ringed dot for the end | the token moves along the transition that is being told; the other states stay dim |
| which parts exist and which depend on which | a **component diagram**: boxes with ports, cables between them, a dashed box for a boundary (a service, a process, a team) | parts rise in dependency order; the cable that the argument hinges on draws last and in the accent |
| a decision with branches | a **flow / activity diagram**: rounded steps, diamonds for the choice, labelled exits | the taken path lights, the untaken path stays grey |
| the shape of a record | a **class or record box**: a title bar and a field list, one field per line | fields appear one by one as the story names them |

**No text over text.** The fastest way to lose a viewer is a label sitting on another label, a
tag running into a box, or a line falling off the right edge. Before writing a scene, lay out its
zones on paper: the title band at the top, the diagram in the middle, captions under it, the
footer line at the bottom, and a reserved strip for any gauge or legend. Then keep to these:

- Estimate every tag's width before placing it: about 14 px per character for a 24 px mono
  face, 12 px at 20 px. A tag that would cross a box or the stage edge gets shorter words, a
  smaller face, or two lines (`white-space: normal` with a fixed width), never a prayer.
- Two elements that are on screen at the same time never share a rectangle. If a note must sit
  where an earlier tag was, fade the earlier one out first.
- A time band, a frame or any full-width element owns its rows: nothing else is placed inside
  its vertical range.
- Keep 8 px of air between any tag and the nearest box edge, and 16 px between stacked lines.
- When a reviewer reports an overlap, fix every sibling scene built the same way, not just the
  one they saw: the same layout mistake was almost certainly copied.

Rules that keep it a story and not a spec dump:

- One diagram per beat, and the beat is still about one thing: the arrow that is missing, the state
  nobody reaches, the dependency that goes the wrong way. Dim everything the point does not need.
- Draw it in the film's look (the same boxes, cables, fonts and colours), never as a pasted image
  or a different visual language. The viewer should not notice the beat "became a diagram".
- Labels are one to three words. Method names and field names are fine; sentences are not.
- Animate the reading order. A sequence diagram that appears whole is a slide; one whose arrows
  land in time with the story is a mechanism.
- A before/after pair (today's sequence, then tomorrow's) is the strongest use: same actors, same
  layout, one arrow changes. Use it whenever the source proposes a change.
- **Never draw two separate requests as one flow.** When the thing being explained spans a gap in
  time (a call that returns, then a webhook hours later; a job queued, then run; a message sent,
  then answered), the gap IS the mechanism. Show it: an activation bar on the lifeline that ends
  when the first request returns, a "time passes" band with a clock across every lifeline, then a
  second activation that starts cold. Whatever survives the gap (a database row, a queue, a file)
  gets its own lifeline, and it is the only thing left bright while time passes. A viewer who saw
  the send and the reply as one arrow will never understand why state has to be stored.

## 5. Render it

**Preferred: a Motion film.** Call the Artifact tool's `quickstart` with intent `other`; when the
result lists a Motion type, create the film from its `type_url` and follow the type's own
instructions. Decide the look yourself (never ask the three style questions when you are running
unattended, and even with a user present, prefer one short line stating your pick): a dark ground
for a meeting screen, one accent for "good", one warning hue for "broken", a mono face for
identifiers. Length is what the beats need (state it in your one line), not the type's default.
Each beat is one scene with one subject; the end card holds three seconds or more.

The film's chapters are the beats, so the presenter can pause and jump between them.

**Fallback: a click-to-advance page**, when there is no Motion type, or the user wants to control
the pace by clicking. `assets/clicker-template.html` is a working presenter (a 1920×1080 stage
scaled to the window, click / Space / arrows to advance, each beat a scene with `init` and
`render(t)`): replace its scenes with yours and publish it as a plain artifact. The scene code
style is the same as a Motion scene, so a film can be ported to it in minutes.

Either way, draw mechanisms: where data flows, which box talks to which, what changes between the
before and the after. A box labelled "cache" says less than the arrow that disappears when the
cache is removed.

## 6. What you reply

The user asked to understand, not to read. Keep the reply to this:

1. One line and the link. If the artifact is private, say the audience cannot open it until shared.
   One more line at most on how to watch it (it starts muted, the chapters are the beats).
2. **Three doors** — three lines, each a precise pointer into the source (section, file, comment,
   figure) and why it is worth opening.
3. **What this story skips** — one line, honest, so nobody mistakes the film for the whole truth.

Under two hundred words in all. No beat list, no summary, no restating the source. If the user
asks for the beats, give them.

## 7. Honesty

The film will be shown to people who were not in this conversation. So:

- Every fact on screen comes from the source or from code you read. If you inferred the "first
  idea" or a motive, keep it generic enough to be true ("what anyone would try first").
- An open question stays open on screen, shown as the options it leaves, never asked as a question.
- A number that matters is exact (sixteen event kinds, three tries), or it is not shown.
- If the source itself is wrong somewhere and you can show it, that is a finding beat, worded as
  "the doc says X, the code does Y", not as blame.

## 8. Audience knob

Default audience: a junior who joined today. If the user names another ("for the CEO", "for the
on-call engineer", "for my mum"), keep the arc and change three things: which seven things are
named, which metaphor is native to them, and how technical the tags are. The budget does not grow.

For a junior, or anyone who "has no clue what this is about", four extra rules, because they are
where every expert explanation loses them:

- **Who's who comes first.** Beat 1 introduces the characters and what each one does, with a
  picture, before any problem is stated. A viewer who does not know what the system is cannot
  care what is wrong with it.
- **Plain words first, the real name under them.** Every concept arrives as something a person
  would say ("a sticky note the receptionist keeps"), and the code's name appears only after the
  picture, as a small tag: `in the code: subscription row`. Never the reverse. Never a term that
  has not had its picture yet.
- **Explain the one thing the idea stands on.** Most designs rest on one fact the expert forgot
  is not obvious (a request ends and the server forgets; a queue is read later by someone else;
  a cache can be stale). Give that fact its own beat, with a picture, before the idea that needs it.
- **Name the idea after showing it.** The word "subscription", "idempotency", "consensus"
  appears on the beat after the mechanism has been watched working, as the label on what the
  viewer already understands.
