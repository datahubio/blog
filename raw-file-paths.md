---
title: New Endpoint for Fetching Raw Data Files from DataHub Cloud Datasets
description: Now you can fetch data files from DataHub Cloud datasets using a stable endpoint, that you can integrate into your workflows to always have the latest data.
date: 2024-09-25
authors: [Ola Rubaj]
---

We’re excited to introduce a new endpoint that allows you to fetch raw data files from DataHub Cloud datasets (and any other DataHub Cloud sites). Here’s an overview of the changes.

## Why the update?

In the previous datahub.io platform version, we had the `/r/{resource}.{csv/json/html}` endpoint, which served datapackage resource files (identified by their name or index) in three different formats:

- CSV – served the raw CSV file of the resource,
- JSON – served the CSV file converted to JSON,
- HTML – provided a preview of the resource in a user-friendly table.

This functionality has been dropped during our migration to the new version of datahub.io. Now, we’re bringing it back, though in a slightly different form.

We’re introducing a new, stable endpoint for raw files: `/_r/-/{path-to-file}`. This endpoint allows you to fetch any file - specifically and most importantly a dataset's data file - by providing its exact path.

## Example usage

Let’s say you regularly use the [Country Codes](https://datahub.io/core/country-codes) dataset and want to integrate it into your code to automatically fetch the latest version of the data. You can obtain the link to the data file from the “Data Files” section by right-clicking on the link in the “Download” column. It's a permalink to that data file, meaning you can use it with confidence without worrying about it being changed unexpectedly.

## What about the old JSON and HTML formats?

In the past, we generated HTML previews of datapackage resource files (e.g. `/r/resource-abc.html`), allowing users to view the data in a table format. This feature is currently not supported, but we are considering bringing it back in the future.

For now, we won’t be reintroducing the generation of JSON files from CSV files. However, if this feature turns out to be needed, we may bring it back too.

---

Stay tuned for further enhancements, and thank you for using our platform!

If you encounter any issues or have questions, the DataHub Cloud community and support team are here to help.

Happy hacking!
