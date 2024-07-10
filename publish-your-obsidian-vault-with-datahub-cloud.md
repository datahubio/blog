---
title: How to Publish Your Obsidian Vault with DataHub Cloud
authors: [Ola Rubaj]
date: 2024-07-10
---

Publishing your Obsidian vault with DataHub Cloud is an excellent way to make your notes accessible online, track changes over time, and collaborate with others. This guide will walk you through the process step-by-step, starting with getting your vault onto GitHub and then using DataHub Cloud to create a website for your notes, making it simple even for non-tech-savvy users.

## What You'll Need

First, you'll need to set up the GitHub Desktop app, which provides a user-friendly interface for managing your repositories.

1. **Create a GitHub Account**: If you haven't already, go to [GitHub](https://github.com) and create an account.

2. **Download and Install GitHub Desktop**: Get the GitHub Desktop app from [here](https://desktop.github.com) and follow the installation instructions.

3. **Sign In**: Open the GitHub Desktop app and sign in with your GitHub account.

## Step 1: Set Up Your Vault as a GitHub Repository

Any DataHub Cloud site is built off of a GitHub repository. Now, let's create one from your Obsidian vault.

In the GitHub Desktop app, click on "Add an Existing Repository from your Hard Drive".

![[Pasted image 20240705122145.png]]
The name of your repository should be the exact name of your Obsidian Vault folder. Then, click on "Choose..." next to the "Local Path" field and select the **parent directory** of your Obsidian vault's folder.

For example, if path to my Obsidian vault is `/Users/o/Projects/my-digital-garden`:
- Name: `my-digital-garden`
- Local Path: `/Users/o/Projects`.

> [!important]
> This is a bit counterintuitive, but if you had selected the path to the vault itself, GitHub Desktop would have created another folder with the repository inside your vault instead.

If your repository doesn't have a root level `README.md` or `index.md` file yet, you can check "Initialize this repository with a README".

> [!tip]
> Any `README.md` or `index.md` file, either in a root of the repository or in a subfolder, will be treated as a "landing" page (of the whole site or a given folder) by the DataHub Cloud.

![[Pasted image 20240705124521.png]]
Now, click on "Create Repository".

To make sure that your Obsidian vault has been correctly added to the repository, switch to "History" tab. Under "Initial commit" you should see all the files from your vault, that has been automatically committed (saved) to your repository.

![[Pasted image 20240705125113.png]]

## Step 2: Push Your Vault to GitHub

With your repository set up locally, it’s time to push it to GitHub.

In the GitHub Desktop app, you’ll see a dashboard with "No local changes". Click on the "Publish repository" button

![[Pasted image 20240708195937.png]]

A new window will appear. Confirm the repository name, add an optional description, and choose whether to make it public or private. Click "Publish Repository".

![[Pasted image 20240708200035.png]]

Wait for the process to finish. You'll get a prompt once the upload is complete, and you can visit your repository on GitHub’s website to see your uploaded vault.

## Step 3: Publish Your Repository with DataHub Cloud

With your vault on GitHub, you can now publish it using [DataHub Cloud](https://cloud.datahub.io/) to create a website for your notes.

Go to your DataHub Cloud account and click the "Create New Site" button at the top of the screen. Then, select your newly created GitHub repository and submit the form.

![[Pasted image 20240708204225.png]]

You’ll be redirected to the settings page of your new DataHub Cloud site. 

![[Pasted image 20240708204423.png]]

You may need to wait a bit for the site to finish syncing content with your GitHub repository. After it's finished, click the "Visit" button to see how your site looks.

![[Pasted image 20240708204449.png]]

## Step 4: Making Changes to Your Vault and Publishing Them

Once your vault is set up and published, you'll likely want to make changes and update your site. 

Open the GitHub Desktop app. In the "Changes" tab you’ll see a list of changes you’ve made. Write a summary of the changes in the "Summary" field and click "Commit to main".

![[Pasted image 20240708202621.png]]

After committing your changes, click the "Push origin" button in GitHub Desktop to upload your changes to GitHub.

DataHub Cloud should automatically update your site after you push changes to the repository. If the automatic sync isn't working or has been disabled, you'll see an "Outdated" status under your site's title. In this case, you can manually sync your site by clicking the "Sync" button to apply the latest changes from your GitHub repository.

## Step 5 (Optional): Simplifying the Process with the Obsidian Git Plugin

For those who want an even easier way to manage changes to their Obsidian vault, the Obsidian Git plugin can automate the process of pushing updates to GitHub directly from within Obsidian, without the need for switching back and forth between Obsidian and GitHub Desktop. Refer to [the docs](https://github.com/Vinzent03/obsidian-git) to learn more.

> [!note]
>  You can set the plugin to automatically commit and push changes at regular intervals. Configure this in the plugin settings under “Auto-push every X minutes”.

---

If you encounter any issues or have questions, the DataHub Cloud community and support team are here to help.

Happy hacking!



