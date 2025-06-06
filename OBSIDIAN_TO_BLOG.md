# Obsidian → Blog Quick Reference

## 🚀 Quick Workflow

1. **Write note in Obsidian** using standard markdown
2. **Copy content** (Ctrl/Cmd + A, then Ctrl/Cmd + C)
3. **Create new file** in `_posts/` folder: `2024-12-07-your-title.md`
4. **Add front matter**:
```yaml
---
layout: post
title: "Your Title"
subtitle: "Optional subtitle"
tags: [tag1, tag2, tag3]
comments: true
author: Omid Sar
---
```
5. **Paste content** below front matter
6. **Fix any Obsidian syntax** (see conversions below)
7. **Commit and push**:
```bash
git add .
git commit -m "Add post: Your Title"
git push origin main
```

## 📝 Obsidian → Jekyll Syntax Conversions

| Feature | Obsidian | Jekyll |
|---------|----------|--------|
| **Internal Links** | `[[Note Title]]` | `[Note Title]({% post_url 2024-01-01-note-title %})` |
| **Images** | `![[image.png]]` | `![Alt text](/assets/img/image.png)` |
| **Tags** | `#programming #tutorial` | `tags: [programming, tutorial]` (in front matter) |
| **Backlinks** | Automatic | Manual linking required |
| **Block References** | `![[note#^block]]` | Copy content directly |
| **Embeds** | `![[note#heading]]` | Copy content or use includes |

## 🖼️ Handling Images from Obsidian

### Method 1: Copy Images to Blog
1. **Copy image files** from Obsidian vault to `assets/img/`
2. **Update image references**:
   - From: `![[my-image.png]]`
   - To: `![Description](/assets/img/my-image.png)`

### Method 2: Use External Hosting
1. **Upload image** to GitHub, Imgur, or other service
2. **Get direct URL** and use in post
3. **Replace Obsidian syntax** with standard markdown

## 🏷️ Tag Management

### In Obsidian
```markdown
#programming #javascript #tutorial #webdev
```

### In Jekyll Front Matter
```yaml
tags: [programming, javascript, tutorial, webdev]
```

## 📋 Obsidian Template for Blog Posts

Create this template in Obsidian for consistent blog post structure:

```markdown
# {{title}}

**Date:** {{date}}
**Tags:** #tag1 #tag2 #tag3
**Status:** Draft/Ready/Published

## Summary
Brief summary of what this post covers...

## Content
Main content here...

## Key Takeaways
- Point 1
- Point 2
- Point 3

## References
- [Link 1](url)
- [Link 2](url)

---
**Blog Front Matter:**
```yaml
---
layout: post
title: "{{title}}"
subtitle: "Brief description"
tags: [tag1, tag2, tag3]
comments: true
author: Omid Sar
---
```
```

## 🔄 Batch Processing Tips

### For Multiple Posts
1. **Export multiple notes** from Obsidian as markdown
2. **Use a script** or batch rename to add dates
3. **Add front matter** to each file
4. **Move to `_posts/` directory**
5. **Commit all at once**

### Maintaining Sync
- **Keep a "Blog Posts" folder** in Obsidian
- **Use consistent naming** between Obsidian and Jekyll
- **Tag consistently** in both systems
- **Regular exports** to keep blog updated

## ⚡ Pro Tips

1. **Preview locally** with `docker compose up` before publishing
2. **Use descriptive filenames** for better organization
3. **Keep images organized** in subfolders under `assets/img/`
4. **Use relative links** for internal blog references
5. **Test on mobile** after publishing

## 🚨 Common Issues & Solutions

**Issue**: Internal links don't work
**Solution**: Convert `[[links]]` to proper Jekyll post URLs

**Issue**: Images not showing
**Solution**: Ensure images are in `assets/img/` and paths are correct

**Issue**: Tags not displaying
**Solution**: Check front matter YAML syntax and indentation

**Issue**: Post not appearing
**Solution**: Verify filename format: `YYYY-MM-DD-title.md`

**Issue**: Broken formatting
**Solution**: Check for Obsidian-specific syntax that needs conversion 