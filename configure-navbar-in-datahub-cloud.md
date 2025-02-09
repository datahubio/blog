---
title: "DataHub Cloud: Learn How to Configure the Navigation Bar"
description: A step-by-step guide to customizing your site's navigation bar's logo, links, and social media
date: 2024-05-20
authors:
  - Ola Rubaj
tags:
  - datahub-cloud
---

This tutorial will guide you through the process of customizing your DataHub Cloud site's navigation bar. You'll learn how to add your logo, customize the title, create navigation links, and integrate social media links.

## Prerequisites

Before you begin, make sure you have:
- A DataHub Cloud site set up
- Basic knowledge of JSON format
- Your logo image ready (if you plan to use a custom logo)

## Step 1: Create the Configuration File

1. Navigate to the root folder of your site's repository
2. Create a new file named `config.json`.

## Step 2: Customize Your Logo and Site Title

3. Upload your logo file to your site's repository. (Skip if you're using a file hosted outside of your repository.)
4. Add your logo path (or URL) to the `nav.logo` field
5. Set your site title in the `nav.title` field

Example:
```json
{
  "nav": {
    "logo": "logo.jpeg",
    "title": "My Digital Garden"
  }
}
```

![[nav-config.png]]

The result:
![[nav-config-1.png]]

## Step 3: Add Navigation Links

Add your navigation links to the `nav.links` array. Each link requires:
- `name`: The text that appears in the navigation bar
- `href`: The URL or path the link points to

Example:
```json
{
  "nav": {
    "links": [
      {
        "href": "/blog",
        "name": "Blog"
      },
      {
        "href": "/about",
        "name": "About"
      }
    ]
  }
}
```

The result:
![[nav-config-2.png]]

## Step 4: Add Social Media Links

Add social media links to the `nav.social` array. Each social link requires:
- `label`: Platform identifier (see supported platforms below)
- `name`: Text label (used in sidebar mode)
- `href`: Your social media profile URL

Supported social platforms:
- github
- discord
- linkedin
- twitter
- x
- facebook
- instagram
- youtube

Example:
```json
{
  "nav": {
    "social": [
      {
        "label": "github",
        "name": "GitHub Profile",
        "href": "https://github.com/yourusername"
      },
      {
        "label": "twitter",
        "name": "Follow me on Twitter",
        "href": "https://twitter.com/yourusername"
      }
    ]
  }
}
```

The result: ![[nav-config-3.png]]
 On smaller screens:  ![[nav-config-4.png]]
 
## Complete Configuration Example

Here's a comprehensive example combining all the elements:

```json
{
  "nav": {
    "logo": "logo.jpeg",
    "title": "My Digital Garden",
    "links": [
      {
        "href": "/blog",
        "name": "Blog"
      },
      {
        "href": "/about",
        "name": "About"
      }
    ],
    "social": [
      {
        "label": "github",
        "name": "GitHub Profile",
        "href": "https://github.com/yourusername"
      },
      {
        "label": "twitter",
        "name": "Follow me on Twitter",
        "href": "https://twitter.com/yourusername"
      }
    ]
  }
}
```

## Troubleshooting

Common issues and solutions:

6. **Logo not appearing?**
   - Verify the logo path is correct relative to your site's root folder
   - Ensure the image file exists at the declared path

7. **Social icons not showing?**
   - Double-check that you're using supported platform labels

---

If you encounter any issues or have questions, reach out to us on [Discord.](https://discord.com/invite/KrRzMKU)