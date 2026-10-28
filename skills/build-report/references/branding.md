# Branding a report

How to make the report look like the client's own, with as few questions as possible. Work through the steps in order and stop as soon as the branding is settled.

If the user says "no branding", "use the defaults" or similar, skip this whole procedure and build with the Quallie.Ai default theme.

Ask every question the way the main skill says: with the ask-user tool when the surface has one, otherwise as a short numbered list in plain text, recommendation first, then wait for the answer.

## 1. Templates first

Call `list_report_templates`.

- If the workspace has templates, name them and recommend one: the default template, or the one whose name and pages best fit this report type. Ask: "Use this one?"
- A template carries the theme (accent colour, fonts, logo), the page structure and the section rhythm, so accepting one settles branding in a single answer. Skip to the end of this procedure.
- If the user wants to see the template first, read it with `get_report` and `get_report_page` and describe its pages and look in a few lines.
- Starting from the chosen template follows the Quallie server's report design rules: pass its id to `create_report` as the template.

If there are no templates, or the user declines them, go on to step 2.

## 2. Ask for one brand example

Ask whether they have brand guidelines, and ask for ONE example of their brand. Recommend, in this order:

1. A screenshot of a recent deck slide (recommended: it shows the colours and type as they are really used).
2. A screenshot of their website.
3. A brand-guidelines PDF also works.

In Claude Code they can give a file path or paste an image; in Cowork and claude.ai chat they attach it to the message.

If they cannot share any example, ask directly for the brand colour as a hex code and the names of their heading and body fonts, then go to step 3 with those.

## 3. Derive the proposal

From the example, work out three things.

**Accent colour.** Pick exactly ONE colour, written as a 6-digit hex like #1F6FEB. Choose the most distinctive brand colour that still has enough contrast on a white background to carry text and bands. Never pick a neutral (white, black, greys, off-whites, beiges). If the brand colour is too pale to read on white, choose its darker brand variant if the example shows one.

**Heading font and body font.** Identify the typeface used for headings and the one used for body text, then map each to the closest face in the report font catalogue. These are the only built-in slugs the server accepts:

| Slug | Family | Style |
|---|---|---|
| inter | Inter | sans |
| dm-sans | DM Sans | sans |
| space-grotesk | Space Grotesk | sans |
| source-serif | Source Serif | serif |
| lora | Lora | serif |
| eb-garamond | EB Garamond | serif |
| playfair | Playfair Display | display |
| fraunces | Fraunces | display |
| bitcount | Bitcount Prop Single | display |
| jetbrains-mono | JetBrains Mono | mono |
| petit-formal | Petit Formal Script | script |

Match on character, not on name: a geometric or humanist sans maps to dm-sans or inter, a grotesque or techy sans to space-grotesk, a book serif to source-serif, lora or eb-garamond, a high-contrast display serif to playfair or fraunces. Keep bitcount, jetbrains-mono and petit-formal for brands that clearly use a pixel, monospaced or script face, and never use petit-formal for body text.

**Custom brand fonts.** A workspace may have uploaded its own fonts. Those appear in the app's font picker, but Claude cannot list them. If the brand font is custom, say so, propose the closest catalogue face for now, and suggest they pick their own font in the Quallie.Ai app's report theme panel. If a custom font slug (it looks like ws- followed by an id) is already in front of you, for instance read back from an existing report's theme, keep it exactly as it is. Never invent one.

## 4. Show the proposal and get approval

Before changing anything, show the proposal in a few lines:

- Accent colour: the hex, and where in the example it comes from.
- Heading font: the slug, and why it is the closest match.
- Body font: the slug, and why it is the closest match.

Ask for approval. Adjust and show it again if they want changes.

Apply it only once the report exists (after `create_report`), with `set_report_theme`. The theme has these fields, described here so you pass the right shapes:

- The accent colour: a hex string in the #RRGGBB form.
- The font: an object with both a heading and a body slug. Always send both halves, the server refuses half a pair.
- The comments colour (optional): one of blue, amber, green, violet, slate or accent. Leave it alone unless the user asks.
- The logo: the media id of an image already uploaded to this report. Claude cannot supply one, see step 5.

## 5. Logo

Say plainly: the logo has to be uploaded in the Quallie.Ai app, in the report theme panel, because Claude cannot upload files to Quallie.Ai. Offer to continue building while they do that.

## 6. At the end of the report

When the report is finished, suggest saving it as a workspace template in the Quallie.Ai app. Next time, branding is one question: "Use this one?"
