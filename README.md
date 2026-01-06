# Bin Wang's Personal Website

This is my personal academic website built with **Hugo** and hosted on GitHub Pages.

## Features

- ⚡ **Hugo Framework**: Fast static site generator (builds in < 1 second)
- 📦 **Single Executable**: No dependencies needed (just Hugo)
- 📝 **Markdown Support**: Write content in Markdown
- 🎨 **Data-Driven**: Content stored in YAML files for easy updates
- 🚀 **GitHub Pages Ready**: Auto-deploys via GitHub Actions
- 📱 **Responsive Design**: Works on all devices

## Quick Start

### Install Hugo

```bash
# macOS
brew install hugo

# Linux/Windows - Download from https://gohugo.io/installation/

# Verify installation
hugo version
```

### Local Development

```bash
# Enter Hugo directory
cd hugo

# Start development server
hugo server

# Visit http://localhost:1313
# The site will auto-reload when you make changes
```

### Build Site

```bash
cd hugo
hugo

# Built files are in hugo/public/ directory
```

## Project Structure

```
├── hugo/                      # Hugo project root
│   ├── config.yaml           # Site configuration (menu, params, etc.)
│   ├── content/               # Content pages (Markdown)
│   │   ├── blogs/            # Blog posts
│   │   ├── work/             # Work experience pages
│   │   └── education/        # Education pages
│   ├── data/                 # Data files (YAML) - Main content source
│   │   ├── work.yml          # Work experience data
│   │   ├── education.yml     # Education data
│   │   ├── projects.yml      # Projects data
│   │   ├── biography.yml     # Biography data
│   │   ├── teaching.yml      # Teaching data
│   │   ├── activities.yml    # Activities data
│   │   └── news.yml          # News data
│   ├── layouts/              # HTML templates
│   │   ├── index.html        # Homepage template
│   │   ├── work/             # Work experience templates
│   │   ├── education/        # Education templates
│   │   └── partials/         # Reusable components
│   ├── static/               # Static assets (CSS, JS, images)
│   └── public/               # Generated static site (gitignored)
├── assets/                   # Legacy static assets
├── .github/                  # GitHub Actions for auto-deployment
│   └── workflows/
│       └── hugo.yml          # Deployment workflow
├── old/                      # Old jemdoc website (archived)
└── CNAME                     # GitHub Pages custom domain
```

## How to Modify Content

### 1. Update Personal Information

Edit `hugo/config.yaml`:

```yaml
params:
  name: "Bin Wang"
  name_chinese: "王斌"
  title: "AI Research Scientist"
  affiliation: "MiroMind, Singapore"
  email:
    - "bwang28c@gmail.com"
  social:
    google_scholar: "https://scholar.google.com/..."
    github: "https://github.com/..."
    linkedin: "https://www.linkedin.com/..."
    twitter: "https://x.com/..."
```

### 2. Update Navigation Menu

Edit `hugo/config.yaml` under `menu.main`:

```yaml
menu:
  main:
    - identifier: "home"
      name: "Home"
      url: "/"
      weight: 1
    - identifier: "work"
      name: "Work Experience"
      url: "#"
      weight: 3
    # Add new menu items here
```

### 3. Add/Update Work Experience

Edit `hugo/data/work.yml`:

```yaml
miromind:
  position: "AI Research Scientist"
  period: "05/2025 - Present"
  location: "MiroMind, Singapore"
  research_focus: "Your research focus here"
  projects_key: "current"  # References projects.yml
  # Add more fields as needed
```

### 4. Add/Update Education

Edit `hugo/data/education.yml`:

```yaml
usc:
  degree: "Ph.D. in Electrical Engineering"
  period: "08/2017 - 05/2021"
  institution: "University of Southern California (USC)"
  supervisor: "Prof. Name"
  supervisor_url: "https://..."
  # Add more fields as needed
```

### 5. Add/Update Projects

Edit `hugo/data/projects.yml`:

```yaml
current:
  - title: "Project Name"
    description: "Project description"
    items:
      - name: "Project Link"
        url: "https://..."
        description: "Link description"
```

### 6. Add Blog Post

Create a new file in `hugo/content/blogs/`:

```bash
# Create new blog post
cd hugo/content/blogs
touch my-new-post.md
```

Edit the file:

```markdown
---
title: "My New Blog Post"
date: 2025-01-15
draft: false
summary: "Brief summary of the post"
---

Your blog content here in Markdown...
```

### 7. Update Other Content

- **Biography**: Edit `hugo/data/biography.yml`
- **Teaching**: Edit `hugo/data/teaching.yml`
- **Activities**: Edit `hugo/data/activities.yml`
- **News**: Edit `hugo/data/news.yml`

### 8. Update Homepage Content

Edit `hugo/layouts/index.html` for homepage structure, or modify the data files it references.

## Deployment

### Automatic Deployment (Recommended)

The website is **automatically deployed** to GitHub Pages via GitHub Actions when you push to the `master` branch.

**How it works:**
1. Push changes to `master` branch
2. GitHub Actions automatically:
   - Builds the Hugo site
   - Deploys to `gh-pages` branch
   - Updates GitHub Pages

**No manual steps needed!** Just commit and push:

```bash
git add .
git commit -m "Update content"
git push origin master
```

### Manual Deployment (if needed)

If you need to deploy manually:

```bash
# 1. Build the site
cd hugo
hugo

# 2. The built files are in hugo/public/

# 3. If using GitHub Pages with Actions (recommended):
#    - Just push to master, GitHub Actions handles it

# 4. If deploying manually to gh-pages branch:
cd public
git init
git add .
git commit -m "Deploy site"
git branch -M gh-pages
git remote add origin https://github.com/BinWang28/BinWang28.github.io.git
git push -f origin gh-pages
```

### GitHub Pages Configuration

1. Go to your repository settings on GitHub
2. Navigate to **Pages** section
3. Set **Source** to: `gh-pages` branch (or `GitHub Actions` if using workflow)
4. The site will be available at: `https://binwang28.github.io`

### Custom Domain

If you have a custom domain:
1. Add your domain to `CNAME` file
2. Configure DNS records as per GitHub Pages instructions
3. GitHub will automatically handle HTTPS

## Development Workflow

1. **Make changes** to content files (YAML, Markdown)
2. **Test locally**: `cd hugo && hugo server`
3. **Preview** at http://localhost:1313
4. **Commit and push** to `master` branch
5. **GitHub Actions** automatically builds and deploys
6. **Site updates** in a few minutes

## Troubleshooting

### Hugo not found
```bash
# macOS
brew install hugo

# Verify
hugo version
```

### Build errors
- Check YAML syntax in data files
- Verify all referenced files exist
- Check Hugo logs for specific errors

### Deployment not working
- Check `.github/workflows/hugo.yml` exists
- Verify GitHub Actions are enabled in repository settings
- Check Actions tab for error messages

### Site not updating
- Wait a few minutes for GitHub Pages to rebuild
- Clear browser cache
- Check if GitHub Actions workflow completed successfully

## Why Hugo?

✅ **Fast**: Builds in < 1 second  
✅ **Simple**: Single executable, no dependencies  
✅ **Easy**: Edit YAML files to update content  
✅ **Flexible**: Markdown + templates  
✅ **GitHub Pages**: Works seamlessly with GitHub Actions  
✅ **Data-Driven**: Content separated from presentation

## Old Website

The previous jemdoc-based website has been moved to the `old/` directory for reference.

## License

All content is © Bin Wang. All rights reserved.
