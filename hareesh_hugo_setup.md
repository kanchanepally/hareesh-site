# Complete Setup Guide: hareesh.co with Hugo + Adritian Theme

## Part 1: Local Setup (30 minutes)

### 1. Install Hugo

**macOS:**
```bash
brew install hugo
```

**Windows:**
```bash
winget install Hugo.Hugo.Extended
```

**Linux:**
```bash
sudo snap install hugo
```

Verify: `hugo version` (should show v0.120+ extended)

### 2. Create Your Site

```bash
# Navigate to where you want your projects
cd ~/projects  # or wherever you keep code

# Create new Hugo site
hugo new site hareesh-site
cd hareesh-site

# Initialize git
git init
```

### 3. Install Adritian Theme

**Method A: Hugo Modules (Recommended - Easier Updates)**

```bash
# Initialize Hugo modules
hugo mod init github.com/yourusername/hareesh-site

# Create hugo.toml config file
# (Delete the default config.toml if it exists)
```

Create `hugo.toml` with this content:
```toml
baseURL = "https://hareesh.co/"
languageCode = "en-gb"
title = "Hareesh Kanchanepally"

[module]
  [module.hugoVersion]
    min = "0.92.0"
  [[module.imports]]
    path = "github.com/zetxek/adritian-free-hugo-theme"
```

Then:
```bash
# Download theme and dependencies
hugo mod get

# Copy package.json for npm dependencies
curl -O https://raw.githubusercontent.com/zetxek/adritian-free-hugo-theme/main/package.json

# Install npm dependencies (for Bootstrap CSS)
npm install
```

**Method B: Git Submodule (If you prefer)**

```bash
# Add theme as submodule (CORRECT URL)
git submodule add https://github.com/zetxek/adritian-free-hugo-theme.git themes/adritian

# Copy example config
cp themes/adritian/exampleSite/config.toml .

# Copy example content structure
cp -r themes/adritian/exampleSite/content/* content/

# Install npm dependencies
cp themes/adritian/package.json .
npm install
```

### 4. Test Locally

```bash
hugo server -D
```

Open browser: `http://localhost:1313`

**You should see the demo site running locally.**

---

## Part 2: Initial Customization (1 hour)

### 1. Edit config.toml

Open `config.toml` in your editor and update:

```toml
baseURL = "https://hareesh.co/"
languageCode = "en-gb"
title = "Hareesh Kanchanepally"
theme = "adritian"

[params]
  author = "Hareesh Kanchanepally"
  description = "Portfolio Director | Founder | Expert Generalist"
  
  # Your info
  [params.hero]
    title = "Hareesh Kanchanepally"
    subtitle = "Building digital sovereignty tools & enabling parents in the digital age"
    description = "Portfolio Director with focus on product development in agile delivery. Currently building MyDigitAlly (edtech) and Kith (digital sovereignty hardware)."
    
  # Social links
  [params.social]
    linkedin = "your-linkedin-url"
    github = "your-github-url"
    email = "your@email.com"

[menu]
  [[menu.main]]
    name = "Now"
    url = "/now/"
    weight = 1
  
  [[menu.main]]
    name = "Ventures"
    url = "/ventures/"
    weight = 2
  
  [[menu.main]]
    name = "Work"
    url = "/work/"
    weight = 3
  
  [[menu.main]]
    name = "Notes"
    url = "/notes/"
    weight = 4
  
  [[menu.main]]
    name = "About"
    url = "/about/"
    weight = 5
```

### 2. Create Your Core Pages

**content/now.md:**
```markdown
---
title: "What I'm Doing Now"
date: 2024-10-30
type: "page"
---

*Last updated: October 2024*

## Current Focus

### Building MyDigitAlly
Live edtech startup helping non-tech parents navigate their kids' digital world. We've launched:
- Weekly automated newsletter with research-based insights
- 5-minute e-learning tools
- Custom ChatGPT app (in development) using RAG + MCP

[Visit MyDigitAlly →](https://mydigitally.co.uk)

### Exploring Kith
Digital sovereignty hardware device - early stage. Building the infrastructure for true data ownership.

### Leading Product Portfolio
Portfolio Director role focusing on agile product development, prioritization, and rapid delivery.

---

*This is a [now page](https://nownownow.com/about). I update it every few months.*
```

**content/ventures/_index.md:**
```markdown
---
title: "Ventures"
description: "Projects I'm building"
---

I believe in building things that matter - tools that give people agency, knowledge, and sovereignty in the digital world.
```

