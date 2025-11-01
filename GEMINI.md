# Project: Personal Website (hareesh.co)

## Project Overview

This is a personal website for Hareesh Kanchanepally, built with the [Hugo](https://gohugo.io/) static site generator and the [Adritian](https://github.com/zetxek/adritian-free-hugo-theme) theme. The site serves as a portfolio, blog, and a central point for Hareesh's online presence. The content is written in Markdown and the site is deployed to Vercel.

## Building and Running

To work with this project, you need to have Hugo and Node.js installed.

**Running the site locally:**

```bash
hugo server -D
```

This will start a local development server at `http://localhost:1313`. The `-D` flag builds and serves draft content as well.

**Building the site for production:**

```bash
hugo --gc --minify
```

This will generate the static site into the `public` directory. The `--gc` flag cleans up unused cache and the `--minify` flag minifies the output.

## Development Conventions

### Content Management

-   **Content is managed in the `content` directory.** All pages and posts are written in Markdown.
-   **Obsidian Workflow:** The primary writing workflow is to create and edit content in [Obsidian](https://obsidian.md/), and then copy the finished Markdown files to the appropriate subdirectory within the `content` directory.
-   **Content-first:** The `public` directory is for the generated site only and should not be edited directly. All changes should be made to the files in the `content`, `static`, or `themes` directories.

### Customization

-   **Configuration:** The main configuration file is `hugo.toml`. This file contains the site's title, theme, menu structure, and other settings.
-   **Theme:** The site uses the Adritian theme, which is located in the `themes/adritian` directory. To customize the theme, you can override its templates by creating files with the same name in the `layouts` directory.
-   **Styling:** Custom CSS can be added to `static/css/custom.css`.

### Deployment

The site is deployed to Vercel. The deployment is automatically triggered when changes are pushed to the `main` branch of the GitHub repository.
