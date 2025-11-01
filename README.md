# Business Buddy - Website Documentation

## 📋 Project Overview

Business Buddy is a landing page for an SME business consulting service focused on helping Thai SMEs create new growth curves (New S-Curve) that are sustainable for business, people, and society.

## 🎯 Purpose

The website serves as the primary marketing and lead generation platform for Business Buddy, offering:
- Information about consulting services
- Package options for different business stages
- Success stories and testimonials
- Contact forms for lead capture
- Direct booking through Line Official Account

## 🚀 Features

### 1. Hero Section
- Prominent logo display
- Clear value proposition
- Call-to-action button for booking consultations
- Visual representation of partnership model

### 2. Interactive Carousel
- **Location**: Between Hero and Services sections
- **Images**: 4 carousel images showcasing success stories
- **Features**:
  - Auto-play (5-second intervals)
  - Manual navigation with Previous/Next buttons
  - Click indicators for direct slide access
  - Smooth transitions with fade effects
  - Responsive design

### 3. Services Section
Three service tiers:
- **Biz Survive**: Stabilization & Immediate Opportunity (3 months)
- **Biz Scale**: New BU Creation & Market Expansion (6-12 months) - Recommended
- **Biz Sustain**: Long-term Model & Renewable Growth (12+ months)

Each package includes interactive selection buttons.

### 4. Success Stories
- Case studies from previous clients
- Testimonials from satisfied customers
- Quantifiable results

### 5. About Us Section
- Mission statement
- Core values and approach
- Social media integration
- Quick booking option

### 6. Contact Section
Two main components:
- **Lead Magnet Form**: E-book download for "New S-Curve Checklist"
- **Line Official Integration**: QR code for direct Line booking

## 🛠️ Technology Stack

### Frontend
- **HTML5**: Semantic markup
- **Tailwind CSS**: Utility-first CSS framework (via CDN)
- **Vanilla JavaScript**: No framework dependencies

### Assets
- Images stored in `assets/images/`
- Logo: `bizbud-logo.png`
- Carousel: `carousel-1.jpg` through `carousel-4.jpg`
- QR Code: `line-qr.jpg`

## 📁 Project Structure

```
BizBud/
├── assets/
│   └── images/
│       ├── bizbud-logo.png
│       ├── carousel-1.jpg
│       ├── carousel-2.jpg
│       ├── carousel-3.jpg
│       ├── carousel-4.jpg
│       └── line-qr.jpg
├── docs/
│   ├── PRD.md
│   ├── GOOGLE_SHEETS_SETUP.md
│   └── DEPLOYMENT.md
├── index.html
├── .gitignore
└── README.md
```

## 🎨 Design System

### Colors
- **Primary Orange**: `#ff914d` (biz-orange)
- **Navy Blue**: `#120e3d` (biz-navy)
- **White**: `#ffffff`
- **Gray Scale**: Tailwind default grays

### Typography
- **Font Family**: Inter, -apple-system, BlinkMacSystemFont, sans-serif
- **Headings**: Bold, varying sizes
- **Body**: Regular weight, size adjusts for readability

### Components
- Rounded corners (rounded-2xl, rounded-full)
- Card hover effects with elevation
- Smooth transitions and animations
- Responsive grid layouts

## 🔧 Setup & Installation

### Local Development

1. Clone the repository:
```bash
git clone https://github.com/Putthipat-L/BizBud.git
cd BizBud
```

2. Open the project:
```bash
# Simply open index.html in your browser
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

Or use a local server:
```bash
# Python 3
python -m http.server 8000

# Node.js (with http-server)
npx http-server

# PHP
php -S localhost:8000
```

3. Access the website at `http://localhost:8000`

### No Build Process Required
This is a static website with no build dependencies. All resources are loaded via CDN or included locally.

## 🌐 Deployment

### GitHub Pages
1. Go to repository Settings
2. Navigate to Pages
3. Select source branch (main)
4. Save
5. Website will be available at `https://putthipat-l.github.io/BizBud/`

### Netlify
1. Connect your GitHub repository
2. Set build command: (none)
3. Set publish directory: `/`
4. Deploy

