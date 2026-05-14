# The AI "Hallucinations" Project

A dataset of 100+ AI hallucinations — their prompts, the models that produced them, and the archival source that provided the accurate response. A record of AI hallucinations not as bugs, but as cultural artifacts that reveal how algorithms distort or erase the histories of marginalized communities.

## What's in the repository

```
.
├── data/                                              # The published datasets
│   ├── model_hallucinations_BlackAmericanHistory.csv
│   └── model_hallucinations_PuertoRicanHistory.csv
├── web-dev-code/                                      # Project website (static HTML/CSS/JS)
│   ├── index.html        # Home — dataset table + charts
│   ├── about.html        # Project statement + team
│   ├── methods.html      # Methodology narrative
│   ├── data.html         # Dataset download
│   ├── style.css
│   └── script.js
└── README.md
```

## The datasets

Two thematic corpora, same schema:

| File | Records | Topic |
|---|---|---|
| `data/model_hallucinations_BlackAmericanHistory.csv` | 103 | Black American history, art, literature, institutions, the African diaspora |
| `data/model_hallucinations_PuertoRicanHistory.csv` | 48 | Puerto Rican history, Nuyorican literature and activism, Puerto Rican feminism, historical institutions |

### Schema

| Field | Type | Description |
|---|---|---|
| `id` | int | Unique record identifier |
| `prompt_id` | string | Identifier for the prompt (e.g. `P001`) |
| `prompt` | string | The exact prompt sent to the model |
| `model` | string | One of `gpt-5`, `gemini-2.5-flash`, `claude-haiku-4-5` |
| `model_response` | string | The model's full reply |
| `date` | string | When the response was collected (`YYYY-MM-DD_HH-MM-SS`) |
| `error_type` | string | Controlled vocabulary (see below) |
| `error_description` | string | Free-text explanation of what's wrong |
| `verification_source` | string | URL or citation used to refute the response |
| `category` | string | Topical category for the prompt |

### Error type vocabulary

- `misattribution` — assigns a work, statement, or action to the wrong person or organization
- `erasure_by_omission` — omits real, relevant figures or sources that should be mentioned
- `adjacent_error` — close to correct but not what was asked (nearby location, related institution, associated work)
- `invented_figure` — fabricates a person, work, or event that never existed
- `temporal_error` — wrong dates or wrong historical period
- `geographical_error` — wrong location (city, state, country, institution)
- `factual_error` — incorrect detail about real people, works, or events

## Methodology

A short version (full narrative on [methods.html](web-dev-code/methods.html)):

1. **The corpus** — curated prompts across Black American and Puerto Rican history, each with a known, verifiable answer.
2. **The probe** — every prompt submitted to three models (`gpt-5`, `gemini-2.5-flash`, `claude-haiku-4-5`) under identical conditions.
3. **The reading** — each response read against its verification source; errors classified using the controlled vocabulary above and described in plain language.
4. **The output** — annotated records exported to the two CSVs in `data/`.

## Viewing the website locally

The site is static — no build step. Open `web-dev-code/index.html` through a local web server (the `fetch()` calls that load the CSVs won't work from `file://`).

With VS Code Live Server:

1. Install the **Live Server** extension
2. Right-click `web-dev-code/index.html` → **Open with Live Server**

Or, with Python:

```bash
python -m http.server 8000
# then open http://localhost:8000/web-dev-code/
```

## Team

- **Sasha Richardson** — Project Manager · Technical Lead
- **Michelle Santiago Cortés** — Outreach & Promotion Lead
- **Christian Condo Gilkes** — Research Lead

## Links

- Project Are.na board: <https://www.are.na/michelle-sc/ai-hallucinations-project>
- Repository: <https://github.com/srichardson0/AI_Hallucinations_Project>
