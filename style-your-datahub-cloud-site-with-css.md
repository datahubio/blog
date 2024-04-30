# Tutorial: Customize Your DataHub Cloud Site with CSS

## Introduction

In this tutorial, we're going to explore how you can personalise the appearance of your DataHub Cloud site. By the end of this tutorial, you'll learn how to use a `custom.css` file to adjust existing styles and how to utilise the "unstyled" layout for complete customisation freedom.

### What You'll Need

- GitHub account.
- A [DataHub Cloud](https://datahub.io/) site you want to customise.
- Basic knowledge of CSS.
- Basic knowledge of browser developer tools.

## Part 1: Adjusting Existing Styles with `custom.css`

Here is an example landing page of a site published with DataHub Cloud that we're going to style.

![[Pasted image 20240430201032.png]]



### Step 1: Create the `custom.css` File

In your GitHub repository, create a file named `custom.css`. This file should be in the root directory of the repo.

> [!important]
> If you're site is published off of a subfolder of your repository (i.e. you've specified "Root Directory" config field), the `custom.css` file should be placed in the root of that subfolder.

### Step 2: Change Background Colour & Heading Fonts

Add the following CSS rules in your `custom.css` file to change the font and color of all headings on your site:

```css
/* Change heading fonts and colors */
.bg-background {
    background: #f9f6f1 !important;
}

h1, h2, h3, h4, h5, h6 {
    font-family: "Lucida Console", "Courier New", monospace !important;
    font-weight: bold !important;
}

h1, h4 {
    color: #d30c7b !important;
}

h2, h5 {
    color: #ba5a31 !important;
}

h3, h6 {
    color: #508484 !important;
}
```

> [!note]
> Note, that we need to override the existing styles with `!important ` rule. This may not be needed each time, but if you're trying to tweak some styles and there is no effect, you may need to use it.

Here is the end result on our example page:

![[Pasted image 20240430202612.png]]
### Step 3: Customise Anything You Want

Those were just some basic examples of tweaking css on your site. But you can style virtually anything you can see on your page. You just need to find out how to properly "select" that HTML element in your `custom.css`. 

How? Developer console to the rescue! 

You can open it using the following keys combination:
- Windows or Linux: Ctrl + Shift + C
- MacOS: Cmd + Option + C

Now you should be able to hover over the elements you see on your site's page and find an underlying HTML element to learn how you can point at it in you custom CSS config.

## Part 2: Using the `unstyled` Layout

There may be times when you might want to go a bit further and you basically want to undo or override most of the site's default styles. This may be especially useful when creating landing pages.

So, let's say we want to create a proper landing page

### Step 1: Opting for an "Unstyled" Layout

In certain scenarios, you might prefer to start with a clean slate, particularly for bespoke pages like a custom landing page. To do this:

1. Create or edit a Markdown file for which you want an "unstyled" layout.
2. Add a front matter block at the beginning of the file specifying the layout type:

```yaml
---
layout: 'unstyled'
---
```

This setup instructs DataHub Cloud to render the page without applying any default styles, giving you full control over its appearance.

### Step 2: Adding a Simple HTML Hero

Within the same Markdown file, you can directly include HTML. Add your hero section as follows:

```html
<!-- Simple HTML Hero -->
<div class="custom-hero">
    <h1>Welcome to Our Site</h1>
    <p>Explore our world of markdown magic.</p>
</div>
```

### Step 3: Styling Your Hero in `custom.css`

Back in your `custom.css` file, add styles for your custom hero section:

```css
.custom-hero {
    background-color: #007BFF; /* Blue background */
    color: white; /* White text */
    padding: 20px; /* Some padding */
    text-align: center; /* Centered text */
}

.custom-hero h1 {
    margin: 0 0 10px 0; /* Adjust margins as needed */
}

.custom-hero p {
    margin: 0; /* Remove paragraph margins */
}
```

Once again, commit and push your changes. DataHub Cloud will update your site, and your custom-styled hero section should now be visible on the specified page.

## Conclusion

Congratulations! You've just learned how to customize the appearance of your DataHub Cloud site using a `custom.css` file for subtle tweaks and how to employ an "unstyled" layout for more significant customizations. These techniques empower you to tailor your site to match your vision or brand identity closely. Explore, experiment, and most importantly, have fun designing your site.

Feel free to revisit this tutorial whenever you need to make further customizations or need a refresher on applying CSS to your DataHub Cloud site.

---

Remember, the visual identity of your site plays a crucial role in engaging your audience, so take advantage of these customization capabilities to make your site stand out.

If you encounter any issues or have questions, the DataHub Cloud community and support team are here to help.

Happy styling!



