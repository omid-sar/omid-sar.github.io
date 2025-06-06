# Personal Blog Management Guide

A comprehensive guide for managing your Jekyll blog hosted on GitHub Pages.

## 📝 Publishing Blog Posts

### Creating a New Post

1. **File Location**: Create new `.md` files in the `_posts/` directory
2. **File Naming**: Use format `YYYY-MM-DD-title-with-hyphens.md`
   - Example: `2024-12-06-my-awesome-post.md`

3. **Front Matter**: Every post needs this header:
```yaml
---
layout: post
title: "Your Post Title"
subtitle: "Optional subtitle"
date: 2024-12-06 10:30:00
tags: [programming, tutorial, personal]
comments: true
author: Omid Sar
---
```

### From Obsidian to Blog

#### Method 1: Direct Copy (Recommended)
1. **Write in Obsidian** using standard markdown
2. **Copy content** from your Obsidian note
3. **Create new file** in `_posts/` with proper naming
4. **Add front matter** at the top
5. **Paste content** below front matter
6. **Commit and push** (see deployment section)

#### Method 2: Export and Edit
1. **Export from Obsidian** as markdown
2. **Move file** to `_posts/` directory
3. **Rename file** to Jekyll format (`YYYY-MM-DD-title.md`)
4. **Add front matter** at the beginning
5. **Fix any Obsidian-specific syntax** (see conversions below)

#### Obsidian → Jekyll Conversions

**Internal Links:**
- Obsidian: `[[Other Note]]`
- Jekyll: `[Other Note]({% post_url 2024-01-01-other-note %})`

**Images:**
- Obsidian: `![[image.png]]`
- Jekyll: `![Alt text](/assets/img/image.png)`

**Tags:**
- Obsidian: `#tag`
- Jekyll: Add to front matter `tags: [tag]`

**Math:**
- Both use LaTeX: `$$math$$` (block) or `$math$` (inline)

## 🚀 Deployment Workflow

### Local Development
```bash
# Start local server (from project root)
docker compose up

# View at: http://localhost:4000
# Auto-reloads when you save files
```

### Publishing to Live Site
```bash
# Add your changes
git add .

# Commit with descriptive message
git commit -m "Add new post about [topic]"

# Push to GitHub (triggers automatic deployment)
git push origin main

# Your blog updates at https://omid-sar.github.io in 2-5 minutes
```

## 🎨 Customization Guide

### Changing Blog Information

**File**: `_config.yml`

```yaml
# Basic Information
title: Omid's Blog
author: Omid Sar
description: Your blog description

# Social Media Links
social-network-links:
  email: "mr.omid.sardari@gmail.com"
  github: omid-sar
  linkedin: omidsar
  twitter: omidsard
  # Add more as needed

# Blog Settings
excerpt_length: 50        # Preview text length
feed_show_excerpt: true   # Show previews on homepage
feed_show_tags: true      # Show tags on homepage
post_search: true         # Enable search functionality
```

### Adding New Pages

1. **Create file** in root directory: `newpage.md`
2. **Add front matter**:
```yaml
---
layout: page
title: "New Page"
subtitle: "Page description"
---
```
3. **Add to navigation** in `_config.yml`:
```yaml
navbar-links:
  About: "aboutme"
  Archive: "archive"
  New Page: "newpage"    # Add this line
```

### Modifying Colors and Styling

**File**: `_config.yml` (Basic colors)
```yaml
page-col: "#FFFFFF"      # Background color
text-col: "#404040"      # Text color
link-col: "#008AFF"      # Link color
navbar-col: "#EAEAEA"    # Navigation bar color
```

**File**: `assets/css/theme.css` (Advanced styling)
- Modify CSS variables for dark/light themes
- Add custom styling for specific elements

### Adding Custom CSS

1. **Create CSS file**: `assets/css/custom.css`
2. **Add to config**: In `_config.yml`:
```yaml
site-css:
  - "/assets/css/theme.css"
  - "/assets/css/custom.css"    # Add this line
```

### Adding Custom JavaScript

