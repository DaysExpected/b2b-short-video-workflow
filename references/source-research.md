# Source Research

## Inputs

Ask for or infer cautiously: topic, business direction, target audience, desired viewpoint, geographic or date limits, and search keywords. If any missing input would materially change the search, ask before searching.

## Search and validation

For one requested video topic, search for at least five relevant English articles, essays, newsletters, journal pieces, research pieces, or reputable management publications. Open and inspect the actual source; do not rank a source using only a search-result snippet.

Validate each viable source for:

- real title;
- real author and publication where available;
- working URL;
- publication date where available;
- access status: open, registration-gated, or paywalled.

Prefer sources written for engineering managers, HR/talent leaders, founders, CTOs, and business decision-makers. Prefer sources that describe a practical workplace problem; contain a tension, contradiction, or counterintuitive point; can support a 45–60 second video; provide a concrete example, original research/data, management trade-off, actionable framework, or specific workplace situation; are specific rather than generic; and have strong short-video potential.

Reject generic “communicate more / build trust / be a better leader” advice without concrete substance, SEO content farms, product landing pages, job postings, social posts treated as articles, duplicate or mirrored sources, and multiple pages that repeat the same underlying study as independent evidence.

Use these preferred outlets as guidance, not hard restrictions: LeadDev, The Engineering Manager, EngineeringManager.io, Built In, Harvard Business Review, Google re:Work, Atlassian, GitLab, Busfactor, Martin Fowler, InfoQ, Increment, The Pragmatic Engineer, and First Round Review.

## Shortlist rule

Shortlist exactly the best three valid sources unless fewer than three valid sources genuinely exist. Do not select the final article on the creator's behalf.

## Output format

```markdown
## Research brief
- Topic:
- Audience:
- Direction:
- Search scope:
- Sources inspected: [at least 5, or explain why fewer were viable]

## Shortlisted sources
### Rank 1 — [Article title]
- Author / publication:
- URL:
- Publication date:
- Access status: Open / Registration / Paywall
- Search keyword used:
- Summary:
  - [3–5 concise bullets]
- Why it fits this video topic:
- Strongest video-worthy tension / contradiction:
- Possible short-video angle:
- Key idea to adapt, paraphrased:
- Risk or limitation:
- Video potential score: [1–10]

### Rank 2 — ...
### Rank 3 — ...

## RECOMMENDED SOURCE
- Article:
- Why it is strongest:
- Strongest usable argument:
- Why it is stronger than the other two:

HUMAN CHECKPOINT — Select ONE article.
Reply with: Article [rank], or provide another source.
```

If the full source cannot be checked, label it `ACCESS LIMITED` and do not present unverified details as facts. The Agent must not start Script Development until the human explicitly selects or supplies one source.
