# Phase 1: Static Content Site Plan
## AI Prompting Learning Platform - Content-First Approach

**Objective**: Create a beautiful, simple static HTML site for content consumption with excellent navigation  
**Timeline**: 1-2 weeks  
**Focus**: Content accessibility, not interactivity  

---

## 🎯 Simplified Goals

### Primary Objectives
- **Content Display**: All 10 modules clearly organized and readable
- **Navigation Excellence**: Intuitive browsing through the learning materials  
- **Visual Design**: Beautiful presentation with Magnus Consulting branding
- **Performance**: Fast loading, lightweight static site
- **Mobile-First**: Responsive design for all devices

### What We're NOT Building (Phase 1)
- ❌ Progress tracking
- ❌ Interactive prompts with copy functionality
- ❌ User accounts or data persistence
- ❌ Bookmarking system
- ❌ Search functionality
- ❌ Notes or personalization
- ❌ Complex state management

---

## 🏗️ Technical Approach

### Technology Stack
- **HTML5**: Semantic markup for content structure
- **CSS3**: Magnus Consulting brand styling + responsive design
- **Minimal JavaScript**: Only for navigation interactions (mobile menu, smooth scrolling)
- **Static Site Generator**: Optional - could use 11ty, Jekyll, or pure HTML
- **Deployment**: Netlify, Vercel, or GitHub Pages

### File Structure
```
ai-prompting-site/
├── index.html                 # Homepage with module overview
├── css/
│   ├── magnus-brand.css      # Brand colors and components
│   ├── layout.css            # Grid, navigation, responsive
│   └── content.css           # Typography, module styling
├── js/
│   └── navigation.js         # Mobile menu, smooth scroll
├── modules/
│   ├── module-1.html         # Foundation Principles
│   ├── module-2.html         # Advanced Techniques
│   ├── module-3.html         # Content Creation
│   ├── ...
│   └── module-10.html        # Future Readiness
├── assets/
│   ├── images/
│   └── icons/
└── README.md
```

---

## 🧭 Navigation Strategy

### Primary Navigation Structure
```
┌─────────────────────────────────────────┐
│  HEADER: Logo + Course Title + Menu     │
├─────────────────────────────────────────┤
│  SIDEBAR: Module Tree (Desktop)         │
│  ┌─ 🟢 BEGINNER                        │
│  ├─── ✓ Module 1: Foundation           │
│  ├─── → Module 2: Advanced Techniques  │
│  ├─── ○ Module 3: Content Creation     │
│  ┌─ 🟡 INTERMEDIATE                    │
│  ├─── ○ Module 4: Research             │
│  └─── ...                              │
└─────────────────────────────────────────┘
```

### Navigation Features
1. **Sticky Header**: Always accessible course overview
2. **Collapsible Sidebar**: Desktop tree view, mobile hamburger
3. **Breadcrumbs**: Current location context
4. **Previous/Next**: Linear progression through modules
5. **Table of Contents**: Within each module for long content
6. **Quick Jump**: Direct links to specific sections

### Mobile Navigation
- **Hamburger Menu**: Full-screen overlay with module tree
- **Bottom Navigation**: Previous/Next for easy thumb access
- **Swipe Gestures**: Optional left/right swipe between modules

---

## 📋 Content Organization

### Homepage Design
```html
<!-- Hero Section -->
<section class="hero bg-magnus-coral">
  <h1>AI Prompting Mastery</h1>
  <p class="magnus-tagline">Transform Your Business with Advanced AI Prompting</p>
  <a href="#modules" class="btn-magnus-primary">Start Learning</a>
</section>

<!-- Module Overview Grid -->
<section class="modules-grid">
  <div class="level-section">
    <h2>🟢 Beginner Level</h2>
    <div class="module-cards">
      <div class="magnus-card level-beginner">
        <h3>Module 1: Foundation Principles</h3>
        <p>45 minutes • 5 sections • 3 prompts</p>
        <a href="modules/module-1.html">Start Module →</a>
      </div>
      <!-- More beginner modules -->
    </div>
  </div>
  <!-- Intermediate & Advanced sections -->
</section>
```

