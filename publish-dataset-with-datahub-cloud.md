---
title: "Tutorial: Publish your dataset with DataHub Cloud"
date: 2024-05-14
authors:
  - Ola Rubaj
---
## Introduction

In this tutorial, we're going to learn how we can publish a dataset with DataHub Cloud.

As an example we'll use this dataset with an analysis of the top 1000 global universities: https://www.kaggle.com/datasets/zahrayazdani81/univercitiesranking?resource=download

### What You'll Need

- GitHub account and basic knowledge of GitHub UI (especially editing and adding files)
- A [DataHub Cloud](https://datahub.io/) account.

## Step 1: Create a GitHub repository with the data files and `README` file

Any DataHub Cloud site is built off of a GitHub repository. This is where you'd put all the dataset file(s) and any related markdown content that you want to publish. For the sake of simplicity, in this tutorial we're only going to add a root level `README.md` file. It's going to serve as a landing page for our site.

Note, we checked "Add a README file" checkbox on the screenshot below. This will make GitHub automatically add an empty `README.md` file to our repository.

![[Pasted image 20240514091335.png]]

> [!hint]
> If you're new to GitHub, here are simple instructions on creating a repository: https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories

Now that we have a new repository, we need to add our dataset files to it. The universities dataset we're using only has one `csv` file. Let's download it and upload it to our repository. We're going to name it `data.csv` but you can name it whatever you want.

> [!hint] 
> If you have multiple data files, to keep things tidy, we recommend putting them in a subfolder, e.g. in `/data`. 

![[Pasted image 20240514091853.png]]

> [!hint]
> If you're new to GitHub, here are simple instructions on uploading files to a repository: https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository

Let's also add some short introduction about our dataset to the `README.md` file. We'll use the one from original Kaggle dataset.

![[Pasted image 20240515003021.png]]
## Step 2: Create a DataHub Cloud site

This is not yet all we need to do, but let's first publishing our repository with DataHub Cloud first to see how it works.

Go to your DataHub Cloud account and click on "Create New Site" button at the top of the screen. Then, select your newly created GitHub repository and submit the form. You should now be redirected to the settings page of your newly created DataHub Cloud site. Click on the "Visit" button to see how your site looks!

![[Pasted image 20240515003051.png]]

As you can see, there is no mention of your data file and it only shows our `README.md` page content. Obviously, this requires some more work. We need to describe our dataset for DataHub Cloud, so that it can display information about it to our site's visitors.

## Step 3: Describe your dataset with Frictionless data standard

In DataHub Cloud, we can leverage Frictionless data standard to describe our datasets. 

What is it and how does it fit in DataHub Cloud? In short, it's a standard format for describing and sharing datasets with others. DataHub Cloud understands it, and, by default, will render each `README.md` (or `index.md`) file that has a Frictionless spec either in
- a `datapackage` frontmatter field,
- or a corresponding (same directory level) `datapackage.{json/yaml/yml}` file
with a special `dataset` layout, combining markdown content from the `README.md` file and metadata from the `datapackage` frontmatter field (or `datapackage.{json/yaml/yml}` file).

Note, that currently only a subset of Frictionless datapackage fields is displayed by DataHub Cloud's `dataset` layout.

Here are the supported ones:
- `title`
- `description`
- `created`: yyyy-mm-dd date
- `updated`: yyyy-mm-dd date
- `licences`:  The license(s) under which the package is provided. It is a list of objects with the following fields:
	- `path`: external link or path to file
	- `title`
- `sources`: Original sources of the dataset, i.e. where does the data come from if it was borrowed from somewhere. It is a list of objects with the same set of fields ar licences.
- `resources` (**required**): Describes all the data files included in the dataset. It is a list of objects with the following fields:
	- `name`
	- `description`
	- `path`
	- `lastModified`

> [!note]
> If you want to learn more about the Frictionless specification, go to https://specs.frictionlessdata.io. Note though, that not all of the fields mentioned in the specification will be displayed.

Now, let's create a `datapackage` yaml spec for our universities dataset.

```yaml
title: Top 1000 universities in the world
description: In this project, the ranking of the top 1000 universities in the world has been reviewed and analyzed.
updated: 2024-05-01
licenses:
  - title: Apache 2.0
    path: https://www.apache.org/licenses/LICENSE-2.0
sources:
  - title: Kaggle dataset
    path: https://www.kaggle.com/datasets/zahrayazdani81/univercitiesranking?resource=download
resources:
  - name: Universities Ranking
    description: Top 1000 Global Universities Analysed
    path: data.csv
```


Now, let's create a `datapackage.yaml` file with the above datapackage spec. Then go to your DataHub Cloud dashboard and "Sync" your site.

> [!note]
> Note, instead of nesting the datapackage specification in a `datapackage` field, you can just put the whole spec in a separate `datapackage.yaml` (or json) file right next to the README file. 

This is how the resulting site looks like:

![[Pasted image 20240515010227.png]]
![[Pasted image 20240515010236.png]]
![[Pasted image 20240515010252.png]]

Congratulations! You've just learned how to publish a dataset with DataHub Cloud.

---

If you encounter any issues or have questions, the DataHub Cloud community and support team are here to help.

Happy hacking!



