---
title: "Optimizing the Clinical Trials (US) Repository: Data Storage and Git LFS Solutions"
date: 2024-12-13
authors: [Anuar Ustayev]
---

The [clinical-trials-us](https://github.com/datasets/clinical-trials-us) repository provides a critical resource, offering official U.S. clinical trial outcomes from the FDA. This data is vital for researchers, medical professionals, and policymakers. However, as the repository continues to grow, a key issue has surfaced regarding the best way to manage large datasets—specifically, the 2.3 GB of XML files sourced from ClinicalTrials.gov.

### The Challenge: Storing Large Datasets in GitHub

The repository's current approach involves storing the complete dataset directly within the repository. While this provides easy access for users, it raises several concerns:

- **Repository Size**: As the dataset grows, storing large files directly in GitHub can significantly inflate the repository size, making it harder to manage and slowing down operations such as cloning or pulling changes.
- **Data Updating**: Since the dataset is updated periodically, the process of pushing new versions to the repository is cumbersome and not ideal for handling such large files.
- **GitHub limits**: GitHub has a limit of 100 MB per file in the repository which makes it impossible to store large files.

### Git LFS: A Potential Solution

In response to these concerns, it was suggested that we utilize [Git LFS (Large File Storage)](https://git-lfs.github.com/) for handling the dataset. Git LFS is an extension to Git that allows users to manage large files more efficiently by storing them outside of the Git repository, while keeping track of them using Git.

#### Key Benefits of Git LFS

- **Reduced Repository Size**: Large files are stored externally, meaning that the repository itself remains lightweight and easier to manage.
- **Efficient Updates**: Git LFS makes it easier to update large datasets since the actual files are stored separately, and only lightweight pointers are tracked in the Git history.
- **Improved Cloning and Pulling**: Users can clone and pull the repository without downloading the large files every time, improving performance and user experience.

### Disadvantages of Git LFS

While Git LFS offers significant advantages, GitHub's option has notable limitations that make it less ideal for some use cases:

1. **Limited Free Storage and High Costs**: GitHub’s built-in Git LFS offers only a limited amount of free storage and bandwidth. After exceeding the free quota, the cost becomes quite high compared to popular blob storage solutions such as AWS S3 or Cloudflare R2. For repositories with large datasets, the cost of using Git LFS can quickly escalate.
   
2. **Lack of Custom Storage Options**: GitHub’s Git LFS is inflexible in terms of customization. Users are not able to write their own storage buckets, meaning that many users with specific requirements for control and ownership of their data are blocked from using GitHub LFS. This is a major barrier for projects that need more customizable and private storage solutions.

### A Better Solution: Giftless

To overcome the limitations of Git LFS, an alternative solution is available: **[Giftless](https://github.com/datopian/giftless)**. Giftless is an open-source, pluggable Git LFS server written in Python, designed to offer flexibility and customization. It allows users to configure their own storage backends, transfer methods, and authentication mechanisms, making it a powerful solution for managing large files in Git repositories.

#### Key Features of Giftless

- **Multiple Storage Backends**: Giftless supports various storage backends, including local storage, Google Cloud Storage, Azure Blob Storage, and Amazon S3, allowing users to choose the solution that best fits their needs.
- **Multipart Upload Support**: Giftless includes a custom transfer mode called `multipart-basic`, which leverages the multipart upload capabilities of many cloud vendors. This feature requires a specialized Git LFS client, such as the [giftless-client](https://github.com/datopian/giftless-client).
- **Pluggable Authentication Providers**: Giftless supports various authentication providers, making it suitable for different security requirements and use cases.

#### Installation and Configuration

Giftless can be installed easily via **PyPI**:

```bash
pip install giftless
```

After installation, Giftless can be configured using a YAML configuration file or environment variables to specify storage backends, transfer adapters, and authentication providers.

#### Getting Started with Giftless

To set up Giftless locally:

1. **Create a Virtual Environment**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

2. **Install Giftless**:
   ```bash
   pip install giftless
   ```

3. **Run the Development Server**:
   ```bash
   export FLASK_APP=giftless.wsgi_entrypoint
   flask run
   ```

Once the server is running, you can configure your Git repository to use Giftless as the LFS server by setting the LFS URL in your repository's configuration:

```bash
git config -f .lfsconfig lfs.url http://127.0.0.1:5000/<organization>/<repository>
```

#### Why Giftless?

Giftless allows users to bypass the limitations of GitHub’s Git LFS, providing full control over storage and bandwidth. It supports various cloud storage providers, reducing costs, and it’s fully customizable to meet specific user needs. By using Giftless, projects can achieve more flexibility and scalability, ensuring their large datasets are managed efficiently.

### Conclusion

While Git LFS offers a good solution for handling large files, its limitations in terms of storage cost and lack of customization make it less ideal for certain projects. For those looking for more control and flexibility, **Giftless** provides an open-source, customizable alternative that supports multiple storage backends and allows for efficient handling of large files.

By adopting Giftless, the **clinical-trials-us** repository can overcome the challenges of managing large clinical trial datasets while maintaining full control over storage solutions. This solution will ensure the repository remains scalable, cost-effective, and easy to manage.

If you have any thoughts on these solutions or would like to contribute, feel free to check out the discussion in [Issue #1](https://github.com/datasets/clinical-trials-us/issues/1) on GitHub.