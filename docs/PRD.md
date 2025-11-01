# Product Requirements Document (PRD)
## Business Buddy Website

---

## Document Information

| Field | Value |
|-------|-------|
| **Project Name** | Business Buddy Website |
| **Version** | 1.0.0 |
| **Date** | November 2024 |
| **Status** | Active Development |
| **Owner** | Business Buddy Team |
| **Last Updated** | 2024-11-01 |

---

## 1. Executive Summary

### 1.1 Product Vision
Business Buddy aims to be the trusted growth partner for Thai SMEs, helping them create sustainable New S-Curves for their businesses. The website serves as the primary digital touchpoint for customer acquisition and engagement.

### 1.2 Business Objectives
- Generate qualified leads for consulting services
- Establish brand credibility and authority
- Provide clear value proposition to target audience
- Enable easy booking and consultation scheduling
- Showcase success stories and build trust

### 1.3 Success Metrics
- **Primary KPIs**:
  - Lead form submissions: Target 50+ per month
  - Line Official adds: Target 100+ per month
  - Page engagement rate: > 60%
  - Average session duration: > 2 minutes
  
- **Secondary KPIs**:
  - Bounce rate: < 50%
  - Mobile traffic: > 50%
  - Package inquiry conversion: > 10%

---

## 2. Target Audience

### 2.1 Primary Users
**SME Business Owners (Age 30-55)**
- Industry: Manufacturing, Retail, Services
- Business Stage: Growth or Plateau phase
- Annual Revenue: 10M - 500M THB
- Pain Points:
  - Stagnant growth
  - Need for business transformation
  - Limited resources for strategic planning
  - Uncertainty about market expansion

### 2.2 Secondary Users
**Business Managers/C-Level Executives**
- Seeking strategic partnerships
- Looking for implementation support
- Need validation and case studies
- Require clear ROI justification

### 2.3 User Personas

#### Persona 1: "Growing Grit"
- **Name**: Khun Somchai
- **Age**: 42
- **Role**: CEO of mid-size manufacturing company
- **Goals**: Scale business to next level, explore new markets
- **Frustrations**: Lack of strategic direction, team capacity constraints
- **Tech Savvy**: Medium (uses Line, email, basic web browsing)

#### Persona 2: "Transformation Seeker"
- **Name**: Khun Panida
- **Age**: 38
- **Role**: Managing Director of family retail business
- **Goals**: Modernize business model, implement digital transformation
- **Frustrations**: Traditional methods not working, competition from online retailers
- **Tech Savvy**: High (active on social media, uses business apps)

---

## 3. Functional Requirements

### 3.1 Homepage/Hero Section

#### FR-1.1: Brand Identity Display
- **Priority**: P0 (Critical)
- **Description**: Display Business Buddy logo prominently
- **Acceptance Criteria**:
  - Logo loads within 1 second
  - Logo is visible on all screen sizes
  - Logo is clickable and returns to top of page

#### FR-1.2: Value Proposition
- **Priority**: P0 (Critical)
- **Description**: Clear headline and tagline explaining the service
- **Acceptance Criteria**:
  - Headline visible above fold
  - Thai and English text properly rendered
  - Contrasting colors for readability

#### FR-1.3: Primary CTA Button
- **Priority**: P0 (Critical)
- **Description**: "Book Queue" button for immediate action
- **Acceptance Criteria**:
  - Button stands out visually (pulse animation)
  - Clicking scrolls to contact section
  - Button accessible on mobile and desktop

### 3.2 Navigation

#### FR-2.1: Sticky Navigation Bar
- **Priority**: P0 (Critical)
- **Description**: Fixed navigation that stays visible while scrolling
- **Acceptance Criteria**:
  - Navigation remains at top when scrolling
  - Smooth scroll to sections when clicked
  - Active state for current section
  - Shadow appears after scrolling past hero

#### FR-2.2: Section Links
- **Priority**: P0 (Critical)
- **Description**: Quick links to main sections
- **Sections**: Services, Success, About Us, Contact
- **Acceptance Criteria**:
  - All links work correctly
  - Smooth scrolling animation
  - Mobile-responsive (can add hamburger menu in future)

### 3.3 Carousel Section

#### FR-3.1: Image Carousel
- **Priority**: P1 (High)
- **Description**: Rotating carousel showcasing success stories
- **Acceptance Criteria**:
  - 4 images cycle automatically every 5 seconds
  - Previous/Next buttons for manual control
  - Click indicators show current slide
  - Clicking indicator jumps to that slide
  - Images responsive and optimized
  - Auto-play pauses on user interaction, then resumes