**content/ventures/mydigitally.md:**
```markdown
---
title: "MyDigitAlly"
date: 2024-10-30
featured: true
image: "/images/mydigitally-hero.jpg"
categories: ["Active"]
tags: ["edtech", "parenting", "AI"]
---

## Empowering Parents in the Digital Age

MyDigitAlly is a freemium edtech startup that helps non-tech parents better navigate their kids' digital world.

### What We Do
- Research-based insights converted into 5-minute e-learning tools
- Weekly automated newsletter
- Non-judgmental approach to digital parenting
- Custom AI assistant grounded in our curriculum

### Current Status
Live and growing. Active newsletter subscribers, building AI-powered learning companion.

[Visit MyDigitAlly →](https://mydigitally.co.uk) | [Subscribe to Newsletter →](https://mydigitally.co.uk/newsletter)
```

**content/ventures/kith.md:**
```markdown
---
title: "Kith"
date: 2024-10-30
featured: true
categories: ["Exploration"]
tags: ["hardware", "privacy", "sovereignty"]
---

## Digital Sovereignty for Everyone

Kith is a hardware device concept focused on true digital sovereignty - giving individuals complete ownership and control of their digital lives.

### The Vision
In a world where our data is constantly extracted and monetized, Kith aims to provide infrastructure for genuine digital autonomy.

### Current Status
Early exploration phase. Researching hardware approaches, sovereignty protocols, and user needs.

*Updates coming as the project develops.*
```

**content/about.md:**
```markdown
---
title: "About"
type: "page"
---

## Expert Generalist

I'm a Portfolio Director, founder, and builder focused on creating tools that empower people in the digital age.

### What I Do

**By Day:** I lead product portfolios in agile delivery environments, focusing on prioritization, strategy, and rapid execution.

**By Night:** I build ventures at the intersection of technology, education, and digital sovereignty:
- **MyDigitAlly** - Helping parents navigate the digital world
- **Kith** - Exploring hardware solutions for digital sovereignty

### Approach

I believe in:
- Building in public
- Digital sovereignty and ownership
- AI-assisted development
- Shipping imperfectly and iterating
- The portfolio approach to life and work

### Get in Touch

Working on something interesting? Let's connect.

[LinkedIn](#) | [Email](mailto:your@email.com)
```

---

## Part 3: Deploy to Production (30 minutes)

### 1. Create GitHub Repository

```bash
# In your hareesh-site directory
git add .
git commit -m "Initial site setup"

# Create repo on GitHub (via web interface)
# Name it: hareesh-site

# Connect and push
git remote add origin https://github.com/yourusername/hareesh-site.git
git branch -M main
git push -u origin main
```

### 2. Deploy to Vercel (Same Place as MyDigitAlly)

