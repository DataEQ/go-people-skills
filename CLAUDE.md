# Good Outcomes Skills Marketplace

Public Claude Code plugin marketplace for Good Outcomes recruitment.

## What This Is

A Claude Code plugin that candidates install to apply for jobs at Good Outcomes. The skill guides them through:
1. Learning about Good Outcomes and the open roles
2. Gathering their information (name, email, about, resume)
3. Solving a semantic embedding challenge (finding a phrase about Consumer Duty)
4. Submitting their application via the API

## Structure

```
.claude-plugin/
├── marketplace.json    # Plugin marketplace manifest
└── plugin.json         # Plugin metadata

plugins/apply-to-good-outcomes/
├── plugin.json         # Plugin definition
└── skills/apply/
    ├── SKILL.md        # Main skill instructions
    └── references/
        └── openapi.yaml  # API specification for candidates
```

## Installation

Candidates install via:
```bash
npx skills add good-outcomes
```

Or manually add to their Claude Code settings.

## The Challenge

Candidates must find a phrase semantically similar to "demonstrating good outcomes for customers under Consumer Duty" with cosine similarity ≥ 0.88.

The skill provides hints pointing to FCA Consumer Duty but does NOT give the answer - candidates must research and iterate.

## API Endpoints (go-people repo)

- `GET /challenge?email={email}` - Get target embedding and hint
- `POST /embed` - Test phrase similarity
- `POST /upload-resume` - Upload resume file
- `POST /apply` - Submit application

Base URL: `https://go-people.goodoutcomes.ai`

## Related Repos

- **go-people** - Private API backend (FastAPI, Notion, GCS)
