# Cloudflare Configuration Guide

This document outlines the Cloudflare configuration for safetyarcher.com.

## DNS Configuration

### Root Domain (TLD)
- **Type**: CNAME or A record
- **Name**: `@` (root)
- **Target**: Cloudflare Pages URL or hosting provider
- **Proxy Status**: Proxied (orange cloud)

### Subdomains
Each application can have its own subdomain:

#### Example: .NET Web App
- **Type**: CNAME
- **Name**: `app` (or your chosen subdomain)
- **Target**: Application hosting URL
- **Proxy Status**: Proxied

#### Example: API Endpoint
- **Type**: CNAME
- **Name**: `api`
- **Target**: API hosting URL
- **Proxy Status**: Proxied

## Cloudflare Pages Setup (for Static Site)

### Initial Setup
1. Log in to Cloudflare Dashboard
2. Navigate to Pages
3. Click "Create a project"
4. Connect to GitHub repository: `safetyarcher/SafetyDev`
5. Configure build settings:
   - **Framework preset**: None
   - **Build command**: (leave empty for static)
   - **Build output directory**: `.` or `/` (leave empty)
   - **Root directory**: `www`

**Important**: The static site includes `_headers` and `_redirects` files for security and routing configuration.

### Custom Domain
1. In Pages project settings, go to "Custom domains"
2. Add `safetyarcher.com`
3. Cloudflare will automatically configure DNS

## SSL/TLS Settings

Recommended settings:
- **SSL/TLS encryption mode**: Full (strict)
- **Always Use HTTPS**: On
- **Automatic HTTPS Rewrites**: On
- **Minimum TLS Version**: 1.2 or higher

## Performance Optimization

### Caching
- **Caching Level**: Standard
- **Browser Cache TTL**: Respect Existing Headers

### Speed
- **Auto Minify**: Enable for HTML, CSS, JavaScript
- **Brotli**: Enabled
- **Early Hints**: Enabled

## Security

### Recommended Settings
- **Security Level**: Medium
- **Challenge Passage**: 30 minutes
- **Browser Integrity Check**: On
- **Privacy Pass Support**: On

### Firewall Rules (Optional)
Create rules as needed for specific applications

## Page Rules (Optional)

### Force HTTPS
- URL: `http://*safetyarcher.com/*`
- Setting: Always Use HTTPS

### Cache Everything for Static Assets
- URL: `*safetyarcher.com/*.css`
- Settings: Cache Level: Cache Everything, Edge Cache TTL: 1 month

## Multiple Applications Deployment

### Strategy 1: Subdomain per Application
Each app runs on its own subdomain with separate hosting:
- `safetyarcher.com` → Static home page (Cloudflare Pages)
- `app.safetyarcher.com` → .NET web app (Azure/AWS)
- `api.safetyarcher.com` → Node.js API (Vercel/Heroku)

### Strategy 2: Path-based Routing
Use Cloudflare Workers to route different paths to different apps:
- `safetyarcher.com/` → Static home
- `safetyarcher.com/app/` → .NET application
- `safetyarcher.com/api/` → API endpoints

## Monitoring

- Enable **Analytics** in Cloudflare Dashboard
- Set up **Alerts** for downtime or traffic spikes
- Review **Security Events** regularly

## Troubleshooting

### DNS Propagation
- DNS changes can take up to 24-48 hours to propagate globally
- Use `dig` or `nslookup` to verify DNS records
- Check DNS propagation at https://www.whatsmydns.net/

### SSL Issues
- Ensure origin server has valid SSL certificate
- Verify SSL/TLS mode matches your setup
- Check certificate validity dates

### Purge Cache
If changes aren't reflecting:
1. Go to Caching > Configuration
2. Click "Purge Everything" or "Purge by URL"
