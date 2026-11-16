# AGENTS.md

## Project
This site explains the block colors of Linglox, rewritten with clearer
explanations and everyday comparisons. Write so that a reader with no
prior knowledge can follow it.

## Writing rules
- Adult tone. Plain, direct, matter-of-fact.
- No toys, cartoon characters, or "imagine a..." framing.
- No em dashes. Use periods or commas.
- Use everyday words first. If a technical term is needed, describe it
  plainly, then put the term in parentheses once.
- No sentence over about 25 words. No paragraph over 2 sentences.
- Never invent puzzle rules, answers, or personal experiences.

## Sources
- `sources/` holds the author's notes, one file per color, plus
  `glossary.md` for core terms. Read-only. Never edit it.
- Create or change a file in `sources/` only when the author asks for it
  and gives the exact text. Save it word for word.
- Facts in `sources/` are confirmed. State them plainly.
- If a fact is not in `sources/`, leave it out and ask the author in your
  reply. Do not guess.
- A "Like" line or an example that appears in the notes is
  author-approved. Use it as written.
- If the notes have no "Like" line, write one yourself (see template).
  If the notes have no examples, write your own. Each example must be a
  short, plain word pair that correctly follows the rule it shows.

## Files
    /
      AGENTS.md
      index.html
      glossary.html
      colors/
        index.html
        <color-name>.html
      assets/
        style.css
      sources/
        glossary.md
        <color-name>.md

- File names: lowercase, words joined by hyphens.
- Relative links only, e.g. `../glossary.html` from inside `colors/`.
- Never link to the AI tool's address or any absolute URL for a page on
  this site.
- No images or screenshots. Use CSS shapes.
- One shared stylesheet: `assets/style.css`. No inline styles except the
  `--block-color` variable, set to the page's hex code on the info card
  swatch and on each block component.
- Static files only, so the site works on GitHub Pages.

## Source file format
Each color has one file: `sources/<color-name>.md`.

    # <Color name>
    - hex: #xxxxxx, rgb: r, g, b
    - Meaning: one plain sentence.
    - Like: one everyday comparison (optional).

    ## High
    - Rule: one plain sentence.
    - Example: hint -> answer (optional)

    ## Middle
    - Rule: ...
    - Example: ... (optional)

    ## Low
    - Rule: ...
    - Example: ... (optional)

To add a color, the author provides this file. The AI then builds the
page from it, following the color page template.

The "Like" line in the notes does not begin with the word "Like".
The template adds the label. Write only the comparison itself.

## Block component
All examples use this component.

- Dark plate on top with the hint word. Answer box below.
- Filled (answer written): answer shown in green.
- Empty (answer not written yet): blank plus a number in brackets,
  like `____ (3)`.
- `--block-color` takes the page's hex code.

Filled:

    <div class="block" style="--block-color: #F8F8F8">
      <div class="block-hint">sea</div>
      <div class="block-answer filled">see</div>
    </div>

Empty:

    <div class="block" style="--block-color: #F8F8F8">
      <div class="block-hint">sea</div>
      <div class="block-answer">____ (3)</div>
    </div>

Write the `.block` styles once in `assets/style.css`.

## Visual style
- Clean, modern reference-site look. Generous spacing, readable type.
- Fonts: system font stack only. No external fonts or libraries.
- Page background: soft off-white. Text: near-black. One accent color:
  deep indigo (#4B4FA3), used for links, heading accents, and buttons.
- Define all colors, spacing, and radii as CSS variables at the top of
  `assets/style.css`. Use the variables everywhere.
- Every page has the same header: site name on the left, navigation
  (Colors, Glossary) on the right, current page highlighted.
- Every page has the same footer: site name and the navigation links.
- The footer stays at the bottom of the window on short pages. Use a
  full-height page layout (min-height: 100vh, with the main content area
  growing to fill the space).
- Content sits in a centered column, max width about 760px.
- Cards: white background, thin border, rounded corners, light shadow.
  Use cards for the info card, for each height section, and for index
  entries.
- `colors/index.html` shows each color as a card with its swatch, name,
  and one-line summary, in a responsive grid.
- Each height section has a small colored tag (High, Middle, Low) in its
  heading.
- The block component stays high contrast: dark plate, light answer box,
  green text only for filled answers.
- Mobile first. Layout must work from 360px wide. Navigation wraps or
  stacks on narrow screens.
- Support dark mode with `prefers-color-scheme`. Swatches keep a visible
  border in both modes.
- Subtle hover states on links and cards. No animation beyond simple
  transitions of about 150ms.
- No images, icons from external sources, or decorative elements that
  carry no information.

## Color page template
File: `colors/<color-name>.html`. Use this exact order.

Top of file, as an HTML comment: title, type: color, hex, rgb.

1. Title and info card (swatch, hex, rgb). Give the swatch a visible
   border so light colors stay visible.
2. Intro, 2 sentences. Sentence 1 is always: "In Linglox, a puzzle block
   shows a hint word and asks you to type a related word back." Sentence 2
   says what the color means, from the notes. Link "puzzle block" to
   `../glossary.html` on first use.
3. **Like:** one everyday adult comparison for the color's whole theme,
   one sentence, placed directly after the intro. Use the notes' line if
   there is one. Otherwise write a short, concrete comparison that
   matches the color's meaning.
4. Three sections: High, Middle, Low, in that order. Each starts with an
   h2 heading (High, Middle, or Low). Under the heading, in this order,
   without repeating the height name:
   - The rule in one plain sentence.
   - **Example:** a bold label on its own line, directly above a block
     component with the hint and answer.

Rules:
- About 100 words of body text, not counting examples.
- Labels use identical wording on every page: "Like:" and "Example:".
- One "Like" line per page, never one per height.

## Other pages
- `glossary.html` defines core terms (block, height, chain, prompt).
  Definitions come only from `sources/glossary.md`. Color pages do not
  re-define these terms. They link to the glossary.
- The home page and `colors/index.html` may contain the site name,
  navigation, and one-line descriptions of what each section is. They must
  not state any puzzle facts.

## Adding a new page
1. Read this file and use an existing color page as the model.
2. Read the matching file in `sources/`.
3. Write the page using the template above.
4. Add it to `colors/index.html` with a one-line summary.
5. Run the checklist below.
6. In your reply, list anything left out because it was not in `sources/`.

## Checklist
- About 100 words of body text, no long paragraphs.
- Intro sentence 1 matches the fixed wording.
- One "Like" line, directly after the intro.
- High, Middle, Low all present, in that order, each with one h2 heading
  and no repeated height label.
- Labels match exactly.
- No em dashes, no childish framing.
- All links are relative and work.
- No images. Examples use the block component.
- Page is listed in `colors/index.html`.
- Every example follows the rule it is shown under.
- Header, footer, and navigation match the other pages.
- Footer sits at the bottom of the window on every page.

## Never
- Edit files in `sources/` unless the author gives the exact text.
- Invent puzzle rules, answers, or personal stories.
- Add story, lore, or game-world details (realms, tutorial, where a color
  appears). Describe only what the color does.
- Re-explain core terms on color pages.
- Add a page without updating the index.
- Add decoration the template does not call for.