### Module Page Structure
```html
<article class="module-content">
  <header class="module-header">
    <div class="breadcrumbs">Home > Beginner > Module 1</div>
    <h1>Foundation Principles and Frameworks</h1>
    <div class="module-meta">
      <span class="level-badge beginner">Beginner</span>
      <span class="duration">45 minutes</span>
      <span class="sections">5 sections</span>
    </div>
  </header>

  <nav class="table-of-contents">
    <h3>Contents</h3>
    <ol>
      <li><a href="#core-principles">Core Prompting Principles</a></li>
      <li><a href="#clear-framework">CLEAR Framework</a></li>
      <li><a href="#role-based">Role-based Prompting</a></li>
    </ol>
  </nav>

  <main class="module-sections">
    <section id="core-principles">
      <h2>Core Prompting Principles</h2>
      <!-- Content with prompts displayed as code blocks -->
      <div class="prompt-example">
        <h4>🎯 Example: Transform Your Basic Prompts</h4>
        <div class="prompt-before">
          <strong>Bad Prompt:</strong>
          <code>"Write a blog post about AI in business"</code>
        </div>
        <div class="prompt-after">
          <strong>Good Prompt:</strong>
          <pre class="prompt-code">You are a senior technology consultant at Sopra Steria, writing for C-suite executives at mid-size European companies...</pre>
        </div>
      </div>
    </section>
  </main>

  <nav class="module-navigation">
    <a href="index.html" class="nav-prev">← Back to Overview</a>
    <a href="module-2.html" class="nav-next">Next: Advanced Techniques →</a>
  </nav>
</article>
```

---

## 🎨 Visual Design System

### Layout Components
1. **Header**: Magnus logo + course title + responsive menu
2. **Sidebar**: Collapsible module tree with progress indicators
3. **Main Content**: Clean typography with generous whitespace
4. **Prompt Boxes**: Styled code blocks with Magnus coral accents
5. **Navigation**: Clear previous/next with visual hierarchy

### Content Styling
```css
/* Module Cards */
.module-card {
  background: white;
  border: 1px solid var(--magnus-border-gray);
  border-left: 4px solid var(--magnus-coral);
  border-radius: 12px;
  padding: 24px;
  transition: all 0.2s ease;
}

/* Prompt Examples */
.prompt-example {
  background: var(--magnus-coral-pale);
  border-left: 4px solid var(--magnus-coral);
  padding: 20px;
  margin: 24px 0;
  border-radius: 8px;
}

.prompt-code {
  background: white;
  border: 1px solid var(--magnus-coral-light);
  padding: 16px;
  border-radius: 6px;
  font-family: var(--font-mono);
  font-size: 14px;
  line-height: 1.5;
  overflow-x: auto;
}

/* Level Badges */
.level-badge.beginner { 
  background: var(--magnus-success);
  color: white;
}
.level-badge.intermediate { 
  background: var(--magnus-warning);
  color: white;
}
.level-badge.advanced { 
  background: var(--magnus-coral);
  color: white;
}
```

---

## 🚀 Implementation Plan

### Week 1: Foundation & Structure
**Days 1-2: Setup & Content Processing**
- Convert syllabus.md to structured HTML pages
- Create base HTML templates
- Set up CSS with Magnus brand colors
- Build responsive grid system

**Days 3-4: Navigation Implementation**
- Create sidebar navigation component
- Implement mobile hamburger menu
- Add breadcrumbs and table of contents
- Build previous/next navigation

**Day 5: Content Styling**
- Style module pages with typography
- Create prompt example components
- Add level indicators and badges
- Implement responsive design

### Week 2: Polish & Deploy
**Days 6-7: Content Review**
- Review all 10 modules for accuracy
- Ensure consistent formatting
- Add any missing content sections
- Test navigation flows

**Days 8-9: Performance & Testing**
- Optimize images and assets
- Test on multiple devices/browsers
- Ensure fast loading times
- Validate HTML/CSS

**Day 10: Deployment**
- Deploy to static hosting (Netlify/Vercel)
- Set up custom domain if needed
- Final testing on live site
- Documentation and handover

---

## 📊 Success Metrics

### Technical Goals
- **Load Time**: <2 seconds on 3G
- **Accessibility**: WCAG 2.1 AA compliance
- **Mobile**: Perfect responsive design
- **SEO**: Proper meta tags and structure

### User Experience Goals
- **Navigation**: Intuitive module browsing
- **Readability**: Clear typography and spacing
- **Visual Appeal**: Professional Magnus branding
- **Content Access**: Easy prompt example viewing

---

## 🔄 Future Phase Considerations

### Phase 2 Enhancements (Later)
- Add search functionality
- Implement prompt copying
- Create PDF export options
- Add print-friendly styles

### Phase 3 Interactive Features (Much Later)
- Progress tracking
- User accounts
- Bookmarking system
- Interactive exercises

---

This Phase 1 approach gets your content accessible quickly with excellent navigation while maintaining the beautiful Magnus Consulting brand experience. The static approach means faster development, easier maintenance, and better performance - perfect for content consumption! 