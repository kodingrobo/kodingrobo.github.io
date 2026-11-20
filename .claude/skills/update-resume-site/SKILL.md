---
name: update-resume-site
description: Use when adding or changing a job, role, achievement, or skill on Angela Ding's personal website (the static HTML site in /Users/angelading/Projects/claude_play). Covers the Experience timeline and the Skills sections on the Home and Experience pages.
---

# Update the résumé site

The site is plain HTML/CSS/JS with no build step, at `/Users/angelading/Projects/claude_play`:

- `index.html`: Home. Contains a **Skills** section with two cards: *Languages* and *Tools*.
- `experience.html`: Experience. Contains the **timeline** of roles, then a **Skills** section with four cards: *Languages*, *Data & streaming*, *Cloud*, *Build & delivery*.
- `css/styles.css` already styles everything below. Don't add new CSS for these changes.

Always read the current file before editing. Angela edits the HTML by hand, so the text may differ from earlier versions. Keep her wording unless she asks for a change.

## Gather the details first

Before editing, make sure you have:

- **New role:** title, company, start and end dates (month + year), 2–4 achievement bullets, and the tools used. If any are missing, ask.
- **New skill:** the exact name to display, and which card it belongs in (see "Adding a skill" below). If the card isn't obvious, ask.

## Adding a role to the timeline (`experience.html`)

Roles live in `<ol class="timeline">` and are ordered **newest first**. Insert the new `<li>` in date order. Copy this structure exactly:

```html
<li class="tl-item reveal">
  <span class="tl-date">Mon YYYY – Mon YYYY</span>
  <div class="tl-body">
    <h3>Job Title, Team</h3>
    <p class="tl-org">Company</p>
    <ul>
      <li>Achievement bullet, written as a full sentence ending with a period.</li>
    </ul>
    <ul class="tags" aria-label="Tools">
      <li>Tool</li><li>Tool</li>
    </ul>
  </div>
</li>
```

Conventions:

- **Dates:** three-letter month plus year, separated by an en dash with spaces: `Jun 2021 – Sep 2026`. Use `Present` for a current role.
- **Bullets:** lead with a strong verb, and include numbers where available (latency, volume, users). Apostrophes and quotes are plain text. Links use a normal `<a href>`.
- **Escaping:** write `&amp;` for `&` in visible text.
- The newest role automatically gets the filled timeline dot (CSS `:first-child`), so there's nothing to change there.

Then check the text that summarizes her career and update it if the new role makes it out of date:

- `experience.html`: the `.eyebrow` year range (`Experience · 2016–2026`), the `<h1>` ("10 years of…"), and the `.lede` sentence.
- `index.html`: the hero `.headline` and the About bio paragraphs.
- Propose wording for these to Angela rather than rewriting them silently.

## Adding a skill

Each skill is one chip: `<li>Skill name</li>` inside a `<ul class="tags">`. Chips sit on one line, back to back, with no spaces between them.

1. **Home page (`index.html`)**: two cards.
   - *Languages*: programming languages and frameworks.
   - *Tools*: everything else.
2. **Experience page (`experience.html`)**: four cards. Add the skill to the best fit:
   - *Languages*: programming languages and frameworks
   - *Data & streaming*: Kafka, Flink, Spark, Hive, Hadoop, Snowflake…
   - *Cloud*: AWS services, Docker, Kubernetes…
   - *Build & delivery*: Git, Bazel, Maven, Jenkins, Chef…

   If a skill fits none of these, ask Angela before creating a new card.
3. **Re-sort alphabetically.** After adding the new skill(s), sort the chips in every card you changed into alphabetical order:
   - Ignore case (`bazel` sorts with `Bazel`).
   - Sort by the full display name as shown, so `AWS EMR` and `AWS Lambda` sort together under "A", and `Protocol Buffers (Protobuf)` sorts under "P".
   - Keep each chip's text exactly as it was. Only the order changes.
   - Leave cards you didn't touch, and the per-role tool tags in the timeline, in their current order.

Unless Angela says to add it to only one page, add the skill to **both** pages so they stay in sync. Before adding, search both files for the skill (case-insensitive) to avoid duplicates. Use the same display name on both pages. If she asked for a specific form such as "Protocol Buffers (Protobuf)", use exactly that.

When a skill was used in a specific role, also offer to add it to that role's tool tags in the timeline.

## After editing

- Tell Angela exactly what changed and where, as a short list.
- If the change came from a new résumé, remind her to replace `assets/Resume_Angela_Ding_2026.pdf`. If the file name changes, the two download links in `experience.html` and `contact.html` must change too.
- To preview, she can open `index.html` in a browser, or run `ruby -run -e httpd . -p 8000` in the site folder and visit http://localhost:8000.
