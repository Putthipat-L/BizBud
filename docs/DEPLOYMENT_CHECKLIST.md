# Pre-Deployment Checklist
## Business Buddy Website

---

## ⚠️ Critical Configuration Items

Before deploying to production, ensure all placeholder values are replaced:

### 1. Google Sheets Integration
- [ ] Google Sheets Web App URL configured in `index.html`
  - Search for: `YOUR_GOOGLE_SHEETS_WEB_APP_URL_HERE`
  - Replace with: Your actual Google Apps Script Web App URL
  - Guide: `docs/GOOGLE_SHEETS_SETUP.md`

### 2. Contact Information
- [ ] Phone number updated in `index.html` (CRITICAL - 2 locations)
  - Search for: `02-XXX-XXXX`
  - Replace with: Actual business phone number (e.g., `02-123-4567`)
  - Location 1: Contact section footer
  - Location 2: Error message in form handler (line ~930)
- [ ] Email address verified
  - Check: `hello@bizbud.co.th` is correct
  - Update if different
  - Also update in `docs/GOOGLE_SHEETS_SETUP.md` if using email notifications

### 3. Pricing Information
- [ ] Package pricing updated in `index.html`
  - Search for: `฿XX,XXX`
  - Replace with: Actual package prices
  - Found in 3 locations (Biz Survive, Biz Scale, Biz Sustain)

---

## 📋 Content Review

### Text Content
- [ ] All placeholder text removed (no Lorem ipsum)
- [ ] Thai and English text reviewed for accuracy
- [ ] No "TODO" comments in code
- [ ] Company name spelling consistent
- [ ] All headings and taglines approved

### Images
- [ ] Logo displays correctly (`assets/images/bizbud-logo.png`)
- [ ] All 4 carousel images load (`carousel-1.jpg` through `carousel-4.jpg`)
- [ ] Line QR code is correct and scannable (`line-qr.jpg`)
- [ ] All images optimized (< 1MB each)

### Links
- [ ] Social media links updated
  - Facebook: Currently `https://facebook.com`
  - Instagram: Currently `https://instagram.com`
- [ ] All internal navigation links work
- [ ] External links open in new tabs
- [ ] Privacy Policy link (currently placeholder)
- [ ] Terms of Service link (currently placeholder)

---

## 🧪 Functionality Testing

### Interactive Features
- [ ] Navigation scroll works smoothly
- [ ] "Book Queue" buttons scroll to contact section
- [ ] Package selection shows toast notification
- [ ] Line button shows QR instruction notification
- [ ] Toast notifications display and auto-dismiss
- [ ] Carousel auto-plays (if motion not reduced)
- [ ] Carousel manual controls work (prev/next/indicators)

### Form Testing
- [ ] Form validates required fields
- [ ] Email format validation works
- [ ] Form submission succeeds (if Google Sheets configured)
- [ ] Success message displays correctly
- [ ] Error handling works gracefully

### Responsive Design
- [ ] Mobile view (< 768px) works correctly
- [ ] Tablet view (768px - 1024px) works correctly
- [ ] Desktop view (> 1024px) works correctly
- [ ] Images responsive and don't overflow
- [ ] Text readable on all screen sizes
- [ ] Buttons touch-friendly on mobile

---

## 🚀 Performance

### Page Speed
- [ ] Google PageSpeed Insights score > 80
- [ ] Images compressed and optimized
- [ ] Page loads in < 3 seconds on 4G
- [ ] No console errors in browser

### SEO
- [ ] Page title is descriptive
- [ ] Meta description present and compelling
- [ ] Open Graph tags added (for social sharing)
- [ ] Favicon present
- [ ] Heading hierarchy proper (h1 → h2 → h3)

---

## 🔒 Security

### Code Security
- [ ] No API keys or secrets in code
- [ ] External links use `rel="noopener noreferrer"`
- [ ] HTTPS enabled on hosting platform
- [ ] Form has basic spam protection (validation)

### Privacy & Legal
- [ ] Privacy Policy created and linked
- [ ] Terms of Service created and linked
- [ ] Cookie consent implemented (if using analytics)
- [ ] GDPR compliance considered (if applicable)

---

## 📊 Analytics & Monitoring

### Analytics Setup
- [ ] Google Analytics installed (if using)
  - Add tracking ID to code
  - Test events are firing
- [ ] Google Tag Manager configured (if using)
- [ ] Facebook Pixel installed (if using)

