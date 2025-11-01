# Deployment Guide
## Business Buddy Website

---

## Overview

This guide covers multiple deployment options for the Business Buddy website. Since this is a static website with no build process, deployment is straightforward across all platforms.

---

## Prerequisites

- Git installed locally
- GitHub account (for GitHub Pages)
- Website files ready in repository
- Google Sheets integration configured (optional)

---

## Deployment Options

### Option 1: GitHub Pages (Recommended for Open Source)

#### Advantages
- ✅ Free hosting
- ✅ Custom domain support
- ✅ HTTPS included
- ✅ Automatic deployment on push
- ✅ Good for public repositories
- ✅ CDN included (fast globally)

#### Step-by-Step Deployment

1. **Push Code to GitHub**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository on GitHub
   - Click **Settings**
   - Scroll to **Pages** section
   - Source: Select `main` branch
   - Folder: Select `/ (root)`
   - Click **Save**

3. **Wait for Deployment**
   - GitHub will build and deploy (1-2 minutes)
   - Check **Actions** tab for status
   - URL will be: `https://username.github.io/repository-name/`

4. **Custom Domain (Optional)**
   - Add CNAME file to repository with your domain
   - Configure DNS with your domain registrar:
     ```
     Type: CNAME
     Name: www
     Value: username.github.io
     ```
   - In GitHub Pages settings, add custom domain
   - Enable "Enforce HTTPS"

#### Updating the Site
```bash
git add .
git commit -m "Update content"
git push origin main
# Site updates automatically in 1-2 minutes
```

---

### Option 2: Netlify (Recommended for Production)

#### Advantages
- ✅ Free tier very generous
- ✅ Super fast deployment
- ✅ Instant preview URLs
- ✅ Forms built-in (alternative to Google Sheets)
- ✅ Edge CDN
- ✅ Automatic HTTPS
- ✅ Deploy previews for pull requests

#### Step-by-Step Deployment

