# How to Configure Your DataHub Cloud Site's Navigation Bar and Set Basic SEO Fields

You can now personalize your site by changing the navbar's logo, title and adding your own navigation links. You can also set your own site-wide SEO title and description.

## Improve SEO by Setting Your Site's Title, and Description

By adding a `config.json` file in the root directory of your site, you can optionally give your DataHub site a name that will be included on pages without a specific title. This can help improve your site's search engine optimization (SEO).

Here's how you can add a title and description for your site. You can make those changes by adding a `config.json` file in the root directory of your site:

```json
{
  "title": "My Great DataHub Site",
  "description": "This is a custom DataHub site for our company's data",
}
```

Now your website should have the title as the website title.
![[Datahub-cloud-title-demo.png]]
The description will only affect the site's SEO.

## Adding site logo

To add a logo, you can add a URL pointing to your logo in the `config.json` file. for example let's add a logo to our `config.json` file we currently have.

```json
{
  "title": "My Great DataHub Site",
  "description": "This is a custom DataHub site for our company's data",
  "logo": "https://images.unsplash.com/photo-1611267254323-4db7b39c732c?q=80&w=2848&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
}
```

Now your website should have the logo as the website logo in the navigation bar.
![[Datahub-cloud-logo-config-demo.png]]

## Changing the links in the navigation bar

To put links on the navigation bar, you just need to list them in your config file. Each link needs two things:

- `name`: what it's called on the bar
- `href`: where it goes when clicked

```json
{
 "title": "My Great DataHub Site",
 "description": "This is a custom DataHub site for our company's data",
 "author": "The Data Team"

 "navLinks": [
  {
   "href": "https://discord.gg/DVfydeGNuT",
   "name": "Join our discord!"
  }, 
  {
  "href": "https://twitter.com/datopian",
  "name": "Follow us on social media"
  }
 ]
}
```

Now the navigation bar should have the new links.
![[Datahub-cloud-navlinks-demo.png]]

## Conclusion
For more information and to join our community, visit us at [datahub.io](https://datahub.io) and connect with us on [Discord](https://discord.gg/DVfydeGNuT). We'd love for you to be a part of our Discord community - it's the perfect spot to meet fellow data enthusiasts, get the latest updates, ask for help, and share your thoughts with us.
