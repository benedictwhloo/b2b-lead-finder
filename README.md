# b2b-lead-finder

CopyB2B Lead Finder
An AI-powered B2B lead research tool that uses Claude to search the web and extract structured company and contact data — no scraping, no third-party databases, no API keys required beyond Anthropic's.
What it does
Enter a company name or website URL and the tool returns:

Company profile — industry, size, location, founding year, website, LinkedIn, email pattern
Key contacts — up to 3 decision-makers with name, title, email, phone, and LinkedIn where publicly available
Confidence rating — high / medium / low based on how much verified data was found
Activity log — a live console showing each web search Claude fires, with elapsed timestamps so you can see exactly where time is spent
CSV export — one row per contact, with company details repeated, ready to import into any CRM

How it works
Each search triggers a call to the Anthropic Messages API with the web_search tool enabled. Claude autonomously runs multiple web searches, synthesises the results, and returns structured JSON. No data is stored — everything lives in memory for the session.
Getting started
No build step, no dependencies. Just open the file.
bashgit clone https://github.com/your-username/your-repo.git
cd your-repo
open b2b-lead-finder.html   # or double-click in Finder / Explorer

The tool calls the Anthropic API directly from the browser. Anthropic handles authentication automatically when used within Claude.ai. If you're self-hosting or running outside Claude.ai, you'll need to add your API key to the fetch headers in the script.

Usage
Single company

Enter a company name (e.g. Atlassian) and optionally a website URL
Press Research leads or hit Enter
Results appear as cards with company info and key contacts below
Click Export CSV to download

Bulk mode

Click + Add multiple companies at once
Paste one company name per line
Companies are researched sequentially — watch the activity log for progress

CSV format
Each exported row contains:
ColumnDescriptioncompany_nameOfficial company namewebsiteCompany websiteindustrySector / industrycompany_sizeEmployee count or rangelocationHQ city and countryfoundedFounding yearemail_patternInferred email format (e.g. firstname@company.com)phoneMain company phonelinkedinCompany LinkedIn pagedescription2-sentence company summaryconfidenceData confidence: high / medium / lowcontact_nameContact full namecontact_titleJob titlecontact_emailDirect email if publicly availablecontact_phoneDirect phone if publicly availablecontact_linkedinPersonal LinkedIn URLcontact_sourceWhere the contact info was found
If a company has multiple contacts, each gets its own row with company details repeated.
Limitations

Public data only — the tool surfaces information that is already publicly available on the web. It will not find private or unlisted contact details.
Best for well-known companies — larger or more established companies with a strong web presence return higher-confidence results.
Speed — each lookup involves multiple live web searches and typically takes 20–40 seconds. Bulk searches run sequentially.
No persistence — results are cleared on page refresh. Export to CSV before closing.

Tech stack

Vanilla HTML / CSS / JS — no framework, no build tooling
Anthropic Messages API with web_search_20250305 tool
DM Mono + Fraunces via Google Fonts

License
MIT
