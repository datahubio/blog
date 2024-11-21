---
title: "Using markdowndb to extract information from markdown files"
date: 2024-05-10
authors: ['Mohamed Yahia']
filetype: blog
---

# Building a website with markdown: extract data from markdown Files with markdownDB

[MarkdownDB](markdowndb.com) can pull out things like tags and links from your markdown files. That's great, but what if you want more?  MarkdownDB lets you grab other things too, like titles, code sections, or even callouts! This is where its "computed fields" come in.

> [!info]
> New to MarkdownDB? Read our short intro to learn more: [What's markdowndb?](). Then, we can dive in!

## extract first title and use it to create an index page

- how to write computed fields?
  - using config.json
- what is the function signture?
  - fileInfo
    - what would adding a property to fileInfo would do?
      - add the field to the database
  - ast
    - this's the representation of the ast
    - [!info] to what are abstract syntax trees?
- example
  - a problem of building an index page by extracting the
  - `config.json` code
  - [!info] querying the database to get the titles
- [!info] other suggestions
  - with regex
- conclusion
  - read docs
  - join discord

We'll show you how to grab titles from your files by adding a simple function to the "computed fields" section in a file called `markdown.config.js`

```ts
export default {
    computedFields: [(fileInfo, ast) => {
        // This function computes additional fields based on fileInfo and AST.
        // Modifying fileInfo here will make changes in the database.
        fileInfo.title = "Markdowndb is awesome!"
    }]
}
```
**(fileInfo):** This contains information about the file itself, like its name and location. Adding a property here will create a new field for that data in the database.
**Code Structure (AST):**  This is a special way of representing the code inside your markdown file, kind of like a map. We use it to understand how the data is organized.

[!info] Want to learn more about Abstract Syntax Trees (ASTs)?  Search online for "AST in programming". 

**A Smoother Workflow for Your Content:**

1. **Prepare Your Content Files:** Your Markdown files are the building blocks. Feel free to include a YAML frontmatter section at the beginning to store metadata like title, date, tags, and more. Here's an example:

    ```md
    ---
    title: My Awesome Blog Post
    date: 2024-05-08
    tags: [markdown, tutorial]
    ---
    
    # This is my fantastic blog post!
    ```

2. **Install and Run MarkdownDB:** The magic tool is the `mddb` package. Install it using npm or yarn:

    ```Bash
    npm install mddb
    ```

3. **Extracting data from markdown**
you can extract any data from a markdown file by adding a function in the configuration file. we will add an example on how to extract titles from markdown file by adding some functions in the computed fields property in the `markdown.config.js` file

    ```javascript
    export default {
      computedFields: [
        (fileInfo, ast) => {
          const stack = [ast];
          while (stack.length > 0) {
            const current = stack.pop();
            
            // Only get the first header h1
            if (current.type === 'heading' && current.depth === 1) {
              fileInfo.title = getNodeValue(current)
            }

            if (current.children) {
              // Since we want to process children in reverse order, we push them onto the stack in reverse
              for (let i = current.children.length - 1; i >= 0; i--) {
                stack.push(current.children[i]);
              }
            }
          }
        }
      ]
    };

    // get the text for a given node
    function getNodeValue(node) {
      if (node.type === 'text') {
        return node.value;
      }
      if (node.children && node.children.length > 0) {
        let value = '';
        node.children.forEach(child => {
          value += getNodeValue(child);
        });
        return value;
      }
      return '';
    }
    ```

1. Now, let MarkdownDB index your Markdown files into an SQLite database! Simply point it to the folder containing your Markdown content:

    ```Bash
    npx mddb ./blog-posts
    ```

    This creates a `markdown.db` file in your current directory, housing all the indexed data.

2. **Querying Your Content:**
    MarkdownDB gives you two ways to retrieve information: SQL and a handy Node.js API.
**5.1 Querying with SQL (Optional):** If you're comfortable with SQL, you can directly query the database. Here's an example to find all files with the "markdown" tag:

```sql
SELECT files.*
FROM files
INNER JOIN file_tags ON files._id = file_tags.file
WHERE file_tags.tag = 'markdown'
```

**5.2 Database Connection Library:**

```JavaScript
// @/lib/mddb.mjs
import { MarkdownDB } from 'mddb';

const dbPath = 'markdown.db';

const client = new MarkdownDB({
  client: 'sqlite3',
  connection: {
 filename: dbPath,
  },
});

const clientPromise = client.init();



export default clientPromise;
/* To run quries
const client = await clientPromise
const results = client.query({
  Your query parameters here, e.g., select title from files
});
*/
```

**Explanation:**

- The `Blog` component renders a list of titles and links from the `blogs` props.
- `getStaticProps` fetches files using the MarkdownDB API.
- The retrieved files are mapped to an array of blog objects containing extracted titles and URL paths.
- The `mddb.mjs` file establishes the connection to the MarkdownDB database.

**Additional Considerations:**

- You can customize title extraction logic (e.g., using a specific header level) by modifying the `computedFields` configuration in your MarkdownDB setup.
- Consider alternative database options for specific use cases. ( e.g. extracting description )

**Embrace Flexibility and Efficiency:** MarkdownDB empowers you to do a lot of things. Visit the following page for more information about the other cool features of MarkdownDB: [https://markdowndb.com/docs](https://markdowndb.com/docs).
