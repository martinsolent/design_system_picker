# Design System Picker

A single web page for browsing open source design systems, previewing their look on the same sample screen, and copying a ready-made prompt for building a prototype with an AI coding tool.

It's for anyone picking a visual style for a prototype, whether they're vibe coding with an AI tool, doing user experience design, or just comparing design systems before choosing one.

## Why it exists

Choosing a design system is usually the first decision in a prototype, and it's hard to compare them. Each one has its own documentation site, its own terms and its own licence. This page puts over 100 open source systems in one place. You see them side by side and copy a prompt your AI tool can follow straight away.

## What's in it

- **105 open source design systems**, each with its licence and links to its documentation and source code.
- **A live preview** for 41 of them. A sample "Study planner" screen is restyled in that system's colours, fonts and shapes. It includes tabs, form fields, an error message, radio buttons, a checkbox, a switch, buttons and cards.
  - **Full previews** (12 systems) include light and dark themes where the system has one.
  - **Starter previews** (29 systems) use the system's main colour, font and corner shapes with generic greys.
  - Systems without a preview show a plain wireframe, plus their licence, links and a prompt.
- **Design tokens** you can click to copy, with a WCAG contrast check for each colour pairing.
- **A prompt builder.** Describe what you're building and the page writes a prompt naming the design system, its tokens and accessibility rules. You can also copy the tokens as CSS variables.

## How to use it

1. **Find a system.** Search by name or licence, or filter the list by *With preview*, *Plain HTML*, *Web components* or *React*.
2. **Preview it.** Select a system to restyle the sample screen. Switch between *Light* and *Dark*, and between *Phone* and *Wide* widths.
3. **Check the details.** Read who makes it, its licence and what it's good for. Use *Official docs* and *Source code* to find out more.
4. **Check the colours.** Click any token to copy its value. The contrast check shows whether text colours pass WCAG AA.
5. **Build with it.** Under *Build with it*, describe your app in a sentence. Choose *Prompt* or *CSS variables*, then select *Copy*.
6. **Paste the prompt** into Claude or another AI tool. It asks for one self-contained HTML file that uses the design system, meets WCAG 2.2 AA, works at phone width first and uses realistic sample content.

### Tips for choosing

- **Plain HTML and CSS** systems (such as Bootstrap, GOV.UK, Primer and daisyUI) are the easiest to use in a single-file prototype, because the real library can load from a CDN link.
- **Web components** systems (such as Shoelace, Carbon and Fluent) can often load from a CDN too.
- **React** systems need a build setup. For single-file prototypes, the prompt asks the AI tool to recreate their look with plain CSS instead.

You can link straight to a system by adding its ID to the address, for example `#govuk`, `#shadcn` or `#material-ui-mui`.

## Running it

The whole tool is one file, `index.html`, with its styles and scripts inside. There's no build step and nothing to install.

- **Locally:** download `index.html` and open it in a browser.
- **On GitHub Pages:**
  1. Add `index.html` and this `README.md` to a repository.
  2. Go to **Settings → Pages**.
  3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and the `/ (root)` folder, then save.
  4. After a minute or two the page is live at `https://<your-username>.github.io/<repository-name>/`.

The page loads fonts from Google Fonts. It still works offline, but previews will use your device's fonts.

## Things to know before you use a system

- **Previews are approximations.** They're drawn from each system's colours, type and shapes. The real component library isn't loaded, so details will differ.
- **Token values are a starting point.** Confirm colours, fonts and sizes in the official documentation before you rely on them.
- **Licences were checked on 17 November 2026,** from each project's own repository. Licences can change, so read the current one before you publish or sell anything built with a system.
- **Some licences have sharing conditions.** MIT, Apache, BSD and CC0 let you use the code freely. GPL, LGPL, EUPL and MPL ask you to share changes under the same terms in some situations.
- **A few licences rest on weaker evidence.** Entries marked "declared in package.json" have no separate licence file.
- **Maintenance wasn't checked.** Look for recent activity on the source code page before committing to a system.
- **A licence covers the code, not the brand.** Names, logos and some fonts stay protected. Never present a prototype in a government, health service or company style as if it were the real service.

## How the list was built

The 12 original systems were chosen as widely used open source examples. The rest come from the community list [awesome-design-systems](https://github.com/alexpate/awesome-design-systems). A system was included only if its source code is public and its licence could be confirmed as open source. Systems were left out if they publish no source code, use a source-available licence (such as the Elastic License, the Functional Source License or Commons Clause), restrict who can use them, or have a licence that couldn't be confirmed.

## Adding or editing a system

All the data is in the `<script>` block of `index.html`:

- `S` holds the systems with full previews: colours for light and dark themes, font, corner radii, button size and component styles.
- `L` holds starter-preview settings (main colour, font, radii, button size, description), keyed by the system's name in the directory.
- `D` is the directory of every other system: `id`, `name`, `lic` (licence), `site` and `repo`.

To add a system, add an entry to `D` with its licence and links. To give it a preview, add matching settings to `L` (or a full entry to `S`). Check that the licence is open source by reading the licence file in the project's repository.

## Accessibility

The page supports keyboard navigation with visible focus states, follows your device's light or dark setting, respects reduced-motion settings and works at phone width. If you find a barrier, please open an issue.
