# Rocketyard

**Structured web data, pay per result.** Rocketyard builds and maintains scrapers for public web data and publishes them as Actors on the [Apify Store](https://apify.com/rocketyard). Every Actor returns clean JSON records with typed values and fills as many fields as the source page publishes.

## Actors

| Actor | What you get |
| --- | --- |
| [Greenhouse Jobs Scraper](https://apify.com/rocketyard/greenhouse-jobs-scraper) | Every open job on a Greenhouse board via the official public API: title, department, locations, dates, description, apply link, salary range when published |
| [Ashby Jobs Scraper](https://apify.com/rocketyard/ashby-jobs-scraper) | Every open job on an Ashby board via the official public API: team, employment type, remote or hybrid, locations, description, salary range when published |
| [Job Postings Scraper](https://apify.com/rocketyard/jobposting-schema-scraper) | Job postings from any career site: title, company, location, posting date, description |
| [Product Scraper](https://apify.com/rocketyard/product-schema-scraper) | Name, SKU, image, price, currency and stock from any online store, plus brand and rating when shown |
| [Events Scraper](https://apify.com/rocketyard/event-schema-scraper) | Dates, status, venue, address, coordinates and ticket prices when listed |
| [Article Scraper](https://apify.com/rocketyard/article-schema-scraper) | Headline, publisher, dates, language, full text and word count from news sites and blogs |
| [Company Info Scraper](https://apify.com/rocketyard/organization-schema-scraper) | Name, logo, website, social profiles and full address from a company's own site |

The full, current list with prices, field lists and sample outputs is at [rocketyard.dev](https://rocketyard.dev).

## Quick start

Run an Actor and get its results in one API call (you need an [Apify API token](https://console.apify.com/settings/integrations)):

```bash
curl -X POST "https://api.apify.com/v2/acts/rocketyard~greenhouse-jobs-scraper/run-sync-get-dataset-items" \
  -H "Authorization: Bearer $APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"startUrls":[{"url":"https://job-boards.greenhouse.io/discord"}],"maxItems":100}'
```

One record from that run:

```json
{
  "title": "Associate Commercial Counsel",
  "company": "Discord",
  "location": "San Francisco Bay Area or Remote (U.S.)",
  "workplaceType": "remote",
  "department": "Legal",
  "datePosted": "2026-11-03T16:27:16.000Z",
  "salaryMin": 200000,
  "salaryMax": 225000,
  "salaryCurrency": "USD",
  "salaryUnit": "YEAR",
  "applyUrl": "https://job-boards.greenhouse.io/discord/jobs/8917177002"
}
```

For AI agents, connect Apify's MCP server: `https://mcp.apify.com?tools=rocketyard/<actor-name>`. Apify also connects the Actors to Make, Zapier and n8n.

## How we work

- **Data first**: before a release, each Actor must fill its key fields on real public pages. We don't advertise fields our tests can't fill reliably.
- **Tested on every release**: each build runs on the Apify platform before it goes live and rolls back automatically if a post-release check fails.
- **Public data only**: no logins, no paywall or CAPTCHA bypass, robots.txt honoured, no personal data.
- **Pay per result**: no subscription. Apify handles billing, and you can cap the cost of any run.

## Contact

Bugs, missing fields and site requests go to the **Issues** tab of the Actor on the Apify Store. Include the run ID and one example URL.

[Website](https://rocketyard.dev) · [Apify Store](https://apify.com/rocketyard)
