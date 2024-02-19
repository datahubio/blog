---
title: "Unveiling MarkdownDB's Latest Features: Export to JSON, task extraction, and computed fields 🚀"
date: 2023-12-12
authors: ['Mohamed Yahia']
filetype: blog
---


## Introduction

MarkdownDB continues to evolve, introducing new features to enhance the management of Markdown files. In this blog post, we're thrilled to present three exciting features: export to JSON files, task extraction, and computed fields.
MarkdownDB continues to evolve, introducing new features to enhance the management of Markdown files. In this blog post, we're thrilled to present three exciting features: export to JSON files, task extraction, and computed fields.

## Export to JSON files 📤

MarkdownDB now supports the seamless export of data to JSON files, offering enhanced flexibility in managing your MarkdownDB content.
```bash
npx mddb ./content
```

This will generate a `.markdowndb/files.json` file that contains metadata extracted from all the files in the `content` folder.

**Output example:**

```json
[
  {
    "_id": "7e01cae193f12f5a4a9be2b89f22b429761bd313",
    "file_path": "blog/hello-world.md",
    "extension": "md",
    "url_path": "blog/hello-world",
    "filetype": null,
    "metadata": {
      "author": "John Doe",
      "date": "2023-12-01"
    }
  },
  ...
]
```

## Task extraction 📋

MarkdownDB makes managing tasks easier with its new task extraction feature. Now, you can quickly find and organize your tasks, making tracking your tasks more straightforward.

For example:

```md
---
  title: markdowndb
  description: "Javascript library for treating markdown files as a database"
---
- [x] Do laundry
```

When you run the query below:
```sql
SELECT metadata FROM files;
```

The output will resemble the following JSON structure:
```json
"metadata": {
  "title": "markdowndb",
  "description": "Javascript library for treating markdown files as a database",
  "tasks": [{
    "description": "Do laundry",
    "checked": true
  }]
}
```

Say goodbye to manual task tracking as **MarkdownDB** helps you handle tasks within your Markdown content. Embrace a more efficient and automated solution for task extraction and management.

Learn more at [MarkdownDB Tasks Documentation](https://markdowndb.com/docs/tasks).

## Computed Fields 🤖

Explore enhanced functionality with Computed Fields, an advanced feature that allows users to create custom functions for dynamic field computation, enriching the depth of Markdown content.

Users can define a function that takes the file object and the file's AST (Abstract Syntax Tree), enabling them to add fields to it as needed.

For example, consider the function `addTitle`, designed to extract the title from the first heading in the AST (Abstract Syntax Tree) of a Markdown file using JavaScript.

Then you can index the folder 
```javascript
client.indexFolder(folderPath: "PATH_TO_FOLDER", customConfig: { computedFields: [addTitle] });
```

MarkdownDB ensures that the computed title is included in the database.

Learn more at [MarkdownDB Computed Fields Documentation](https://markdowndb.com/docs/).

## Getting Started

Excited to explore these new features? Ensure your MarkdownDB installation is up to date, and dive into our [documentation](https://markdowndb.com/blog/basic-tutorial) for detailed instructions on utilizing Export to JSON, Effortless Task Extraction, and Computed fields.


## Conclusion

With these new features, MarkdownDB continues to redefine how users interact with Markdown content. Whether you're a developer, content creator, or data enthusiast, these updates introduce new dimensions for handling and utilizing Markdown files in your projects.

Explore the enhanced capabilities of MarkdownDB today and stay tuned for more exciting updates on the horizon!

*MarkdownDB - Built with ❤ by Datopian.*
