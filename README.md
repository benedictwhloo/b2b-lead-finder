# b2b-lead-finder

A single-file browser tool for researching B2B leads. Enter a company name or URL and get back a structured profile with key contacts, exportable to CSV.
 
Powered by the Anthropic API with live web search — no database subscriptions, no scraping.
 
---
 
## Usage
 
No install required. Clone the repo and open the file:
 
```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
open b2b-lead-finder.html
```
 
> **Note:** The tool calls the Anthropic API from the browser. It works out of the box inside Claude.ai. To self-host, add your API key to the `fetch` headers in the script.
 
### Single lookup
 
Enter a company name and optionally a website URL, then hit **Research leads** or press Enter.
 
### Bulk lookup
 
Click **+ Add multiple companies at once** and paste one company per line. Results come back sequentially — the activity log shows live progress and elapsed time per step.
 
---
 
## Output
 
Each result includes:
 
- Company profile — industry, size, HQ, founded, website, LinkedIn, email pattern
- Up to 3 key contacts — name, title, email, phone, LinkedIn (public data only)
- Confidence rating — `high` / `medium` / `low`
 
### CSV export
 
One row per contact. If a company has multiple contacts, company fields are repeated across rows for easy CRM import.
 
| Field | Description |
|---|---|
| `company_name` | Official name |
| `website` | Company website |
| `industry` | Sector |
| `company_size` | Headcount or range |
| `location` | HQ city, country |
| `founded` | Founding year |
| `email_pattern` | e.g. `firstname@company.com` |
| `phone` | Main switchboard |
| `linkedin` | Company LinkedIn page |
| `confidence` | Data quality rating |
| `contact_name` | Full name |
| `contact_title` | Job title |
| `contact_email` | Direct email if found |
| `contact_phone` | Direct phone if found |
| `contact_linkedin` | Personal LinkedIn |
| `contact_source` | Where the data was found |
 
---
 
## Notes
 
- Only surfaces **publicly available** information — no private or unlisted data
- Each lookup takes **20–40 seconds** due to live web searches; bulk runs are sequential
- Results are **not persisted** — export before closing or refreshing
 
---
 
## Stack
 
- Vanilla HTML/CSS/JS — no build step, no dependencies
- [Anthropic Messages API](https://docs.anthropic.com/en/api/messages) with `web_search_20250305`
- [DM Mono](https://fonts.google.com/specimen/DM+Mono) + [Fraunces](https://fonts.google.com/specimen/Fraunces)
 
---
 
## License
 
MIT
