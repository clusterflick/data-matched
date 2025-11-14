# data-matched

This repository contains the automated workflow for matching movie data with
additional sources for the Clusterflick project.

## Purpose

The matching workflow enriches cinema data by cross-referencing movies with
additional data sources beyond The Movie Database. This provides enhanced
metadata, ratings, reviews, and other supplementary information to improve the
user experience.

## How It Works

The workflow executes the match command to enhance movie data:

```bash
npx clusterflick/scripts match
```

This command:

- Reads the combined cinema data
- Identifies movies that need additional metadata
- Queries additional data sources (e.g., IMDb, Rotten Tomatoes)
- Matches and merges supplementary information
- Generates enriched dataset with enhanced metadata

## Schedule

The workflow is automatically triggered when the
[data combining workflow](https://github.com/clusterflick/data-combined)
completes successfully. It can also be triggered manually via workflow dispatch
if needed.

## Maintenance

### Dependencies

The workflow may require API keys configured as GitHub secrets depending on the
data sources being used:

- Additional API keys for third-party data sources (as needed)
- `PAT` - Personal Access Token for publishing releases and triggering
  downstream workflows
