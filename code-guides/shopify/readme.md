# Shopify Guide

A mostly reasonable approach to Shopify theme development

## A note on the language:

- "Avoid" means don't do it unless you have good reason.
- "Don't" means there's never a good reason.
- "Prefer" indicates a better option and its alternative to watch out for.
- "Use" is a positive instruction.
- "Always" means always do it inless you have a good reason.

## High-Level Guidelines

- Use our prefered Starterkit, unless you have a good reason not to.
- Always commit your work to git after a feature is complete.
- Always Use .SCSS flavor of SASS.
- Use sections/snippets whenever possible.
- [Shopify Docs](https://help.shopify.com/api) are your friend.
- When in doubt, copy the [Debut Theme](#) design patterns
- Use [Shopify Image Filters](https://www.shopify.com/partners/blog/the-img_url-filter-just-got-10x-better) to serve properly sized media files.
- Use Shopify Section/Theme Options for dynamic data and configuration. 
- Use Shopify Pages for static content.
- Use Shopify Blogs are looped content.

# Starter Theme

Prefer to use [Skeleton](https://github.com/Pixel2HTML/shopify-skeleton) for new projects.

Prefer to migrate inherited projects to [Slate](https://github.com/Shopify/slate).

Whats important about these starterkits? 

- SCSS Paritials
- Javascript Components
- Local Proxy for live-reload
- Asset Minification 
- CLI Deployments (critlce for hooking up with CI/CD deployments)

# Shopify Workflow

Shopify does not have a local server or git deployment strategy. This means it's extremely easy to either 1) overwrite a team members work or 2) introduce bugs into a live site. To avoid this, you should follow a development workflow that works with the Shopify system.

## Steps to make a feature

1. Setup your machine
* Clone the repo to your local machine. 
* Create a branch for yourself, ie `dev/myname`
* Log into [Shopify Admin > Themes](https://YOUR_DOMAIN.myshopify.com/admin/themes)
* Duplicate the live theme
* Rename newly duplicated theme your branch name, ie `dev/myname`
* On your new theme, click `Customize Theme`
* Note the Theme ID in the URL (it should be the only integer in the URL)
* **IMPORTANT** paste the branched Theme ID into the `theme_id` value in `config.yml` or `.env` (depending on which starterkit you're using)
* Run `npm install` to install dependacies. 
* Ren the start command, either `npm run code` or `slate watch`, depending on your starterkit. 
* Code all the things, and your changes will automatically be pushed up to the unpublished theme of the Theme ID you identified. You can view your theme using the local proxy link provided in the CLI. 
* Finish the feature, make a PR.
* Merge the PR to `master`.
* Run the CI/CD service to deploy the site out to its various enviroments.

## Best Practices

* Sections
    * Use Sections to create "smart" componenets, that manage logic or dynamic content. 
* Snippets
    * Use snippets to create "dummy" componenets, that dont amanage any logic or dynamic content. 
* SCSS
    * Use BEM synmatx for class names. 
    * Use Partials/Imports to organize SCSS. Prefered structure is:
      ```
      +-- main.scss
      +-- 1-abstracts
      |   +-- _config.scss
      |   +-- _breakpoints.scss
      |   +-- _colors.scss
      |   +-- _mixins.scss
      |   +-- _resets.scss
      |   +-- _functions.scss
      +-- 2-base
      |   +-- general.scss
      |   +-- forms.scss
      |   +-- tables.scss
      |   +-- typography.scss
      |   +-- forms.scss
      +-- 3-layout
      |   +-- container.scss
      |   +-- ...
      +-- 4-components
      |   +-- header.scss
      |   +-- footer.scss
      |   +-- ...
      +-- 5-pages
      |   +-- home.scss
      ```
    * Use [Manila Mixins](https://www.npmjs.com/package/manila-mixins) for breakpoints, grid, placeholder color, smart underline, etc.
* JS
    * Use NPM for any 3rd party packages or libraries. 
    * Prefer to write JS in reusable modules, using [ES6 import / export](http://javascript.tutorialhorizon.com/2015/06/23/es6-modules-examples/). 
* Responsive Images / Image Filters
    * Alway use [Shoify Image filters]() for downsize image assets to an approraiet size for their context. 
    * Prefer to use responsive images to load smaller images into mobile devices and larger images into retina devices.
* Background Images
    * Use explicate alternative image on all background images set to `background-size: cover`. This will allows admins to maintain explicate control of the image composition on smaller screens that would overwise have lot of cropping. 
* Sliders
    * Always use [Slick.js]() as a slider library.
    * Always have explicate mobile images for hero sliders that are full width using background images. 
* HTML5 Videos w/ Fallbacks
    * Use jpg/gif fallbacks for all HTML video on touch devices. 
* Ajax Cart
    * Use [Cart.js]() for Ajax cart JS templating.
* Ignoring Settings & Locals
    * Always ignore `config/settings_data.json` from git and from the build/watch commands. 
* Documentation 
    * Alway provide documentation on features that are unique or not default to shopify.  

## Shopify Integration Standards 

* Header 
    * Header should always be static section with options to select navigation(s).
    * Other theme options, such as utility items, icons, etc should be section settings. 
* Footer
    * Footer should always be static section with options to select navigation(s).
    * Other theme options, such as utility items, icons, etc should be section settings. 
* Home
    * Homepage should be all dynamic / reusable sections. 
    * Home sections should have seven margin on top and bottom to ensure that they can be used in as many orders as possible. 
    * Each section should incapsolate its own settings. 
    * Whenever possible, use a single section with modification settings rather than 2 separate sections for similar blocks. 
* Catalog
* Product
    * Use sections for common blocks that have global logic. For example, a related products block (number of priducts to show?).
    * Use snippets for common blocks that do not hold any logic, For example, Static Image block.
    * Use meta fields (always use [SuperFields App](https://apps.shopify.com/superfields)) for dynamic data on the product page.
    * Whenever there is a content block on the PDP, it should always be conditionally rendered. Each block should default to disabled, and be able to optionally be enabled. 
* Cart
    * Prefer Ajax cart submissions. 
* Content Pages
    * Use Shopify Sections on interior content pages, such as About, Store Locator, etc. 
    * Prefer keeping page settings and configurations in secctions over in the page content. 
* Custom Objects
    * Perfer to use [SuperFields App](https://apps.shopify.com/superfields) for [custom objects](http://support.maestrooo.com/article/141-what-are-custom-objects), for example, Size Guide, Brands, etc. 
