# Deployment Guide for AKora.dev

This guide covers deploying your AKora.dev blog to various hosting platforms.

## Prerequisites

- Domain `akora.dev` configured in Cloudflare
- Repository pushed to GitHub
- Local build tested successfully

## Netlify Deployment (Recommended)

### Initial Setup

1. **Connect Repository**
   - Go to [Netlify](https://netlify.com)
   - Click "New site from Git"
   - Connect your GitHub repository

2. **Build Settings**
   ```
   Build command: npm run build
   Publish directory: dist
   Node version: 18
   ```

3. **Environment Variables**
   ```
   SITE_URL=https://akora.dev
   ```

### Custom Domain Configuration

1. **In Netlify Dashboard**
   - Go to Site settings > Domain management
   - Add custom domain: `akora.dev`
   - Note the DNS targets provided

2. **In Cloudflare Dashboard**
   - Add CNAME record: `akora.dev` → `your-site.netlify.app`
   - Or use A records to Netlify's IP addresses
   - Enable Cloudflare proxy (orange cloud)

3. **SSL Configuration**
   - Netlify will automatically provision SSL
   - Cloudflare provides additional SSL/TLS encryption

### Deployment Workflow

```bash
# Local development
npm run dev

# Test build locally
npm run build
npm run preview

# Deploy (automatic on git push to main)
git add .
git commit -m "Update content"
git push origin main
```

## Alternative: Vercel Deployment

1. **Connect Repository**
   - Go to [Vercel](https://vercel.com)
   - Import your GitHub repository

2. **Build Settings**
   ```
   Framework Preset: Astro
   Build Command: npm run build
   Output Directory: dist
   ```

3. **Domain Configuration**
   - Add custom domain in Vercel dashboard
   - Configure DNS in Cloudflare similar to Netlify

## Manual Deployment

For any static hosting provider:

```bash
# Build the site
npm run build

# Upload the dist/ folder contents to your web server
# Ensure your web server serves index.html for routes
```

## Performance Optimization

### Cloudflare Settings

- **Caching**: Set to "Standard" or "Aggressive"
- **Minification**: Enable HTML, CSS, JS
- **Brotli Compression**: Enable
- **HTTP/2**: Enable

### Build Optimization

```bash
# Analyze bundle size
npm run build -- --verbose

# Check for unused dependencies
npx depcheck
```

## Monitoring

### Analytics Setup

Add to `src/site.config.ts`:

```typescript
// Optional analytics configuration
analytics: {
  googleAnalytics: 'G-XXXXXXXXXX', // Your GA4 ID
}
```

### Performance Monitoring

- Use Lighthouse CI for automated performance testing
- Monitor Core Web Vitals in Google Search Console
- Set up Cloudflare Analytics for traffic insights

## Troubleshooting

### Common Issues

1. **Build Failures**
   - Check Node.js version (use 18+)
   - Verify all dependencies are installed
   - Review build logs for specific errors

2. **DNS Issues**
   - Allow 24-48 hours for DNS propagation
   - Use `dig akora.dev` to verify DNS records
   - Check Cloudflare DNS settings

3. **SSL Certificate Issues**
   - Ensure Cloudflare SSL/TLS mode is "Full (strict)"
   - Wait for certificate provisioning (can take up to 24 hours)

### Support Resources

- [Netlify Documentation](https://docs.netlify.com/)
- [Cloudflare Documentation](https://developers.cloudflare.com/)
- [Astro Deployment Guide](https://docs.astro.build/en/guides/deploy/)

## Backup Strategy

```bash
# Regular content backup
git add src/content/
git commit -m "Backup content $(date)"
git push origin main

# Database backup (if using external CMS)
# Configure automated backups through your CMS provider
```

## Security Considerations

- Keep dependencies updated: `npm audit fix`
- Use environment variables for sensitive data
- Enable Cloudflare security features (DDoS protection, WAF)
- Regular security headers via Cloudflare or hosting provider