1. Go to [vercel.com](https://vercel.com) (you're already logged in)
2. "Add New..." → "Project"
3. Import Git Repository → select `hareesh-site`
4. Framework Preset: Hugo
5. Build settings (Vercel auto-detects, but verify):
   - Build Command: `hugo --gc --minify`
   - Output Directory: `public`
   - Install Command: (leave default)
6. Environment Variables → Add:
   - `HUGO_VERSION` = `0.120.0`
7. Deploy

**Your site is now live at a Vercel URL** (something like `hareesh-site.vercel.app`)

**No charges - Vercel free tier includes unlimited projects + custom domains.**

### 3. Connect Custom Domain

1. In Vercel project: Settings → Domains
2. Add domain: `hareesh.co`
3. Vercel will show DNS configuration needed
4. Go to your domain registrar (wherever you manage hareesh.co DNS):
   
   **If using Vercel nameservers (recommended):**
   - Copy Vercel's nameservers
   - Update at your registrar
   
   **Or using existing DNS:**
   - Add A record: `@` → `76.76.21.21`
   - Add CNAME: `www` → `cname.vercel-dns.com`

5. Back in Vercel, verify domain
6. HTTPS automatically enabled

**Wait 10-60 minutes for DNS propagation.**

**Bonus:** Now both MyDigitAlly and hareesh.co are in one dashboard.

---

## Part 4: Obsidian Publishing Workflow

This workflow uses "Page Bundles," a powerful Hugo feature that keeps a post and its images together, making content much easier to manage.

### 1. In Obsidian: Create a Post Folder

Instead of creating a single note file, your new process for each post is to **create a folder**.

Inside your Obsidian vault, create a new folder for the post. Inside that folder, create your note and name it **`index.md`**. As you write, place all images for that post in the very same folder.

Your structure in Obsidian should look like this:
```
/My Obsidian Vault/
└── A New Post Title/
    ├── index.md
    └── an-image.jpg
```

### 2. In `index.md`: Add Front Matter and Content

Edit your `index.md` file. Ensure it has the correct front matter. The `draft: false` line is important to make sure the post is published.

```markdown
---
title: "My New Post Title"
date: 2025-11-08
draft: false
categories: ["Some categories:"]
---

This is the beginning of my post...
```

### 3. To Publish: Copy the Entire Folder

When your post is ready, copy the entire post folder (e.g., `A New Post Title/`) from your Obsidian vault into your Hugo project.

The destination should be inside a year-based folder for good organization:
`content/notes/2025/A New Post Title/`

### 4. Advanced Layout: Floating an Image

If you want an image to float to the right with text wrapping around it, you cannot use the standard Markdown `![alt](src)` syntax. Instead, you must use a raw HTML `<img>` tag.

Place this code in your `index.md` file where you want the image to appear (usually after the first paragraph):

```html
<img src="your-image-name.jpg" alt="A descriptive alt text" style="float: right; margin: 0 0 1rem 1.5rem; width: 35%; min-width: 250px; border-radius: 4px;">
```

**How to customize the image layout:**

You can change the values in the `style` attribute to adjust the look:
*   `float: right;`: Aligns the image to the right.
*   `margin: 0 0 1rem 1.5rem;`: Sets the margin in the order of `top`, `right`, `bottom`, `left`. The `1.5rem` left margin creates space between the image and the wrapping text. Change the first `0` to move the image down (e.g., `0.5rem`).
*   `width: 35%;`: Makes the image take up 35% of the available content width. Increase or decrease this to make the image larger or smaller.
*   `min-width: 250px;`: Ensures the image doesn't become too small on narrow screens.

### 5. Final Check and Deploy

Before deploying, always test locally to make sure everything looks correct:
```bash
hugo server -D
```
Once you are happy, commit and push your changes to deploy the new post via Vercel.

---

## Part 5: Branding & Polish (Sunday - 2 hours)

### Visual Identity

**Colors (to match your positioning):**
- Primary: Deep blue (trust, professionalism)
- Accent: Teal/cyan (innovation, technology)
- Keep Adritian's clean aesthetic

**Profile Photo:**
- Professional but approachable
- Place in `static/images/profile.jpg`
- Update in config.toml

**Venture Logos:**
- Create simple logos/hero images for MyDigitAlly and Kith
- Place in `static/images/`
- Reference in venture post frontmatter

### Content Hierarchy

**Homepage priority:**
1. Name + one-line positioning
2. Current ventures (MyDigitAlly + Kith)
3. Latest 2-3 posts from Notes
4. Call-to-action: "Working on something? Let's connect"

**Navigation:**
- Now (high priority - shows current focus)
- Ventures (your builds)
- Work (portfolio case studies)
- Notes (digital garden)
- About (the story)

---

## Part 6: Migration from WordPress (The AI-Assisted Way)

### Step 1: Export Your WordPress Content

1. Log into WordPress.com
2. Go to **Settings → Site → Site Tools → Export**
3. Select "Export All" 
4. Download the XML file (save as `wordpress-export.xml`)

### Step 2: AI-Assisted Conversion (Easiest Method)

**Use Claude or ChatGPT to convert your posts:**

1. Open the XML file in a text editor
2. Find a post you want to migrate (between `<item>` tags)
3. Copy the entire `<item>...</item>` block
4. Ask Claude:

```
Convert this WordPress post to Hugo markdown format:
[paste XML]

Use this frontmatter structure:
---
title: ""
date: YYYY-MM-DD
categories: [""]
tags: [""]
---
```

5. Claude will give you clean markdown → save to appropriate folder:
   - Portfolio/case studies → `content/work/post-title.md`
   - Blog posts → `content/notes/YYYY-MM-DD-post-title.md`

**Repeat for your 5-10 best posts.** Don't migrate everything - be selective.

### Step 3: Bulk Conversion Option (If You Have Many Posts)

**Using wordpress-to-hugo tool:**

```bash
# Install the tool
npm install -g wordpress-export-to-markdown

# Convert (creates a 'posts' folder)
npx wordpress-export-to-markdown --input=wordpress-export.xml

# Review and move to Hugo structure
mv posts/* content/notes/
```

**Then clean up:**
- Fix frontmatter format
- Remove WordPress shortcodes
- Update image paths
- Categorize properly (work vs notes)

### Step 4: Handle Images

**If posts have images:**

1. Download images from WordPress media library
2. Place in `static/images/posts/`
3. Update markdown image paths:
   ```markdown
   ![Alt text](/images/posts/image-name.jpg)
   ```

**Or keep images on WordPress.com temporarily:**
- Images will still load from their URLs
- Migrate later if needed

### Step 5: Curate, Don't Dump

**You don't need to migrate everything.** Select:

**For /work (3-5 posts):**
- Best portfolio case studies
- Clear demonstrations of delivery/strategy
- Posts that show your product/portfolio director skills

**For /notes (5-10 posts):**
- Posts that still resonate
- Evergreen thinking
- Good writing you're proud of

**Archive the rest:**
- Keep WordPress.com active for 1 more month as archive
- Or export to local backup
- Old posts probably don't need to follow you

### Step 6: Set Up URL Redirects

**Create `static/_redirects` file:**

```
# Old WordPress URLs → New Hugo URLs
/2023/05/old-post-title    /notes/old-post-title    301
/portfolio/case-study-1    /work/case-study-1       301

# Catch-all for old blog URLs
/*/*/                      /notes/                  301
```

Vercel will automatically handle these redirects.

### Step 7: Pre-Launch Testing

**Before switching DNS:**

1. Test all migrated posts on your Vercel preview URL
2. Check images load correctly
3. Verify frontmatter renders properly
4. Test mobile responsiveness
5. Check all internal links work

**Only when satisfied:** Switch hareesh.co DNS to Vercel

---

## Migration Timeline (Realistic)

**Saturday:** Get Hugo + Adritian running locally
**Sunday Morning:** Migrate 3-5 key posts using AI assistance
**Sunday Afternoon:** Polish, test, deploy
**Monday:** Switch DNS, keep WordPress.com active as backup
**1 week later:** Verify everything works, cancel WordPress.com

**Don't rush the migration. Better to launch with 5 great posts than 50 mediocre ones.**

---

## Part 7: Cross-Linking Ecosystem

### Update MyDigitAlly.co.uk

Add footer link:
```html
<a href="https://hareesh.co/about">About the Founder</a>
```

Add to About page:
```markdown
MyDigitAlly is founded by Hareesh Kanchanepally, a Portfolio Director and 
product leader. [Learn more about Hareesh →](https://hareesh.co)
```

### Update hareesh.co

In ventures/mydigitally.md, add clear CTAs:
- [Visit MyDigitAlly →](https://mydigitally.co.uk)
- [Subscribe to Weekly Newsletter →](https://mydigitally.co.uk/newsletter)

---

## Part 8: Launch Checklist

Before canceling WordPress:

- [ ] All core pages created (Now, Ventures, Work, Notes, About)
- [ ] Site live on hareesh.co with HTTPS
- [ ] 5-10 migrated posts published
- [ ] Profile photo and branding in place
- [ ] MyDigitAlly cross-links added
- [ ] Social links working
- [ ] Mobile responsive (test on phone)
- [ ] Google Search Console connected
- [ ] Analytics added (optional: Plausible for privacy-focused)

**Then:** Cancel WordPress.com subscription, redirect if possible.

---

## Ongoing: Publishing Rhythm

### Regular Updates (Low Effort)

**Monthly:**
- Update /now page (5 minutes)
- Quick Kith progress note if applicable

**When You Have Something to Share:**
- Copy from Obsidian → Hugo
- Commit → Push
- Live

**No pressure, no schedule, no guilt.**

---

## Troubleshooting

**Site not building on Netlify?**
- Check build logs
- Verify HUGO_VERSION environment variable
- Ensure theme submodule committed properly

**DNS not working?**
- Wait longer (can take up to 48 hours)
- Verify DNS records match Netlify's requirements
- Check with `dig hareesh.co`

**Theme not loading?**
- Ensure theme added as git submodule
- Run: `git submodule update --init --recursive`

**Need help?**
- Hugo docs: https://gohugo.io/documentation/
- Adritian theme: https://github.com/adrianaadeel/adritian-free-hugo-theme
- Ask Claude for specific issues

---

## Success State

By Sunday evening you have:

✅ Sovereignty-aligned infrastructure (you own everything)
✅ Professional portfolio site at hareesh.co
✅ Clear positioning as expert generalist + founder
✅ MyDigitAlly and Kith properly showcased
✅ Low-friction publishing workflow from Obsidian
✅ £35/year saved
✅ Walking the talk on digital ownership

**Now you can focus on building MyDigitAlly and Kith, knowing your digital home is solid.**
