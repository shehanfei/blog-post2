# Blog Post 2: What Skills Are Companies Actually Asking For?

This repository contains the R Markdown source and code for a blog post that
scrapes the current "Ask HN: Who is hiring?" thread on Hacker News with `rvest`,
extracts which technical skills appear most often in job postings, and turns that
into a recommendation for what to study.

## Data Source

- **Site:** Hacker News (`news.ycombinator.com`), the monthly "Ask HN: Who is
  hiring?" thread.
- **Access method:** `rvest::read_html()` on the thread's comment page. The current
  thread's ID is looked up automatically via Hacker News's public Algolia search
  API (`hn.algolia.com`), which is a documented, keyless API endpoint, not scraping.
- **Ethics:** Hacker News's `robots.txt` does not restrict crawling of comment pages,
  the content is posted publicly and voluntarily by hiring companies, and only one
  request per run is made against the page (a raw HTML snapshot is saved locally so
  the analysis can be re-parsed without re-requesting the page).

## Contents

- `hn_hiring_skills.Rmd` — R Markdown source: full write-up, the `rvest` scraping
  code, keyword-based skill extraction, and the resulting chart.
- `hn_hiring_skills.html` / `index.html` — Knitted output.
- `data/raw/` — Raw HTML snapshot(s) of the scraped thread, one per run, named by
  thread ID.
- `results/skill_counts.csv` — Cleaned, tidy output: one row per skill, with counts,
  share of postings, and source/access-date provenance columns.

## How to Reproduce

1. Clone this repository.
2. Open `hn_hiring_skills.Rmd` in RStudio.
3. Install required packages if needed:
   ```r
   install.packages(c("rvest", "dplyr", "stringr", "purrr", "tibble",
                       "ggplot2", "here", "httr2"))
   ```
4. Click **Knit** (or run `rmarkdown::render("hn_hiring_skills.Rmd")`).
5. Because the thread ID is looked up automatically, re-running this on a later
   date will scrape whichever month's thread is current at that time, and the
   chart and CSV will reflect that month's postings.

## Published Post

[Add your GitHub Pages / blog URL here once published.]
