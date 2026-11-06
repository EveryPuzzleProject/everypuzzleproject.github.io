# everypuzzleproject.org

The home page of the [Every Puzzle Project](https://github.com/EveryPuzzleProject),
served by GitHub Pages at https://everypuzzleproject.org (`CNAME`). Plain HTML, CSS
and JavaScript; no build step.

| File | What it is |
|---|---|
| `index.html` | The home page: the mission, the four steps from a publication to the corpus, the publications board, ways to help, the three newest posts. |
| `publications.json` | The registry the board is drawn from: one entry per publication with its years, repo, status page, and which public TSV gives its counts and how to read it. Add a publication here and the board picks it up. |
| `blog/` | The project's blog: one HTML file per post, `index.html` listing them newest first, and `img/` for their illustrations (public-domain scans and our own figures). Posts have no byline and link the review site at blitz.xwordapp.com. The old addresses under blitz.xwordapp.com/blog/ redirect here. |
| `img/social-card.png` | The link-preview image (1200×630), made by `img/social_card.py` from the public-domain Judge cover beside it; rerun the script to change the words. |
| `site.css` | The shared stylesheet: palette, type, and the `.epp-header` bar. The publication status pages link to it so the sites look like one family. |
| `CNAME` | The custom domain. Keep it. |

The publication status pages (`/judge/`, `/bostonglobe/`, `/newyorkworld/`, `/bell/`,
`/games/`, `/collegian/`) are separate repos, each published as its own GitHub Pages
project site under this domain.

## The publications board

`index.html` fetches `publications.json`, then each publication's TSV, at load. For each
source it counts rows by the named column and groups the states as the registry says;
a count with no `states` is the number of rows. If a fetch fails the card still renders
with its static text and a link to the status page. Only metadata is shown: dates,
counts, states. Never clues or grids.

## The shared header

Status pages built by their repo's `tools/render.py` should load `site.css` and start
with this bar, which reads "Every Puzzle Project · *Page name*" and links home:

```html
<link rel="stylesheet" href="https://everypuzzleproject.org/site.css">
...
<header class="epp-header"><div class="wrap">
  <a href="https://everypuzzleproject.org/">Every Puzzle Project</a>
  <span class="epp-page">Judge</span>
  <nav><a href="https://github.com/EveryPuzzleProject/judge">Repo</a></nav>  <!-- optional -->
</div></header>
```

`site.css` also defines `.wrap` (the centred column), `h1`, `h2`, `.muted` and the colour
variables (`--bg`, `--surface`, `--ink`, `--muted`, `--line`, `--accent`, `--good`, `--warm`,
`--bad`), with a dark scheme that follows the system preference. A page can keep its own
`<style>` for everything else.