1. **Create Netlify Account**
   - Go to [netlify.com](https://netlify.com)
   - Sign up with GitHub account

2. **Connect Repository**
   - Click "New site from Git"
   - Choose GitHub
   - Select your repository
   - Configure build settings:
     - **Build command**: (leave empty)
     - **Publish directory**: `.` or `/`
     - Click **Deploy site**

3. **Configure Domain**
   - Site will get random URL like `random-name-123.netlify.app`
   - Click **Domain settings**
   - Add custom domain or change subdomain

4. **Enable Features**
   - **Forms**: Built-in form handling (no Google Sheets needed)
   - **Analytics**: Enable Netlify Analytics
   - **Functions**: Add serverless functions if needed

#### Using Netlify Forms (Alternative to Google Sheets)

1. **Update HTML form**:
   ```html
   <form name="lead-form" method="POST" data-netlify="true">
     <input type="hidden" name="form-name" value="lead-form">
     <input type="text" name="name" required>
     <input type="email" name="email" required>
     <input type="text" name="company">
     <button type="submit">Submit</button>
   </form>
   ```

2. **View Submissions**:
   - Go to Netlify dashboard
   - Click on **Forms** tab
   - See all submissions
   - Export to CSV
   - Set up email notifications

#### Continuous Deployment
- Every push to `main` triggers automatic deployment
- Pull requests get preview URLs
- Rollback to previous version anytime

---

### Option 3: Vercel

#### Advantages
- ✅ Fast global CDN
- ✅ Free for personal projects
- ✅ Excellent performance
- ✅ Analytics included
- ✅ Easy custom domains

#### Step-by-Step Deployment

1. **Create Vercel Account**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub

2. **Import Repository**
   - Click "New Project"
   - Import from GitHub
   - Select BizBud repository

3. **Configure Project**
   - **Framework Preset**: Other
   - **Build Command**: (leave empty)
   - **Output Directory**: `.`
   - Click **Deploy**

4. **Custom Domain**
   - Project Settings > Domains
   - Add your domain
   - Configure DNS as instructed
   - HTTPS automatic

#### Updating
- Push to GitHub automatically deploys
- Preview deployments for branches
- Production deployment from `main`

---

### Option 4: Traditional Web Hosting (cPanel)

#### Suitable For
- Existing hosting account
- Shared hosting plans
- Traditional hosting providers

#### Step-by-Step Deployment

1. **Prepare Files**
   ```bash
   # Create deployment package
   zip -r bizbud-website.zip index.html assets/ -x "*.git*" -x "docs/*"
   ```

2. **Upload via FTP**
   - Use FileZilla or similar
   - Connect to your hosting
   - Upload to `public_html` or `www` directory
   - Upload:
     - `index.html`
     - `assets/` folder

3. **Or Use cPanel File Manager**
   - Login to cPanel
   - Open File Manager
   - Navigate to `public_html`
   - Upload zip file
   - Extract files

4. **Configure Domain**
   - Domain should already point to hosting
   - Set index.html as default document
   - Enable HTTPS (Let's Encrypt in cPanel)

#### Updating
```bash
# Re-upload changed files via FTP
# Or use deployment script:
#!/bin/bash
lftp -u username,password ftp.yourhost.com <<EOF
cd public_html
put index.html
mirror -R assets assets
bye
EOF
```

---

### Option 5: Firebase Hosting

#### Advantages
- ✅ Free tier
- ✅ Fast CDN
- ✅ Custom domains
- ✅ Easy SSL
- ✅ Good for Firebase ecosystem

#### Step-by-Step Deployment

1. **Install Firebase CLI**
   ```bash
   npm install -g firebase-tools
   ```

2. **Initialize Firebase**
   ```bash
   firebase login
   firebase init hosting
   ```
   - Choose "Use an existing project" or create new
   - Public directory: `.`
   - Single-page app: No
   - GitHub integration: Optional

3. **Deploy**
   ```bash
   firebase deploy
   ```

4. **Custom Domain**
   ```bash
   firebase hosting:channel:deploy production
   ```
   - Add custom domain in Firebase console
   - Configure DNS as instructed

#### Updating
```bash
firebase deploy
# Or set up GitHub Actions for auto-deploy
```

---

## Pre-Deployment Checklist

### Content Review
- [ ] All text content is final
- [ ] No placeholder text (Lorem ipsum)
- [ ] No "TODO" comments in code
- [ ] Contact information is correct
- [ ] Social media links work
- [ ] All images load correctly

### Technical Checks
- [ ] HTML validates (W3C validator)
- [ ] All links work (no 404s)
- [ ] Forms submit correctly
- [ ] Google Sheets integration configured
- [ ] Google Analytics added (if using)
- [ ] Favicon added
- [ ] Meta tags complete (title, description, OG tags)

### Performance
- [ ] Images optimized (< 1MB each)
- [ ] Page loads in < 3 seconds
- [ ] Mobile responsive
- [ ] Lighthouse score > 80

### Security
- [ ] HTTPS enabled
- [ ] External links have rel="noopener"
- [ ] No hardcoded secrets
- [ ] Form has spam protection

### Testing
- [ ] Tested on Chrome, Firefox, Safari
- [ ] Tested on mobile devices
- [ ] All buttons work
- [ ] Carousel functions properly
- [ ] Forms submit successfully

---

## Post-Deployment Tasks

### Immediate (Day 1)
1. **Verify Deployment**
   - [ ] Visit live URL
   - [ ] Test all functionality
   - [ ] Submit test form
   - [ ] Check Google Sheets receives data

2. **Set Up Monitoring**
   - [ ] Add to uptime monitor (UptimeRobot)
   - [ ] Set up Google Analytics
   - [ ] Configure error tracking
   - [ ] Test form submissions

3. **Share URLs**
   - [ ] Share with team
   - [ ] Update social media profiles
   - [ ] Add to email signatures

### Week 1
- [ ] Monitor analytics daily
- [ ] Check form submissions
- [ ] Review user feedback
- [ ] Fix any reported issues
- [ ] Optimize based on performance data

### Month 1
- [ ] Review analytics
- [ ] A/B test different CTAs
- [ ] Update content based on feedback
- [ ] Add more case studies
- [ ] Start SEO optimization

---

## Domain Configuration

### Purchasing a Domain

**Recommended Registrars:**
- Namecheap: https://namecheap.com
- Google Domains: https://domains.google
- Cloudflare: https://cloudflare.com

**Good Domain Options:**
- bizbud.co.th (primary)
- businessbuddy.co.th
- bizbud.com
- bizbuddy.co.th

### DNS Configuration

**For GitHub Pages:**
```
Type: A
Name: @
Value: 185.199.108.153
Value: 185.199.109.153
Value: 185.199.110.153
Value: 185.199.111.153

Type: CNAME
Name: www
Value: username.github.io
```

**For Netlify:**
```
Type: CNAME
Name: @
Value: apex-loadbalancer.netlify.com

Type: CNAME
Name: www
Value: your-site.netlify.app
```

**For Vercel:**
```
Type: A
Name: @
Value: 76.76.21.21

Type: CNAME
Name: www
Value: cname.vercel-dns.com
```

### SSL Certificate
- All recommended platforms provide free SSL
- Automatically renews
- Enable "Force HTTPS" in platform settings

---

## Environment Variables

If you need environment-specific configuration:

**Create `.env` file (don't commit):**
```bash
GOOGLE_SHEETS_URL=https://script.google.com/...
GA_TRACKING_ID=UA-XXXXX-Y
CONTACT_EMAIL=hello@bizbud.co.th
```

**For Netlify:**
- Site Settings > Build & Deploy > Environment
- Add each variable

**For Vercel:**
- Project Settings > Environment Variables
- Add each variable

**For GitHub Pages:**
- Use GitHub Secrets
- Access in Actions workflow

---

## Continuous Integration/Deployment (CI/CD)

### GitHub Actions Workflow

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Production

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2
    
    - name: Validate HTML
      run: |
        sudo apt-get install -y tidy
        tidy -q -e index.html || true
    
    - name: Deploy to Netlify
      uses: nwtgck/actions-netlify@v1.2
      with:
        publish-dir: '.'
        production-deploy: true
      env:
        NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
        NETLIFY_SITE_ID: ${{ secrets.NETLIFY_SITE_ID }}
```

---

## Rollback Procedures

### GitHub Pages
```bash
git revert HEAD
git push origin main
# Wait 1-2 minutes for deployment
```

### Netlify
- Go to Deploys tab
- Click on previous successful deploy
- Click "Publish deploy"
- Instant rollback

### Vercel
- Go to Deployments
- Click on previous deployment
- Click "Promote to Production"
- Instant rollback

---

## Troubleshooting

### Issue: Site not loading after deployment

**Solution:**
1. Check deployment status in platform dashboard
2. Verify DNS propagation (use whatsmydns.net)
3. Clear browser cache
4. Check for build errors in logs

### Issue: Images not displaying

**Solution:**
1. Check file paths (case-sensitive)
2. Verify images are in correct directory
3. Check `.gitignore` doesn't exclude images
4. Test image URLs directly

### Issue: Form not submitting

**Solution:**
1. Check Google Sheets URL is correct
2. Verify Web App is deployed
3. Check browser console for errors
4. Test form with test data

### Issue: HTTPS not working

**Solution:**
1. Wait for SSL certificate provisioning (can take 24 hours)
2. Check DNS configuration
3. Enable "Force HTTPS" in settings
4. Clear browser cache

---

## Performance Optimization

### Before Deployment
```bash
# Optimize images
npm install -g sharp-cli
sharp -i assets/images/*.jpg -o assets/images/optimized/ --quality 85

# Or use online tools:
# - TinyPNG: https://tinypng.com
# - Squoosh: https://squoosh.app
```

### CDN Configuration
- All recommended platforms include CDN
- No additional configuration needed
- Files served from edge locations globally

### Caching Headers
Most platforms handle this automatically. For custom hosting:

**.htaccess (Apache):**
```apache
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType image/jpg "access plus 1 year"
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType text/javascript "access plus 1 month"
</IfModule>
```

---

## Monitoring & Analytics

### Google Analytics Setup

1. **Create GA4 Property**
   - Go to analytics.google.com
   - Create new property
   - Get Measurement ID (G-XXXXXXXXXX)

2. **Add to Website**
   ```html
   <!-- Add before </head> -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'G-XXXXXXXXXX');
   </script>
   ```

### Uptime Monitoring

**UptimeRobot (Free):**
1. Sign up at uptimerobot.com
2. Add new monitor (HTTP/HTTPS)
3. Enter your website URL
4. Set check interval (5 minutes)
5. Add alert contacts (email, SMS)

**Alternative: Pingdom, StatusCake**

### Error Tracking

**Sentry (Free tier):**
```html
<script src="https://browser.sentry-cdn.com/7.x.x/bundle.min.js"></script>
<script>
  Sentry.init({
    dsn: 'YOUR_SENTRY_DSN',
    environment: 'production'
  });
</script>
```

---

## Backup Strategy

### Automated Backups

**GitHub (Primary Backup):**
- All code in version control
- Commit history is backup
- Can restore any previous version

**Monthly Export:**
```bash
#!/bin/bash
# backup.sh
DATE=$(date +%Y-%m-%d)
mkdir -p backups/$DATE
cp -r . backups/$DATE/
zip -r backups/bizbud-$DATE.zip backups/$DATE/
```

**Google Sheets Backup:**
- See GOOGLE_SHEETS_SETUP.md
- Weekly automatic backups
- Manual export monthly

---

## Cost Estimate

| Platform | Free Tier | Paid Plans |
|----------|-----------|------------|
| **GitHub Pages** | Unlimited public repos | N/A for static sites |
| **Netlify** | 100GB bandwidth/month | Starts at $19/month |
| **Vercel** | 100GB bandwidth/month | Starts at $20/month |
| **Firebase** | 10GB storage, 360MB/day | Pay as you go |
| **Domain** | N/A | $10-15/year |
| **Email** | Free (Gmail) | $6/month (Google Workspace) |

**Recommended Free Setup:**
- **Hosting**: GitHub Pages or Netlify (Free)
- **Domain**: $12/year
- **Email**: Gmail (Free)
- **Analytics**: Google Analytics (Free)
- **Monitoring**: UptimeRobot (Free)
- **Total**: ~$12/year

---

## Support & Resources

### Documentation
- GitHub Pages: https://pages.github.com
- Netlify: https://docs.netlify.com
- Vercel: https://vercel.com/docs
- Firebase: https://firebase.google.com/docs/hosting

### Community
- Stack Overflow
- GitHub Discussions
- Platform-specific forums

### Professional Support
- Hire developer via Upwork/Fiverr
- Contact platform support teams
- Thai dev communities

---

**Last Updated**: November 2024  
**Version**: 1.0  
**Maintained by**: Business Buddy Development Team
