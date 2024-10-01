---
title: "Updating the Country Codes Open Dataset: A Major Overhaul"
date: 2024-10-01
authors: ["Anuar Ustayev"]
---

We are excited to share the latest updates on our open dataset, `country-codes`. Over time, this dataset had become outdated, and the underlying codebase required a significant overhaul. To ensure it remains reliable and up-to-date, we embarked on a comprehensive update, fixing the structure and implementing new processes for regular maintenance.

## **Why the Update?**

The `country-codes` dataset is an essential resource for many data enthusiasts and developers. However, it had not been actively maintained, resulting in outdated information and obsolete scripts. It became clear that a significant restructuring was necessary to bring the dataset back to life and make it a valuable, up-to-date resource once more.

## **Key Updates and Improvements**

### **1. Codebase Structure Fix**

The first task was to address the structure of the codebase. We reviewed the entire folder structure, re-organizing scripts and files to make it more maintainable and future-proof. This involved cleaning up unnecessary files and making sure the essential scripts are well-structured and documented.

### **2. Removal of Outdated Files and Scripts**

Some files were no longer relevant, including outdated scripts and configurations. For instance, we removed the `travis.yml` file since we no longer use Travis CI for our continuous integration. This cleanup ensures that the repository is lean and focused only on what's necessary.

### **3. Updated the `Makefile`**

The `Makefile` was updated to streamline the processes for building, testing, and maintaining the dataset. This update allows for easier management of the codebase, reducing the complexity for new contributors and ensuring consistent execution of tasks.

### **4. Automating with GitHub Actions**

To maintain the dataset effectively, we implemented a monthly cron job using GitHub Actions. This automation will ensure that the dataset is regularly checked and updated, helping to keep it accurate and up-to-date without manual intervention. Moving to GitHub Actions also aligns with our current CI/CD practices.

### **5. Link Updates**

Links throughout the project were reviewed and updated. This ensures that documentation, references, and resource files are correctly linked and accessible, providing a seamless experience for users and contributors.

### **6. Requirements File Update**

The `requirements.txt` file was updated to ensure compatibility with the latest versions of dependencies. This helps in maintaining a stable environment and reduces the risk of issues due to outdated libraries.

### **7. Resolving Issues and Cleaning Up**

Finally, we took the time to address the most recent issues reported by users. Outdated or irrelevant issues were closed, allowing us to focus on meaningful improvements. This cleanup not only helps keep our issue tracker relevant but also provides a clearer picture of what work is left to be done.

## **What’s Next?**

With these updates, the `country-codes` dataset is now in a much healthier state. Moving forward, our new monthly automated checks using GitHub Actions will help keep this dataset fresh and reliable. We're always open to feedback and contributions from the community, so feel free to reach out with suggestions or improvements!

Stay tuned for more updates, and thank you for being part of our open data journey!