#### FR-3.2: Carousel Controls
- **Priority**: P1 (High)
- **Description**: User controls for carousel navigation
- **Acceptance Criteria**:
  - Previous button goes to previous slide
  - Next button advances to next slide
  - Indicators reflect current position
  - Smooth transitions between slides
  - Keyboard navigation (future enhancement)

### 3.4 Services Section

#### FR-4.1: Service Package Display
- **Priority**: P0 (Critical)
- **Description**: Three-tier service package presentation
- **Packages**: Biz Survive, Biz Scale, Biz Sustain
- **Acceptance Criteria**:
  - Each package clearly differentiated
  - Features listed with checkmarks
  - Pricing placeholders visible
  - "Recommended" badge on Biz Scale
  - Responsive grid layout (3 columns → 1 column on mobile)

#### FR-4.2: Package Selection
- **Priority**: P1 (High)
- **Description**: Interactive selection buttons for each package
- **Acceptance Criteria**:
  - Clicking button shows package name
  - Scrolls user to contact section
  - Visual feedback on hover
  - Mobile tap-friendly button size

### 3.5 Success Stories Section

#### FR-5.1: Case Studies
- **Priority**: P1 (High)
- **Description**: Two featured case study cards
- **Acceptance Criteria**:
  - Company anonymized (A, B, etc.)
  - Results quantified
  - "Read more" link (can expand in future)
  - Cards have hover effects

#### FR-5.2: Testimonial Display
- **Priority**: P1 (High)
- **Description**: Customer testimonial in prominent card
- **Acceptance Criteria**:
  - Quote clearly displayed
  - Customer name and title shown
  - Visual avatar/placeholder
  - Contrasting background for emphasis

### 3.6 About Us Section

#### FR-6.1: Mission Statement
- **Priority**: P1 (High)
- **Description**: Clear communication of company mission
- **Acceptance Criteria**:
  - Mission statement readable and compelling
  - Supporting points with icons
  - Professional layout

#### FR-6.2: Social Media Links
- **Priority**: P2 (Medium)
- **Description**: Links to company social profiles
- **Platforms**: Facebook, Instagram
- **Acceptance Criteria**:
  - Icons clearly visible
  - Links open in new tab
  - Proper security attributes (rel="noopener noreferrer")
  - Hover effects on icons

### 3.7 Contact Section

#### FR-7.1: Lead Capture Form
- **Priority**: P0 (Critical)
- **Description**: E-book download form for lead generation
- **Fields**: Name (required), Email (required), Company (optional)
- **Acceptance Criteria**:
  - Form validation prevents empty submission
  - Required fields marked
  - Email format validation
  - Submit button clearly visible
  - Success message after submission
  - Data sent to Google Sheets (when configured)

#### FR-7.2: Line Official Integration
- **Priority**: P0 (Critical)
- **Description**: QR code for Line Official Account
- **Acceptance Criteria**:
  - QR code image loads correctly (line-qr.jpg)
  - Scannable on mobile devices
  - "Add Line" button provides instruction
  - Contact information displayed (phone, email, hours)

#### FR-7.3: Google Sheets Integration
- **Priority**: P1 (High)
- **Description**: Form submissions automatically saved to Google Sheets
- **Acceptance Criteria**:
  - Form data POST to Google Apps Script Web App
  - Timestamp automatically added
  - No-CORS mode for security
  - Graceful error handling
  - User sees success message regardless of backend status

### 3.8 Footer

#### FR-8.1: Company Information
- **Priority**: P2 (Medium)
- **Description**: Basic company info and legal links
- **Acceptance Criteria**:
  - Copyright notice
  - Privacy Policy link (placeholder)
  - Terms of Service link (placeholder)
  - Consistent styling with brand

---

## 4. Non-Functional Requirements

### 4.1 Performance

#### NFR-1.1: Page Load Time
- **Requirement**: Initial page load < 3 seconds on 4G connection
- **Measurement**: Google PageSpeed Insights score > 80
- **Implementation**: 
  - Optimize images (compress, proper formats)
  - Use CDN for Tailwind CSS
  - Minimize inline scripts

#### NFR-1.2: Image Optimization
- **Requirement**: All images < 1MB each
- **Implementation**:
  - Use JPEG for photos
  - Use PNG for logos with transparency
  - Consider WebP for better compression (future)
  - Lazy loading for below-fold images (future)

### 4.2 Accessibility

#### NFR-2.1: WCAG Compliance
- **Target**: WCAG 2.1 Level AA
- **Requirements**:
  - Proper heading hierarchy (h1 → h2 → h3)
  - Alt text for all images
  - Sufficient color contrast (4.5:1 for text)
  - Keyboard navigation support
  - ARIA labels for interactive elements

