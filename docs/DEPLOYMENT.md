# Deployment Guide

This guide covers deployment strategies for the SafetyDev repository applications.

## Static Homepage (TLD)

### Cloudflare Pages Deployment

**Recommended for the static homepage at safetyarcher.com**

#### Prerequisites
- GitHub account connected to Cloudflare
- Domain configured in Cloudflare

#### Steps

1. **Connect Repository**
   - Go to Cloudflare Dashboard → Pages
   - Click "Create a project"
   - Select "Connect to Git"
   - Choose `safetyarcher/SafetyDev` repository
   - Authorize Cloudflare to access the repository

2. **Configure Build Settings**
   - **Project name**: safetyarcher (or your preference)
   - **Production branch**: main
   - **Framework preset**: None
   - **Root directory**: `www`
   - **Build command**: (leave empty)
   - **Build output directory**: `/` (or leave empty)

3. **Deploy**
   - Click "Save and Deploy"
   - Cloudflare will build and deploy your site
   - Initial deployment takes 1-2 minutes

4. **Custom Domain**
   - After deployment, go to Custom domains
   - Click "Set up a custom domain"
   - Enter `safetyarcher.com`
   - Cloudflare automatically configures DNS

5. **Verify**
   - Wait for DNS propagation (can take a few minutes)
   - Visit https://safetyarcher.com to see your site

#### Automatic Deployments
- Every push to `main` branch automatically triggers a new deployment
- Preview deployments created for pull requests
- Rollback available from Pages dashboard

---

## Future Applications (Subdomains)

### .NET Web Application Example

For a future .NET application on a subdomain (e.g., app.safetyarcher.com):

#### Azure App Service
1. Create Azure App Service
2. Configure deployment from GitHub
3. Set environment variables
4. In Cloudflare DNS, add CNAME:
   - Name: `app`
   - Target: `your-app.azurewebsites.net`
   - Proxy: Enabled

#### AWS Elastic Beanstalk
1. Create Elastic Beanstalk application
2. Deploy .NET application
3. In Cloudflare DNS, add CNAME:
   - Name: `app`
   - Target: `your-app.elasticbeanstalk.com`
   - Proxy: Enabled

### Node.js API Example

For a future API on api.safetyarcher.com:

#### Vercel
1. Import project from GitHub
2. Set root directory to `apps/api`
3. Configure build settings
4. In Cloudflare DNS, add CNAME:
   - Name: `api`
   - Target: Vercel deployment URL
   - Proxy: Enabled

#### Heroku
1. Create Heroku app
2. Connect to GitHub repository
3. Set buildpack and environment variables
4. In Cloudflare DNS, add CNAME:
   - Name: `api`
   - Target: `your-app.herokuapp.com`
   - Proxy: Enabled

---

## Environment Variables

### For Static Site
No environment variables needed for the static homepage.

### For Future Applications
Use environment variable management from your hosting provider:

- **Azure**: Application Settings
- **AWS**: Environment Properties
- **Vercel**: Environment Variables in project settings
- **Heroku**: Config Vars

**Never commit sensitive data like:**
- API keys
- Database credentials
- Secret tokens
- Private certificates

---

## CI/CD Pipeline (Optional)

### GitHub Actions Example

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Cloudflare Pages

on:
  push:
    branches:
      - main
    paths:
      - 'www/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to Cloudflare Pages
        uses: cloudflare/pages-action@v1
        with:
          apiToken: ${{ secrets.CLOUDFLARE_API_TOKEN }}
          accountId: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          projectName: safetyarcher
          directory: www
```

---

## Monitoring and Maintenance

### Cloudflare Analytics
- Monitor traffic in Cloudflare Dashboard
- View performance metrics
- Track security events

### Uptime Monitoring
Consider using:
- UptimeRobot
- Pingdom
- Cloudflare Health Checks

### SSL Certificate
- Cloudflare provides free SSL certificates
- Automatic renewal
- Supports both TLD and subdomains with wildcard cert

---

## Troubleshooting

### Site Not Loading
1. Check DNS settings in Cloudflare
2. Verify deployment status in Pages dashboard
3. Check browser console for errors
4. Clear Cloudflare cache

### SSL Certificate Issues
1. Ensure SSL/TLS mode is "Full (strict)"
2. Check certificate validity
3. Wait for certificate provisioning (can take up to 24 hours)

### Custom Domain Not Working
1. Verify DNS records are correct
2. Wait for DNS propagation
3. Check custom domain status in Pages settings
4. Ensure domain is not already in use elsewhere

---

## Rollback Procedure

If a deployment causes issues:

1. Go to Cloudflare Pages dashboard
2. Click on your project
3. View deployments history
4. Click "Rollback" on a previous working deployment
5. Confirm rollback

---

## Support

For issues with:
- **Cloudflare**: https://support.cloudflare.com/
- **Repository structure**: See README.md
- **Specific applications**: Check app-specific documentation