1. **Create JS file**: `assets/js/custom.js`
2. **Add to config**: In `_config.yml`:
```yaml
site-js:
  - "/assets/js/theme-toggle.js"
  - "/assets/js/custom.js"       # Add this line
```

## 📁 Directory Structure

```
your-blog/
├── _posts/                 # Blog posts go here
│   ├── 2024-12-06-hello-world.md
│   └── 2024-12-07-new-post.md
├── _includes/              # Reusable HTML components
├── _layouts/               # Page templates
├── assets/
│   ├── css/               # Stylesheets
│   ├── js/                # JavaScript files
│   └── img/               # Images
├── _config.yml            # Main configuration
├── index.html             # Homepage
├── aboutme.md             # About page
└── archive.md             # Archive page
```

## 🖼️ Adding Images

### Method 1: Assets Folder
1. **Upload image** to `assets/img/`
2. **Reference in post**:
```markdown
![Image description](/assets/img/your-image.jpg)
```

### Method 2: External Hosting
1. **Upload to** GitHub, Imgur, or other service
2. **Use direct URL**:
```markdown
![Image description](https://example.com/image.jpg)
```

## 🏷️ Tags and Categories

### Adding Tags to Posts
```yaml
---
tags: [programming, tutorial, jekyll, markdown]
---
```

### Creating Tag Pages
1. **Create file**: `tag/programming.md`
2. **Add content**:
```yaml
---
layout: tag
title: "Programming Posts"
tag: programming
---
```

## 💬 Comments Setup

### GitHub Discussions (Recommended)
1. **Enable Discussions** in your GitHub repository
2. **Uncomment in `_config.yml`**:
```yaml
utterances:
  repository: omid-sar/omid-sar.github.io
  issue-term: pathname
  theme: github-light
```

## 📊 Analytics Setup

### Google Analytics
1. **Get tracking ID** from Google Analytics
2. **Add to `_config.yml`**:
```yaml
gtag: "G-XXXXXXXXXX"
```

## 🔧 Maintenance Tasks

### Regular Maintenance
- **Update dependencies**: Occasionally update `Gemfile`
- **Backup content**: Your posts are safe in Git, but backup locally too
- **Monitor performance**: Check site speed and responsiveness
- **Update social links**: Keep contact information current

### Troubleshooting

**Site not updating?**
1. Check GitHub Pages build status in repository settings
2. Verify front matter syntax in posts
3. Ensure file names follow `YYYY-MM-DD-title.md` format

**Local development not working?**
1. Ensure Docker is running: `docker compose ps`
2. Restart container: `docker compose restart`
3. Check for typos in `_config.yml`

**Styling issues?**
1. Clear browser cache
2. Check CSS file paths in `_config.yml`
3. Validate CSS syntax

## 📝 Content Ideas and Organization

### Post Categories Suggestions
- **Technical Tutorials**: Step-by-step guides
- **Project Showcases**: Your coding projects
- **Learning Notes**: From courses, books, conferences
- **Personal Reflections**: Career insights, lessons learned
- **Tool Reviews**: Software, libraries, frameworks you use

### Obsidian Integration Tips
- **Use templates** in Obsidian for consistent post structure
- **Create a "Blog Posts" folder** in Obsidian
- **Use tags consistently** between Obsidian and Jekyll
- **Keep a "Ideas" note** for future post topics

## 🚀 Advanced Features

### Adding Search
Search is already enabled! Users can use the search button in navigation.

### RSS Feed
Automatically generated at `/feed.xml` - visitors can subscribe for updates.

### SEO Optimization
- Use descriptive titles and subtitles
- Add relevant tags
- Include meta descriptions
- Use proper heading structure (H1, H2, H3)

### Mobile Responsiveness
Your theme is already mobile-responsive, but test on different devices.

---

## 📞 Need Help?

- **GitHub Issues**: For Jekyll/theme problems
- **Jekyll Documentation**: https://jekyllrb.com/docs/
- **Beautiful Jekyll**: https://beautifuljekyll.com/
- **Markdown Guide**: https://www.markdownguide.org/

Happy blogging! 🎉 