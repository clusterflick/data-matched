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
npm run match
```

This command:

- Reads the combined cinema data
- Identifies movies that need additional metadata
- Queries additional data sources (e.g., IMDb, Rotten Tomatoes)
- Matches and merges supplementary information
- Generates enriched dataset with enhanced metadata

## Data Sources

One job per source, each publishing `matched-data/<source>.json` keyed by TMDB
id: IMDb, Letterboxd, Metacritic, The Movie DB, Rotten Tomatoes and the Bechdel
Test.

The Bechdel Test list carries terms the others do not. Its ratings are
[licensed under CC BY-NC 3.0](https://bechdeltest.com/about/), so the releases
published here redistribute them on the same terms: attribution is required
wherever they are shown, and neither the data nor anything built on it may be
put to commercial use. Every matched entry carries a `url` back to the film's
page on bechdeltest.com, which is how the site satisfies the attribution.

Coverage is partial — the list is crowd-sourced and lags on new releases, so a
missing entry means "not rated", never "fails".

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
