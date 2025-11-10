# Personal Website (hareesh.co)

This repository contains the source code and content for the personal website of Hareesh Kanchanepally, available at [hareesh.co](https://hareesh.co/). The website serves as a professional portfolio, a personal blog (Notes), and a hub for various ventures.

## Technology Stack

*   **Static Site Generator:** [Hugo](https://gohugo.io/) (v0.152.2 or higher)
*   **Theme:** [typo](https://github.com/tomfran/typo)
*   **Hosting:** [Vercel](https://vercel.com/)
*   **Content:** Markdown

## Getting Started

### Prerequisites

*   [Hugo](https://gohugo.io/getting-started/installing/) (extended version)
*   [Node.js](https://nodejs.org/en/download/)

### Local Development

To run the website locally for development and testing, follow these steps:

1.  Clone the repository:
    ```bash
    git clone <repository-url>
    cd hareesh-site
    ```

2.  Initialize and update the theme submodule:
    ```bash
    git submodule update --init --recursive
    ```

3.  Start the Hugo development server:
    ```bash
    hugo server -D
    ```
    The `-D` flag includes draft pages. The site will be available at `http://localhost:1313/`.

### Building for Production

To generate the static site for production, run the following command:

```bash
hugo --gc --minify
```

This will create the production-ready website in the `public/` directory. The `--gc` flag cleans up unused cache files, and `--minify` optimizes the output files for performance.

## Content Management & Workflow

The primary workflow for creating and managing content is as follows:

1.  **Writing:** Content is written and edited in [Obsidian](https://obsidian.md/), a powerful Markdown editor.
2.  **Organization:** Once a piece of content is finalized, the Markdown file is moved into the appropriate subdirectory within the `content/` directory of this repository.
3.  **Committing:** The new or updated file is then committed to the Git repository and pushed to the `main` branch.

This content-first approach ensures a clean separation between the content creation process and the website's code and configuration.

## Architecture & Templating

The website's structure and page generation are governed by Hugo's content organization and templating system.

### Content Structure

All content for the website resides in the `content/` directory. Hugo uses the directory structure within `content/` to create sections for the website. For example:
*   `content/notes/` contains all the blog posts for the "Notes" section.
*   `content/ventures/` contains all the pages for the "Ventures" section.

### Page Generation

When you visit a URL on the website, Hugo uses a specific template to render the page.

#### Section Pages (`/notes`, `/ventures`)

Section pages are "list" pages that display a list of their subpages.

*   **/ventures:** This section is rendered using a custom template located at `layouts/ventures/list.html`. This template iterates through all the pages in `content/ventures/` and displays them in a custom list format, sorted by weight.

*   **/notes:** This section does not have a custom template. Instead, it uses the theme's default list template at `themes/typo/layouts/_default/list.html`. This default template is designed to be more generic and works for any section that doesn't have its own specific template. It iterates through the pages in `content/notes/` and uses a "partial" template (`layouts/partials/post-entry.html`) to render each item in the list. This allows for a consistent look and feel across different sections while still allowing for customization.

#### Blog Posts (Notes)

Blog posts appear on the `/notes` page simply by being present as Markdown files in the `content/notes/` directory. Hugo's templating logic automatically detects these files and the `/notes` list template renders them as a list.

#### Categories

Categories are managed using "front matter" at the top of each Markdown file. To assign a post to one or more categories, you add a `categories` key to the front matter:

```yaml
---
title: "My Blog Post"
date: 2025-11-10
categories: ["Technology", "Hugo"]
---
```

Hugo automatically groups all posts with the same category and creates a dedicated page for each category (e.g., `/categories/technology/`). This is a built-in feature of Hugo's taxonomy system.

## Customization

### CSS

Custom CSS styles can be added to the `static/css/custom.css` file. These styles will be applied across the entire website and can be used to override or extend the theme's default styles.

### Templates

To customize the theme's HTML structure, you can override its templates. To do this, create a file with the same name and path in the project's `layouts/` directory. For example, to override the theme's header, you would create a file at `layouts/partials/header.html`. This new file will be used instead of the theme's original file at `themes/typo/layouts/partials/header.html`.

## Deployment

The website is automatically deployed to Vercel whenever changes are pushed to the `main` branch of the GitHub repository. Vercel detects the push, runs the `hugo` build command, and deploys the resulting static site from the `public/` directory.