#### NFR-2.2: Screen Reader Support
- **Requirement**: All content accessible via screen readers
- **Implementation**:
  - Semantic HTML elements
  - Proper ARIA roles
  - Skip navigation links (future)

### 4.3 Responsiveness

#### NFR-3.1: Mobile Support
- **Requirement**: Fully functional on screens 320px and above
- **Breakpoints**:
  - Mobile: < 768px
  - Tablet: 768px - 1024px
  - Desktop: > 1024px
- **Testing Devices**:
  - iPhone SE (smallest)
  - iPhone 12/13/14
  - iPad
  - Android phones (various)
  - Desktop browsers

#### NFR-3.2: Touch Optimization
- **Requirement**: All interactive elements at least 44x44px
- **Implementation**:
  - Buttons properly sized
  - Adequate spacing between clickable elements
  - Touch-friendly carousel controls

### 4.4 Browser Compatibility

#### NFR-4.1: Supported Browsers
- **Desktop**:
  - Chrome (last 2 versions)
  - Firefox (last 2 versions)
  - Safari (last 2 versions)
  - Edge (last 2 versions)
- **Mobile**:
  - iOS Safari (last 2 versions)
  - Chrome Mobile (last 2 versions)
  - Samsung Internet (last version)

### 4.5 Security

#### NFR-5.1: HTTPS
- **Requirement**: All traffic over HTTPS
- **Implementation**: SSL certificate on hosting

#### NFR-5.2: External Links
- **Requirement**: All external links use rel="noopener noreferrer"
- **Purpose**: Prevent reverse tabnabbing attacks

#### NFR-5.3: Form Security
- **Requirement**: Client-side validation and sanitization
- **Implementation**:
  - HTML5 validation attributes
  - JavaScript validation
  - No sensitive data stored client-side

### 4.6 SEO

#### NFR-6.1: Meta Tags
- **Requirements**:
  - Title tag with keywords
  - Meta description
  - Open Graph tags for social sharing
  - Favicon
  - Proper heading structure

