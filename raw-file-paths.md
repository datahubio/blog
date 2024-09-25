---
title: Announcing a New Endpoint for Fetching Raw Data Files in DataHub Cloud Sites
date: 2024-09-25
authors: [Ola Rubaj]
---

We’re excited to introduce a new endpoint that allows you to fetch raw data files from any DataHub Cloud site. Here’s an overview of the changes.

## Why the Update?

In the previous datahub.io platform version, we had the `/r/{resource}.{csv/json/html}` endpoint, which served datapackage resource files (identified by their name or index) in three different formats:

- CSV – served the raw CSV file of the resource,
- JSON – served the CSV file converted to JSON,
- HTML – provided a preview of the resource in a user-friendly table.

This functionality has been dropped during our migration to the new version of datahub.io. Now, we’re bringing it back, though in a slightly different form.

We’re introducing a new, stable endpoint for raw files: `/_r/-/{path-to-file}`. This endpoint allows you to fetch any file by providing its exact path.

## Example Usage

Let’s say you regularly use the Country Codes dataset and want to integrate it into your code to automatically fetch the latest version of the data. You can obtain the link to the data file from the “Data Files” section by right-clicking on the link in the “Download” column.

## What About the Old JSON and HTML Formats?

In the past, we generated HTML previews of datapackage resource files (e.g. `/r/resource-abc.html`), allowing users to view the data in a table format. This feature is currently not supported, but we are considering bringing it back in the future.

For now, we won’t be reintroducing the generation of JSON files from CSV files. However, if this feature turns out to be needed, we may bring it back too.

---

Stay tuned for further enhancements, and thank you for using our platform!

If you encounter any issues or have questions, the DataHub Cloud community and support team are here to help.

Happy hacking!
