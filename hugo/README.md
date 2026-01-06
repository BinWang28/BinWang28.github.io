# Bin Wang Personal Homepage - Hugo Version

## Quick Start

### 1. Install Hugo

```bash
# macOS
brew install hugo

# Verify installation
hugo version
```

### 2. Local Development

```bash
cd hugo
hugo server
# Visit http://localhost:1313
```

### 3. Build Website

```bash
hugo
# Generated files are in public/ directory
```

## Project Structure

```
hugo/
├── config.yaml              # Site configuration (personal info, menu, social links)
├── content/                 # Page content (Markdown)
│   ├── blogs/              # Blog posts
│   ├── work/               # Work experience pages
│   └── education/          # Education pages
├── data/                    # Data files (YAML)
│   ├── work.yml            # Work experience data (MiroMind, I²R, NUS, JD, Ontario)
│   ├── education.yml       # Education data (USC, UESTC, CityU, Jining)
│   └── projects.yml        # Projects data
├── layouts/                 # Template files
│   ├── index.html          # Homepage template
│   ├── work/single.html    # Work experience page template
│   ├── education/single.html # Education page template
│   └── partials/           # Shared components
├── static/assets/           # Static files (CSS, images, PDFs)
└── public/                  # Build output directory
```

## How to Modify Content

### Update Personal Info
Edit `config.yaml`:
```yaml
params:
  name: "Bin Wang"
  title: "AI Research Scientist"
  affiliation: "MiroMind, Singapore"
```

### Update Work Experience
Edit `data/work.yml`:
```yaml
miromind:
  position: "AI Research Scientist"
  period: "05/2025 - Present"
  location: "MiroMind, Singapore"
  research_section:
    topics_summary: "..."
    publications:
      - name: "Paper Title"
        url: "https://..."
        venue: "Conference 2025"
```

### Update Education
Edit `data/education.yml`:
```yaml
usc:
  degree: "Ph.D. in Electrical Engineering"
  period: "08/2017 - 05/2021"
  institution: "University of Southern California"
  supervisor: "C.-C. Jay Kuo (ACM Fellow, IEEE Fellow)"
```

### Add Blog Posts
Create a new `.md` file in `content/blogs/`:
```markdown
---
title: "Post Title"
date: 2025-01-10
draft: false
---

Post content...
```

## Deploy to GitHub Pages (Automatic)

This repository uses **GitHub Actions** for automatic deployment.

### Setup (One-time)

1. Go to your GitHub repository **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**

### Deploy

Simply push your changes:

```bash
git add .
git commit -m "Update website"
git push
```

GitHub Actions will automatically:
1. Build the Hugo site
2. Deploy to GitHub Pages

Your site will be live at: **https://binwang28.github.io**

### Workflow File

The deployment workflow is defined in `.github/workflows/hugo.yml`:
- Triggers on push to `master` branch
- Builds Hugo site with minification
- Deploys to GitHub Pages

## Main Pages

| Page | Path | Description |
|------|------|-------------|
| Home | `/` | Introduction, contact, featured publications |
| Blogs | `/blogs/` | Blog posts list |
| MiroMind | `/work/miromind/` | Current work |
| I²R | `/work/i2r/` | A*STAR experience |
| NUS | `/work/nus/` | NUS postdoc experience |
| USC | `/education/usc/` | Ph.D. degree |
| UESTC | `/education/uestc/` | Bachelor's degree |

## Notes

- Static assets go in `static/assets/` directory
- Images should be PNG or JPG format
- PDFs (resume, papers) go in `static/assets/data/`
- Run `hugo server` to preview changes locally

## Tech Stack

- **Hugo** - Static site generator
- **YAML** - Data file format
- **Markdown** - Content writing
- **GitHub Pages** - Website hosting
- **GitHub Actions** - Automatic deployment
