# Set up a project (all in one)

The same setup as `setup-project.md`, with one extra first step: it downloads this kit's
`mise.toml` to the project root, installs the pinned tools (`bun`, `just`, `node`, `uv`), and
installs the vendored agent skills. Then it sets up the Matt Pocock skills with local issues and
does the rest of `setup-project.md`: the project-docs and tools sections in `CLAUDE.md`, the
docs index, the shared HTML assets, the ruff config and `.gitignore`.

**How to use:** copy the block below into a new session at the project root. You need `mise`
installed.

HTML documents load `docs/shared/globals.css` and `docs/shared/doc.js`. The prompt downloads
them from this kit's `assets/` folder on GitHub (`chuan-khuna/altr-kit`, branch `main`).

---

````text
First, set up mise. Download the shared mise.toml to the project root. If mise.toml already
exists, show me the differences and ask before you overwrite it:

  curl -fsSL -o mise.toml https://raw.githubusercontent.com/chuan-khuna/altr-kit/main/tools/mise.toml

Then trust it, install the tools and install the agent skills:

  mise trust
  mise install
  mise run skills

Next, run /setup-matt-pocock-skills and use local markdown (.scratch/) to store issues. If the
slash command is not available yet in this session, read the setup-matt-pocock-skills SKILL.md
that `mise run skills` installed and follow it.

Edit CLAUDE.md (create it if it's missing) and add the sections below alongside the Agent
skills block. Then create docs/documents/INDEX.md as an empty starter index, and download
the shared HTML assets into docs/shared/:

  mkdir -p docs/shared
  curl -fsSL -o docs/shared/globals.css https://raw.githubusercontent.com/chuan-khuna/altr-kit/main/assets/globals.css
  curl -fsSL -o docs/shared/doc.js https://raw.githubusercontent.com/chuan-khuna/altr-kit/main/assets/doc.js

Also download the shared ruff config to the project root:

  curl -fsSL -o ruff.toml https://raw.githubusercontent.com/chuan-khuna/altr-kit/main/tools/ruff.toml

Set up .gitignore from the shared template. If .gitignore is missing, save the template as
.gitignore. If it exists, append only the template lines it lacks, under their section
comments, and keep every existing line:

  curl -fsSL https://raw.githubusercontent.com/chuan-khuna/altr-kit/main/tools/gitignore

## Project docs

### Documents

Documents about this project, including how it is implemented, live in
docs/documents/<slug>.md (or .html). docs/documents/INDEX.md is the entry point: it lists
every document as one bullet, `- Title — one-line summary`.

- Read the index before working on an area, and open the documents relevant to it.
- When you add, rename or remove a document, update INDEX.md in the same change.
- Keep documents in step with the code they describe: if a change makes a document wrong,
  fix the document in the same change.

### HTML documents

When you write a document in `docs/` as HTML, follow the page contract at the top of
`docs/shared/doc.js`. Linking `globals.css` and `doc.js` gives the page its themes, Shiki
highlighting, Pele diagrams, table of contents and glossary cards.

- Shared code: link `docs/shared/` files by relative path; add new shared CSS/JS there.
- Colour: write every colour in `oklch()`; derive with `color-mix(in oklch, …)`.
- Glossary: define each term once, in `<dl class="glossary">` or a table marked
  `data-glossary`, with id `term-<slug>`. Link its first use in each `h2` section with
  `<a class="term" href="#term-<slug>">`, only for terms that have an entry.
- Technical manuals (setup guides, runbooks, how-to, API guides): ASD-STE100 at about 60%.
  Numbered steps, one action each, starting with a verb; condition before action; active
  voice; 20 words or fewer; warnings before their step; the glossary term every time.
  Explanations may read naturally. Thai text follows the same principles.

### Records

Discussion records live at docs/records/yyyy-mm-dd-<slug>.md, dated the day the discussion
took place. Each record captures one discussion: what was discussed, what was decided, and
any open questions.

## Tools

### Python

Use `uv` for everything Python: `uv run <script>`, `uv add <pkg>`, `uv sync`. Run it
instead of calling `python`, `pip` or `venv` directly. Lint and format with ruff
(`uvx ruff check`, `uvx ruff format`), configured by `ruff.toml` at the project root.

### Node

Use `bun` as the package manager (`bun install`, `bun add`, `bun run`). Fall back to `npm`
only when bun can't do the job.

When you set up a Node project or add a package manager config, set a minimum release age
of 7 days for both tools, so freshly published (possibly compromised) versions are never
installed:

- `bunfig.toml`:
  ```toml
  [install]
  minimumReleaseAge = 604800 # 7 days, in seconds
  ```
- `.npmrc` (needs npm >= 11.10):
  ```ini
  min-release-age=7
  ```
````
