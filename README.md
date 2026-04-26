# 2026-midterms

This repository houses datasets used to **track the 2026 U.S. Congressional midterm elections**, with an emphasis on comparing:

- **Expectations** (race ratings, favored party, incumbent/candidate context, etc.)
- **Actual performance** (primary outcomes, general election results, margins, flips, etc.)

The intent is to support consistent tracking across:
- **Every state** (Senate + statewide election/primary context)
- **Every congressional district** (House)

## Repository structure (current)

- `primary-calendar.csv`  
  State-by-state primary (and runoff, where applicable) calendar with indicators for whether the state has Senate races and the number of House races.

- `senate-elections/`  
  Senate election tracking data.
  - `senate-GE.csv` — Senate general election tracker (incumbent info, primary date/completion, notable challengers placeholders, and rating fields).

- `house-elections/`  
  House election tracking data.
  - `house-GE.csv` - House general election tracker (incumbent info, primary date/completion, notable challengers, and rating fields).

- `2026-midterms.Rproj`  
  RStudio project file for working with this repo in R/RStudio.

## Data conventions (project intent)

To make “expectations vs. actuals” analyzable over time, datasets in this repo are intended to clearly separate:

### Expectations
Examples of expectation-type fields (varies by chamber):
- race rating (e.g., Cook-style categories)
- incumbent status and candidate notes
- “favored party” / expected winner (if tracked)
- forecast or expected margin (optional, if added later)

### Actual performance
Examples of results-type fields:
- primary: winner(s), vote share, runoff status (where relevant)
- general: winner, margin, party flips, vote totals/percentages (as available)

When practical, columns should be named and structured so they can be compared programmatically (e.g., rating vs. final result, predicted party vs. winning party).

## Current datasets

### `primary-calendar.csv`
State-level primary calendar reference.

Columns include:
- `State` (2-letter abbreviation)
- `Primary Date`
- `Runoff Date` (if applicable)
- `Senate Races` (Yes/No)
- `House Races` (count)
- `Notes`

### `senate-elections/senate-GE.csv`
Senate general election tracker.

Contains fields for:
- pre-election incumbent, party, and whether running
- special election flag
- primary date and whether the primary is completed
- notable challengers / primary result placeholders
- rating fields (including Cook-style categories)

> Note: Some fields may contain `NA` where information is unknown or not yet populated.

## Planned additions (recommended)

To fully support “every state and district” tracking, likely next additions include:

### House tracking file(s)
A canonical district-level file
- `house-elections/house-GE.csv`

Columns:
- `State`, `District`
- incumbent name/party, whether running
- primary date and primary completion status (optional but useful)
- notable challengers
- expectation fields (rating / favored party)
- results fields (winner, margin, flipped)

### Sources / update metadata (optional but helpful)
To keep the datasets auditable over time, consider adding:
- a `Source` column and/or `Last updated` column in key tables, or
- a lightweight changelog (even a `CHANGELOG.md` with brief notes)

## Using the data (R)

```r
primary_calendar <- read.csv("primary-calendar.csv")
senate_ge <- read.csv("senate-elections/senate-GE.csv")
```

## Maintainer workflow

This repository is currently maintained by the author.