### Monitoring
- [ ] Uptime monitoring configured (UptimeRobot, etc.)
- [ ] Error tracking setup (Sentry, etc.)
- [ ] Form submission notifications working
- [ ] Email alerts configured for downtime

---

## 🌐 Domain & Hosting

### Domain Configuration
- [ ] Domain purchased and registered
- [ ] DNS configured correctly
- [ ] SSL certificate active
- [ ] WWW and non-WWW both work
- [ ] Redirect to HTTPS enabled

### Hosting Platform
- [ ] Code deployed to hosting
- [ ] Environment variables set (if any)
- [ ] Build succeeded
- [ ] Live URL accessible
- [ ] Previous version backed up

---

## 📱 Cross-Browser Testing

### Desktop Browsers
- [ ] Chrome (latest version)
- [ ] Firefox (latest version)
- [ ] Safari (latest version)
- [ ] Edge (latest version)

### Mobile Browsers
- [ ] iOS Safari (iPhone)
- [ ] Chrome Mobile (Android)
- [ ] Samsung Internet
- [ ] Testing on actual devices (not just emulators)

---

## ♿ Accessibility

### WCAG Compliance
- [ ] Color contrast meets AA standards
- [ ] Images have alt text
- [ ] Headings hierarchical
- [ ] Keyboard navigation works
- [ ] Screen reader tested (NVDA or VoiceOver)
- [ ] ARIA labels present on interactive elements

---

## 📧 Post-Deployment

### Immediate Actions (Day 1)
- [ ] Visit live site and test all features
- [ ] Submit test form and verify data received
- [ ] Check Google Sheets receives submissions
- [ ] Verify email notifications working
- [ ] Share URL with team
- [ ] Update social media profiles with new URL

### First Week
- [ ] Monitor analytics daily
- [ ] Check form submissions
- [ ] Review error logs
- [ ] Collect user feedback
- [ ] Fix any critical issues immediately

### First Month
- [ ] Review performance metrics
- [ ] Analyze user behavior
- [ ] Optimize based on data
- [ ] Plan next improvements
- [ ] Update content as needed

---

## 🔍 Validation Tools

Use these tools to validate your deployment:

### Performance
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- [GTmetrix](https://gtmetrix.com/)
- [WebPageTest](https://www.webpagetest.org/)

### SEO
- [Google Search Console](https://search.google.com/search-console)
- [Bing Webmaster Tools](https://www.bing.com/webmasters)

### Accessibility
- [WAVE](https://wave.webaim.org/)
- [aXe DevTools](https://www.deque.com/axe/devtools/)

### HTML/CSS
- [W3C HTML Validator](https://validator.w3.org/)
- [W3C CSS Validator](https://jigsaw.w3.org/css-validator/)

### Security
- [Mozilla Observatory](https://observatory.mozilla.org/)
- [Security Headers](https://securityheaders.com/)

### Mobile
- [Google Mobile-Friendly Test](https://search.google.com/test/mobile-friendly)

---

## 🚨 Rollback Plan

If issues occur after deployment:

### GitHub Pages
```bash
git revert HEAD
git push origin main
# Wait 1-2 minutes
```

### Netlify/Vercel
1. Go to Deployments
2. Find previous working version
3. Click "Publish" or "Promote to Production"

### Have Ready
- [ ] Previous working version noted
- [ ] Backup of database/forms (if applicable)
- [ ] Team contact information
- [ ] Hosting platform credentials

---

## ✅ Final Sign-Off

Before going live, get approval from:

- [ ] **Developer**: All features work correctly
- [ ] **Designer**: UI/UX matches specifications
- [ ] **Content Manager**: All text is accurate
- [ ] **Marketing**: Analytics and tracking configured
- [ ] **Business Owner**: Final approval to launch

---

## 📞 Emergency Contacts

Keep these handy for launch day:

- **Developer**: [Name, Phone, Email]
- **Hosting Support**: [Platform support link]
- **Domain Registrar**: [Support contact]
- **Team Lead**: [Name, Phone, Email]

---

## 🎉 Launch Announcement

After successful deployment:

- [ ] Announce on social media
- [ ] Send email to stakeholders
- [ ] Update business cards/materials
- [ ] Add to email signatures
- [ ] Submit to search engines
- [ ] Share with existing customers

---

**Deployment Date**: _______________  
**Deployed By**: _______________  
**Verified By**: _______________  
**Sign-off**: _______________

---

**Version**: 1.0  
**Last Updated**: November 2024  
**Next Review**: Before each deployment