#### NFR-6.2: Semantic HTML
- **Requirement**: Use semantic HTML5 elements
- **Elements**: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`, etc.

---

## 5. Technical Architecture

### 5.1 Technology Stack

#### Frontend
- **HTML5**: Structure and content
- **CSS**: Tailwind CSS v3 (via CDN)
- **JavaScript**: Vanilla JS (ES6+)
- **No build tools**: Direct HTML/CSS/JS

#### Backend
- **Hosting**: Static file hosting (GitHub Pages, Netlify, Vercel)
- **Form Backend**: Google Sheets via Apps Script
- **No server required**: Fully static site

### 5.2 File Structure
```
BizBud/
├── assets/
│   └── images/          # All image assets
│       ├── bizbud-logo.png
│       ├── carousel-1.jpg
│       ├── carousel-2.jpg
│       ├── carousel-3.jpg
│       ├── carousel-4.jpg
│       └── line-qr.jpg
├── docs/                # Documentation
│   ├── PRD.md
│   ├── GOOGLE_SHEETS_SETUP.md
│   └── DEPLOYMENT.md
├── index.html           # Main page
├── README.md            # Project documentation
└── .gitignore          # Git ignore rules
```

### 5.3 Dependencies
- **Tailwind CSS**: https://cdn.tailwindcss.com
- **No npm packages**: Pure static site
- **No build process**: Direct deployment

---

## 6. User Flows

### 6.1 Lead Generation Flow
1. User arrives at website (organic, social, ads)
2. Scrolls through content, learns about services
3. Clicks on lead magnet form in Contact section
4. Fills out name, email, company
5. Submits form
6. Data saved to Google Sheets
7. User sees success message
8. Email automation sends e-book (future implementation)

### 6.2 Quick Booking Flow
1. User clicks "Book Queue" button (nav or hero)
2. Page scrolls to Contact section
3. Line QR code is highlighted
4. User scans QR code with phone
5. Adds Line Official Account
6. Initiates conversation with business
7. Books consultation slot

### 6.3 Package Selection Flow
1. User reads about service packages
2. Clicks "Select Package" button
3. Alert shows selected package
4. Page scrolls to Contact section
5. User can either:
   - Fill lead form, OR
   - Scan Line QR code
6. Contact established

---

## 7. UI/UX Requirements

### 7.1 Design Principles
- **Simplicity**: Clear, uncluttered layouts
- **Consistency**: Uniform spacing, colors, typography
- **Hierarchy**: Clear visual hierarchy guides user attention
- **Feedback**: Visual feedback for all interactions
- **Accessibility**: Inclusive design for all users

### 7.2 Visual Design

#### Color Palette
- **Primary**: #ff914d (Orange) - Energy, growth, action
- **Secondary**: #120e3d (Navy) - Trust, professionalism, stability
- **Neutrals**: Tailwind gray scale
- **Accents**: Green for success states, Line brand color

#### Typography
- **Font**: Inter (fallback: system fonts)
- **Sizes**:
  - H1: 3rem (mobile: 2.5rem)
  - H2: 2.5rem (mobile: 2rem)
  - H3: 1.5rem
  - Body: 1rem
  - Small: 0.875rem

#### Spacing
- **Consistent scale**: 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px
- **Section padding**: py-20 (5rem top/bottom)
- **Container max-width**: 1280px (max-w-7xl)

### 7.3 Animations
- **Hover effects**: Subtle scale or color change
- **Scroll animations**: Fade-in for cards
- **Transitions**: 0.3s ease for most interactions
- **Carousel**: 0.5s ease-in-out slide transition
- **Pulse**: 2s infinite for primary CTA

### 7.4 Responsive Behavior
- **Mobile-first**: Design for mobile, enhance for desktop
- **Breakpoints**: Use Tailwind's responsive prefixes
- **Touch targets**: Minimum 44x44px
- **Font scaling**: Use relative units (rem)
- **Images**: Responsive with max-width: 100%

---

## 8. Content Requirements

### 8.1 Copywriting Tone
- **Professional yet approachable**
- **Thai-first with English support**
- **Action-oriented language**
- **Focus on benefits, not features**
- **Credible and authoritative**

### 8.2 Required Content Sections
- [x] Hero headline and tagline
- [x] Service descriptions (3 packages)
- [x] Case studies (minimum 2)
- [x] Testimonial (minimum 1)
- [x] About us mission
- [x] Contact information
- [x] Legal placeholders

### 8.3 Content Updates
- **Frequency**: Quarterly review
- **Responsibility**: Marketing team
- **Process**: Submit changes via pull request
- **Testing**: Preview on staging before production

---

## 9. Analytics & Tracking

### 9.1 Recommended Tools
- **Google Analytics 4**: User behavior, traffic sources
- **Google Tag Manager**: Easy tag management
- **Facebook Pixel**: Social media tracking and retargeting
- **Hotjar**: Session recordings, heatmaps
- **Google Search Console**: SEO performance

### 9.2 Key Events to Track
- Page views by section
- Button clicks (CTA, packages, social)
- Form submissions
- Form field interactions
- Carousel interactions
- Scroll depth
- Bounce rate by traffic source
- Time on page
- External link clicks

### 9.3 Goals & Conversions
1. **Primary Goal**: Lead form submission
2. **Secondary Goal**: Line QR interaction
3. **Micro-conversions**:
   - Scroll to services
   - Package button click
   - Carousel interaction
   - Social media click

---

## 10. Testing Requirements

### 10.1 Functional Testing
- [ ] All navigation links work
- [ ] Smooth scrolling to sections
- [ ] Carousel auto-play functions
- [ ] Carousel manual controls work
- [ ] All buttons trigger correct actions
- [ ] Form validation works
- [ ] Form submission succeeds
- [ ] Success messages display
- [ ] QR code image loads
- [ ] All images load correctly
- [ ] Social links open in new tabs

### 10.2 Cross-Browser Testing
- [ ] Chrome (Windows, Mac)
- [ ] Firefox (Windows, Mac)
- [ ] Safari (Mac, iOS)
- [ ] Edge (Windows)
- [ ] Chrome Mobile (Android)
- [ ] Samsung Internet

### 10.3 Responsive Testing
- [ ] iPhone SE (320px)
- [ ] iPhone 12/13/14 (390px)
- [ ] iPad (768px)
- [ ] iPad Pro (1024px)
- [ ] Desktop 1920px
- [ ] Desktop 2560px

### 10.4 Performance Testing
- [ ] Google PageSpeed Insights (Mobile & Desktop)
- [ ] GTmetrix score
- [ ] WebPageTest
- [ ] Image optimization check
- [ ] Load time < 3 seconds

### 10.5 Accessibility Testing
- [ ] WAVE accessibility checker
- [ ] Screen reader testing (NVDA, VoiceOver)
- [ ] Keyboard navigation
- [ ] Color contrast checker
- [ ] HTML validation (W3C)

---

## 11. Deployment & Maintenance

### 11.1 Deployment Process
1. Test locally
2. Commit to feature branch
3. Create pull request
4. Code review
5. Merge to main
6. Auto-deploy to production (GitHub Pages/Netlify/Vercel)
7. Verify deployment
8. Monitor analytics

### 11.2 Monitoring
- **Uptime monitoring**: UptimeRobot or similar
- **Error tracking**: Browser console errors
- **Analytics**: Weekly review
- **Form submissions**: Daily check of Google Sheets

### 11.3 Maintenance Schedule
- **Daily**: Check form submissions
- **Weekly**: Review analytics
- **Monthly**: Content updates, image optimization
- **Quarterly**: Major feature updates, A/B testing
- **Annually**: Complete site audit, redesign considerations

---

## 12. Future Enhancements

### Phase 2 (Next 3 months)
- [ ] Blog section for content marketing
- [ ] Email automation for form submissions
- [ ] Calendar integration (Calendly) for direct booking
- [ ] Live chat widget (Tawk.to, Intercom)
- [ ] Multi-language toggle (Thai/English)
- [ ] More case studies and testimonials
- [ ] Video testimonials

### Phase 3 (3-6 months)
- [ ] Customer portal with login
- [ ] Payment integration for package purchases
- [ ] Automated proposal generator
- [ ] Client dashboard
- [ ] Resource library/downloads
- [ ] Webinar registration
- [ ] Newsletter signup

### Phase 4 (6-12 months)
- [ ] Mobile app (iOS/Android)
- [ ] AI chatbot for FAQ
- [ ] Advanced analytics dashboard
- [ ] CRM integration (HubSpot, Salesforce)
- [ ] Marketing automation
- [ ] Partner portal
- [ ] Referral program

---

## 13. Risks & Mitigations

### Risk 1: Low Form Conversion Rate
- **Impact**: High
- **Probability**: Medium
- **Mitigation**: 
  - A/B test form fields
  - Improve lead magnet appeal
  - Add social proof
  - Simplify form (fewer fields)

### Risk 2: Google Sheets API Issues
- **Impact**: Medium
- **Probability**: Low
- **Mitigation**:
  - Graceful error handling
  - User sees success message regardless
  - Backup email notification system
  - Manual form fallback

### Risk 3: Poor Mobile Experience
- **Impact**: High
- **Probability**: Low
- **Mitigation**:
  - Extensive mobile testing
  - Touch-optimized controls
  - Fast image loading
  - Simple navigation

### Risk 4: Carousel Images Too Large
- **Impact**: Medium
- **Probability**: Medium
- **Mitigation**:
  - Compress images before upload
  - Use appropriate formats
  - Implement lazy loading
  - Consider responsive images (srcset)

---

## 14. Success Criteria

### Launch Criteria (Must Have)
- [x] All sections complete and functional
- [x] Carousel working with all 4 images
- [x] QR code replaced with actual image
- [x] All buttons functional
- [x] Google Sheets integration documented
- [x] Responsive on mobile, tablet, desktop
- [x] Cross-browser tested
- [x] Documentation complete

### Post-Launch Success (1 month)
- [ ] 50+ lead form submissions
- [ ] 100+ Line Official adds
- [ ] < 50% bounce rate
- [ ] > 2 min average session duration
- [ ] > 60% mobile traffic
- [ ] Google PageSpeed score > 80

### Long-Term Success (3 months)
- [ ] 200+ total leads
- [ ] 10+ consultation bookings
- [ ] 5+ package sign-ups
- [ ] Featured in search results
- [ ] Social media traffic growing
- [ ] Positive user feedback

---

## 15. Appendix

### A. Glossary
- **S-Curve**: Business growth model showing stages from introduction to maturity
- **New S-Curve**: Creating new growth trajectory when current curve plateaus
- **SME**: Small and Medium-sized Enterprises
- **Lead Magnet**: Free resource offered in exchange for contact information
- **CTA**: Call to Action - button or link encouraging user action
- **QR Code**: Quick Response code for easy mobile scanning

### B. References
- Tailwind CSS Documentation: https://tailwindcss.com/docs
- Google Sheets API: https://developers.google.com/sheets/api
- Web Accessibility Guidelines: https://www.w3.org/WAI/WCAG21/quickref/
- HTML Best Practices: https://developer.mozilla.org/en-US/

### C. Change Log

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| 2024-11-01 | 1.0.0 | Initial PRD creation | Development Team |

---

**Document Owner**: Business Buddy Development Team  
**Review Cycle**: Quarterly  
**Next Review Date**: February 2025