### Vercel
1. Import GitHub repository
2. Framework Preset: Other
3. Build Command: (leave empty)
4. Output Directory: `.`
5. Deploy

## 📊 Google Sheets Integration

The contact form can be integrated with Google Sheets for lead tracking. See [docs/GOOGLE_SHEETS_SETUP.md](docs/GOOGLE_SHEETS_SETUP.md) for detailed setup instructions.

### Quick Setup
1. Create a Google Sheets spreadsheet
2. Create a Google Apps Script Web App
3. Replace `YOUR_GOOGLE_SHEETS_WEB_APP_URL_HERE` in index.html with your Web App URL
4. Test the form submission

## 🎯 Interactive Features

### Button Functionality

1. **Book Queue Buttons**: Scroll to contact section and highlight Line QR code
2. **Package Selection**: Show alert with selected package and scroll to contact
3. **Line Official Button**: Show instruction to scan QR code
4. **Lead Form**: Submit data to Google Sheets (when configured)

### Carousel Controls

- **Auto-play**: Advances every 5 seconds
- **Previous/Next Buttons**: Manual navigation
- **Indicators**: Click to jump to specific slide
- **Keyboard**: Can be enhanced with arrow key support

## 🧪 Testing

### Manual Testing Checklist

- [ ] All navigation links scroll smoothly to sections
- [ ] Carousel auto-plays and manual controls work
- [ ] All buttons trigger appropriate actions
- [ ] Form validates required fields
- [ ] Form submits successfully (when Google Sheets is configured)
- [ ] QR code image displays correctly
- [ ] Responsive design works on mobile, tablet, and desktop
- [ ] Hover effects work on interactive elements
- [ ] Social media links open in new tabs

### Browser Compatibility
- Chrome (recommended)
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## 📱 Responsive Design

The website is fully responsive with breakpoints:
- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

Key responsive features:
- Navigation collapses on mobile (hamburger menu can be added)
- Grid layouts adjust column counts
- Font sizes scale appropriately
- Images maintain aspect ratios
- Touch-friendly button sizes

## 🔒 Security Considerations

1. **Form Validation**: Client-side validation prevents empty submissions
2. **External Links**: Use `rel="noopener noreferrer"` for security
3. **HTTPS**: Always deploy with SSL certificate
4. **CORS**: Google Sheets integration uses 'no-cors' mode

## 🚀 Future Enhancements

### Planned Features
- [ ] Multi-language support (Thai/English toggle)
- [ ] Blog section for content marketing
- [ ] Customer portal login
- [ ] Calendar integration for booking
- [ ] Live chat widget
- [ ] Analytics dashboard
- [ ] A/B testing framework
- [ ] Progressive Web App (PWA) capabilities

### Technical Improvements
- [ ] Lazy loading for images
- [ ] Service Worker for offline support
- [ ] Performance optimization
- [ ] SEO enhancements
- [ ] Accessibility improvements (WCAG 2.1 AA)

## 📈 Analytics

### Recommended Tools
- Google Analytics 4
- Facebook Pixel
- LinkedIn Insight Tag
- Hotjar for user behavior

### Key Metrics to Track
- Page views
- Bounce rate
- Form submissions
- Button click rates
- Carousel engagement
- Average session duration
- Traffic sources

## 🤝 Contributing

### Development Workflow
1. Create a feature branch
2. Make changes
3. Test thoroughly
4. Submit pull request
5. Code review
6. Merge to main

### Coding Standards
- Use semantic HTML
- Follow Tailwind CSS conventions
- Comment complex JavaScript logic
- Maintain consistent indentation
- Keep functions small and focused

## 📞 Support & Contact

For questions or issues:
- **Email**: hello@bizbud.co.th
- **Phone**: 02-XXX-XXXX
- **Line Official**: Scan QR code on website
- **GitHub Issues**: Report bugs or request features

## 📄 License

Copyright © 2024 Business Buddy. All rights reserved.

## 🙏 Acknowledgments

- Tailwind CSS for the styling framework
- Font Awesome (if used) for icons
- All contributing developers and designers

---

**Last Updated**: November 2024  
**Version**: 1.0.0  
**Maintained by**: Business Buddy Development Team
