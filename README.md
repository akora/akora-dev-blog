# AKora.dev Blog

A software developer blog built with [Astro](https://astro.build/) and the [MultiTerm](https://multiterm.stelclementine.com/) theme. Features technical tutorials, project showcases, and development insights.

## Features

- **59 Color Themes** - Interactive theme selector with popular coding themes
- **MDX Support** - Write posts in Markdown with JSX components
- **Content Collections** - Type-safe content management with Astro
- **Search** - Full-text search powered by Pagefind
- **RSS Feed** - Automatic RSS generation
- **Sitemap** - SEO-friendly sitemap generation
- **Syntax Highlighting** - Code blocks with line numbers and theme support
- **Math Support** - LaTeX math rendering with KaTeX
- **Responsive Design** - Mobile-first responsive layout

## Project Structure

```text
/
├── public/                 # Static assets
├── src/
│   ├── components/        # Reusable Astro components
│   ├── content/          # Blog posts and content
│   │   └── posts/        # Individual blog posts
│   ├── layouts/          # Page layouts
│   ├── pages/            # Route pages
│   ├── styles/           # Global styles
│   └── site.config.ts    # Site configuration
├── astro.config.mjs      # Astro configuration
└── package.json
```

## Development Commands

All commands are run from the root of the project:

| Command                | Action                                           |
| :--------------------- | :----------------------------------------------- |
| `npm install`          | Install dependencies                             |
| `npm run dev`          | Start local dev server at `localhost:4321`      |
| `npm run build`        | Build production site to `./dist/`              |
| `npm run postbuild`    | Generate search index after build               |
| `npm run preview`      | Preview build locally before deploying          |
| `npm run format`       | Format code with Prettier                       |

## Daily Workflow Commands

### Development Workflow

```bash
# Start development server
npm run dev

# Make changes to your blog
# ... edit content, add posts, customize theme ...

# Commit changes
git add .
git commit -m "Add new blog post about X"

# Push to both repositories
git push origin main    # Push to homelab Gitea (primary)
git push github main    # Push to GitHub (public/Netlify)

# Or push to both at once
git push origin main && git push github main
```

### Content Creation Workflow

```bash
# Create new blog post
touch src/content/posts/my-new-post.md

# Edit the post with your content
# Add frontmatter and markdown content

# Test locally
npm run dev

# Build and preview
npm run build
npm run preview

# Commit and deploy
git add .
git commit -m "Add post: My New Post"
git push origin main && git push github main
```

## Content Management

### Creating New Posts

1. Create a new `.md` or `.mdx` file in `src/content/posts/`
2. Add frontmatter with required fields:

```yaml
---
title: "Your Post Title"
description: "Brief description of your post"
publishDate: "2024-01-01"
tags: ["tag1", "tag2"]
---
```

### Content Types

- **Technical Tutorials** - Step-by-step guides and how-tos
- **Project Showcases** - Detailed project breakdowns and case studies
- **Development Insights** - Thoughts on development practices and tools

### Supported Content Features

- **Code Blocks** - Syntax highlighting with line numbers
- **Math Equations** - LaTeX support via KaTeX
- **Images** - Optimized image handling
- **Callouts** - Custom directive components
- **External Links** - Automatic external link handling

## Customization

### Theme Configuration

Edit `src/site.config.ts` to customize:

- Site metadata (title, description, author)
- Navigation links
- Social media links
- Theme settings
- SEO configuration

### Styling

- Global styles: `src/styles/global.css`
- Component styles: Individual component files
- Theme colors: Configured via the theme selector

## Deployment

### Manual Deployment

1. Build the site: `npm run build`
2. Deploy the `dist/` folder to your hosting provider

### Netlify Deployment

1. Connect your GitHub repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Configure custom domain in Netlify settings

### Domain Configuration

This site is configured for `akora.dev` domain. Update `site.config.ts` if using a different domain.

## Local Development Environment

The project is designed to be portable and isolated:

- All dependencies are managed via `package.json`
- Configuration is centralized in `site.config.ts`
- Content is stored in version-controlled markdown files
- No external database dependencies

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `npm run dev`
5. Submit a pull request

## License

This project is based on the MultiTerm theme by [stelcodes](https://github.com/stelcodes/multiterm-astro).
