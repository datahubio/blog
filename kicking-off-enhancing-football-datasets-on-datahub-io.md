--- 
title: "Kicking Off: Enhancing Football Datasets on Datahub.io"
description: "Discover the latest updates to Datahub.io's football datasets repository, including improved data processing workflows, expanded datasets, and automated updates. Learn how these changes make accessing and analyzing football data easier than ever."
date: 2024-12-09
authors: ["Anuar Ustayev"]
---

At Datahub.io, we are committed to providing up-to-date and comprehensive football datasets. Our recent enhancements to the football-datasets repository reflect this dedication. Below is an overview of the key updates.

## Updated datasets on DataHub.io

This work includes 5 major European leagues:

- English Premier League – https://datahub.io/core/english-premier-league
- Spanish La Liga – https://datahub.io/core/spanish-la-liga
- Italian Serie A – https://datahub.io/core/italian-serie-a
- German Bundesliga – https://datahub.io/core/german-bundesliga
- French Ligue 1 – https://datahub.io/core/french-ligue-1

Each league has data for the all the seasons. The data is updated on daily basis via Github Actions.

## Streamlining Data Processing Workflows

We revamped our data processing workflows to efficiently parse football data from trusted sources like [football-data.co.uk](https://www.football-data.co.uk/). This improvement includes introducing a `requirements.txt` file and organizing scripts into a dedicated `scripts/` directory for better structure and maintainability.

## Modernizing the Codebase

Our codebase received a much-needed cleanup by removing outdated files, such as those related to Travis CI, and updating `.gitignore` and `README.md`. This ensures the repository is easier to use and aligned with the latest development practices.

## Expanding and Updating Datasets

The `datasets/` folder now includes fresh data, along with updated `datapackage.json` files, ensuring users always have access to the latest football statistics and records.

## Automating Data Updates

To keep datasets current, we implemented GitHub Actions that automatically run data processing workflows daily. This guarantees up-to-date football data, reflecting the latest match results and statistics without manual intervention.

## Improving Documentation for Better Usability

The repository’s `README.md` file was revamped to address user feedback and offer clearer instructions. This makes it easier for both new and experienced users to navigate and contribute to the repository.

## Enhancing Data Package Readability

We converted `datapackage.json` files to YAML format, improving readability and simplifying data package management for users.

These updates reflect our ongoing commitment to providing high-quality, accessible football datasets. We invite you to explore the repository and contribute to this open-data initiative.

*Check out the repository [here](https://github.com/datasets/football-datasets).*