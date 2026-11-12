# Publications dashboard

A one-page dashboard of papers, co-authors and research themes. It's plain HTML with no build step, and it runs on GitHub Pages.

## Put it online

1. Create a new repository on GitHub (for example `publications`).
2. Upload `index.html` and `papers.csv` (**Add file → Upload files**), then commit.
3. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, and save.
4. After about a minute the site is live at `https://<your-username>.github.io/publications/`.

## Update papers

Edit `papers.csv`, either in GitHub's editor (pencil icon) or by uploading a new file with the same name. The page always reads the latest version, so a normal refresh shows the change.

| Column | What to put |
|---|---|
| `id` | Any number |
| `title` | Paper title (keep the quotes if it contains a comma) |
| `authors` | Surnames separated by `;`, e.g. `Arayssi; Itani; Yassine` |
| `journal` | Journal name |
| `submission_id` | Manuscript number from the journal (optional; shown under "Details" with a Copy button) |
| `theme` | e.g. ESG, Banking, Gender, Energy, Markets, Governance (new themes get a colour automatically) |
| `status` | `Submitted`, `With editor`, `Under review`, `Revise and resubmit`, `Accepted`, `Rejected`, `Withdrawn`, `Can't confirm` (or `Published`). Add a round like `Under review R1` to show an R1 badge. |
| `submitted` | Submission date, `DD/MM/YYYY` or `YYYY-MM-DD` (optional) |
| `last_update` | Date of the latest news from the journal, same formats (optional) |
| `comments` | Editor's note or decision letter summary (optional; shown under "Editor note") |
| `link` | URL to the paper or submission page (optional; makes the title clickable) |

Active papers (Submitted, With editor, Under review, Revise and resubmit) with no news for 60 days get a "No news in N days" flag. Change `NUDGE_DAYS` in `index.html` to adjust. `Can't confirm` papers are never flagged and are left out of the acceptance rate.

When saving from Excel, choose **CSV UTF-8** so accents and apostrophes survive (the page can also read the older Windows format).

Once some papers are `Accepted` or `Rejected`, the fourth headline number switches to the acceptance rate.

## Preview on your computer

If you double-click `index.html`, the browser blocks it from reading the CSV, so the page asks you to choose the file instead. To see the page as it will look online, run `python3 -m http.server` in the folder and open http://localhost:8000.

## Customise

At the top of the `<script>` in `index.html` are `OWNER` (your surname, which is left out of the co-author network), `OWNER_INITIALS`, and the colours for statuses and themes.
