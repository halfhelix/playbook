# Shopify Guide

A mostly reasonable approach to Shopify theme development

## A note on the language:

- "Avoid" means don't do it unless you have good reason.
- "Don't" means there's never a good reason.
- "Prefer" indicates a better option and its alternative to watch out for.
- "Use" is a positive instruction.

## High-Level Guidelines

- Use Gulp, unless you have a good reason not to.
- Always commit your work to git after a feature is complete
- Always Use .SCSS flavor of SASS
- Use snippets/partials whenever possible
- [Shopify Docs](https://help.shopify.com/api) are your friend.
- When in doubt, copy the [Timber theme](https://github.com/Shopify/Timber) design patterns
- Use [Shopify Image Filters](https://www.shopify.com/partners/blog/the-img_url-filter-just-got-10x-better) to server properly sized media files.
- Use Shopify Theme Options for common variables, such as email, social links, hours
- Use Shopify Pages for static content.
- Use Shopify Blogs are looped content.
- Avoid deeply nested naviagtions.
- Avoid customizing checkout (Shopify Plus Only)

# Starter Theme

## Shopify Helix
User the Shopify-Helix starterkit unless there is a good reason not to.

https://github.com/halfhelix/shopify-helix

- SCSS Paritials
- Modular Javascript + ES6
- Gulp-based file syncing
- Minification

# Shopify Workflow

Shopify does not have a local server or git deployment strategy. This means it's extremely easy to either 1) overwrite a team members work or 2) introduce bugs into a live site. To avoid this, you should follow a development workflow that works with the SHopify system.

## Steps to make a feature

1. Setup your machine
* Create a branch
* Log into [Shopify Admin > Themes](https://YOUR_DOMAIN.myshopify.com/admin/themes)
* Duplicate the live theme
* Rename newly duplicated theme your branch name
* On your new theme, click `Customize Theme`
* Note the Theme ID in the URL (it should be the only integer in the URL)
* **IMPORTANT** paste the branched Theme ID into the `theme_id` value in `config.yml`
* Run Gulp
* Code all the things, and your changes will automatically be pushed up to the unpublished theme of the Theme ID you identified
* **IF** you change any theme settings on your branch (in the Shopify customize theme WYSIWYG), run `theme download config/settings_data.json` and commit that with your PR.
* Finish the feature, make a PR
* Merge the PR to `master`
