# Design System Documentation

## AI Prompting Learning Platform

**Version**: 1.0  
**Last Updated**: December 2024

---

## 🎨 Brand Identity

### Magnus Consulting Brand Colors

#### Primary Palette

```css
/* Primary Orange - Main brand color */
--primary-orange: #e55a2b;
--primary-orange-hover: #d14a1f;
--primary-orange-light: #f4a460;
--primary-orange-pale: #fff7ed;

/* Secondary Colors */
--dark-blue: #1e3a8a;
--dark-blue-hover: #1e40af;
--success-green: #10b981;
--success-green-hover: #059669;

/* Neutral Palette */
--white: #ffffff;
--light-gray: #f8f9fa;
--medium-gray: #6b7280;
--dark-gray: #1f2937;
--border-gray: #e5e7eb;
```

#### Color Usage Guidelines

- **Primary Orange**: CTAs, active states, progress indicators, accent elements
- **Dark Blue**: Headers, important text, professional elements
- **Success Green**: Completion indicators, positive feedback
- **Light Gray**: Backgrounds, subtle sections
- **Medium Gray**: Secondary text, inactive elements
- **Dark Gray**: Primary text, headings

### Typography

#### Font Families

```css
/* Primary Font - Inter */
--font-family-primary: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
  sans-serif;

/* Code Font - Fira Code */
--font-family-code: "Fira Code", "Monaco", "Consolas", monospace;
```

#### Font Scale

```css
/* Headings */
--text-4xl: 2.25rem; /* 36px - Main page titles */
--text-3xl: 1.875rem; /* 30px - Module titles */
--text-2xl: 1.5rem; /* 24px - Section headings */
--text-xl: 1.25rem; /* 20px - Subsection headings */
--text-lg: 1.125rem; /* 18px - Large body text */

/* Body Text */
--text-base: 1rem; /* 16px - Regular body text */
--text-sm: 0.875rem; /* 14px - Small text, captions */
--text-xs: 0.75rem; /* 12px - Extra small text */

/* Font Weights */
--font-thin: 100;
--font-light: 300;
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
--font-extrabold: 800;
```

#### Typography Usage

- **Headings**: Bold weights (600-700) for clear hierarchy
- **Body Text**: Regular weight (400) for readability
- **Emphasis**: Medium weight (500) for subtle emphasis
- **Code/Prompts**: Monospace font for technical content

---

## 🧩 Component Library

### Layout Components

#### Header Component

```jsx
// Header with navigation and progress
<Header>
  <Logo />
  <Navigation />
  <ProgressIndicator />
  <UserActions />
</Header>
```

**Specifications:**

- Height: 64px
- Background: White with subtle shadow
- Sticky positioning on scroll
- Responsive collapse on mobile

#### Sidebar Navigation

```jsx
// Collapsible sidebar with module tree
<Sidebar collapsed={false}>
  <CourseOverview />
  <ModuleTree />
  <QuickActions />
</Sidebar>
```

**Specifications:**

- Width: 280px desktop, full-width mobile overlay
- Background: Light gray (#F8F9FA)
- Collapsible with smooth animation
- Scrollable content area

#### Main Content Area

```jsx
// Primary content display area
<ContentArea>
  <Breadcrumbs />
  <PageContent />
  <Navigation />
</ContentArea>
```

**Specifications:**

- Responsive padding and margins
- Maximum width: 1200px
- Centered layout with sidebar offset

### Content Components

#### Module Card

```jsx
<ModuleCard
  level="beginner"
  title="Foundation Principles"
  description="Core prompting principles..."
  progress={60}
  estimatedTime={45}
  lessonCount={5}
  promptCount={3}
/>
```

**Visual Specifications:**

```css
.module-card {
  background: white;
  border-radius: 12px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  padding: 24px;
  border-left: 4px solid var(--level-color);
  transition: all 0.2s ease;
}

.module-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transform: translateY(-2px);
}

/* Level indicators */
.level-beginner {
  border-left-color: #10b981;
}
.level-intermediate {
  border-left-color: #f59e0b;
}
.level-advanced {
  border-left-color: #ef4444;
}
```

#### Prompt Box

```jsx
<PromptBox
  title="Transform Your Basic Prompts"
  content="You are a senior technology consultant..."
  category="try-this"
  onCopy={handleCopy}
  onBookmark={handleBookmark}
/>
```

**Visual Specifications:**

```css
.prompt-box {
  background: #fff7ed; /* Light orange tint */
  border: 1px solid #fed7aa;
  border-left: 4px solid #e55a2b;
  border-radius: 8px;
  padding: 20px;
  margin: 16px 0;
  font-family: var(--font-family-code);
  font-size: 14px;
  line-height: 1.6;
}

.prompt-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 12px;
  font-family: var(--font-family-primary);
  font-weight: 600;
  color: #1f2937;
}

.copy-button {
  background: #e55a2b;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 8px 16px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
}

.copy-button:hover {
  background: #d14a1f;
  transform: translateY(-1px);
}
```

#### Progress Bar

```jsx
<ProgressBar value={60} max={100} showPercentage={true} size="large" />
```

**Visual Specifications:**

```css
.progress-bar {
  width: 100%;
  height: 8px;
  background: #e5e7eb;
  border-radius: 4px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #e55a2b 0%, #f4a460 100%);
  border-radius: 4px;
  transition: width 0.3s ease;
}

.progress-large {
  height: 12px;
}
.progress-small {
  height: 4px;
}
```

### Interactive Elements

#### Buttons

```css
/* Primary Button */
.btn-primary {
  background: #e55a2b;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 12px 24px;
  font-weight: 500;
  transition: all 0.2s ease;
  cursor: pointer;
}

.btn-primary:hover {
  background: #d14a1f;
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(229, 90, 43, 0.3);
}

/* Secondary Button */
.btn-secondary {
  background: transparent;
  color: #e55a2b;
  border: 2px solid #e55a2b;
  border-radius: 8px;
  padding: 10px 22px;
  font-weight: 500;
  transition: all 0.2s ease;
  cursor: pointer;
}

.btn-secondary:hover {
  background: #e55a2b;
  color: white;
}

/* Ghost Button */
.btn-ghost {
  background: transparent;
  color: #6b7280;
  border: none;
  padding: 8px 16px;
  font-weight: 400;
  transition: all 0.2s ease;
  cursor: pointer;
}

.btn-ghost:hover {
  color: #1f2937;
  background: #f3f4f6;
}
```

#### Form Elements

```css
/* Input Fields */
.input-field {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 16px;
  transition: all 0.2s ease;
}

.input-field:focus {
  outline: none;
  border-color: #e55a2b;
  box-shadow: 0 0 0 3px rgba(229, 90, 43, 0.1);
}

/* Search Input */
.search-input {
  position: relative;
  display: flex;
  align-items: center;
}

.search-input input {
  padding-left: 40px;
  background: #f9fafb;
  border: 1px solid #e5e7eb;
}

.search-icon {
  position: absolute;
  left: 12px;
  color: #6b7280;
  z-index: 1;
}
```

---

## 📱 Responsive Design

### Breakpoints

```css
/* Mobile First Approach */
--breakpoint-sm: 640px; /* Small tablets */
--breakpoint-md: 768px; /* Tablets */
--breakpoint-lg: 1024px; /* Laptops */
--breakpoint-xl: 1280px; /* Desktops */
--breakpoint-2xl: 1536px; /* Large desktops */
```

### Layout Specifications

#### Desktop (1024px+)

- **Sidebar**: 280px fixed width
- **Content**: Remaining space with max-width 1200px
- **Grid**: 12-column layout
- **Spacing**: 24px base unit

#### Tablet (768px - 1023px)

- **Sidebar**: Collapsible overlay
- **Content**: Full width with padding
- **Grid**: 8-column layout
- **Spacing**: 20px base unit

#### Mobile (<768px)

- **Navigation**: Hamburger menu
- **Content**: Single column
- **Grid**: 4-column layout
- **Spacing**: 16px base unit

### Component Responsive Behavior

#### Module Cards

```css
/* Desktop: 3 columns */
@media (min-width: 1024px) {
  .module-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
  }
}

/* Tablet: 2 columns */
@media (min-width: 768px) and (max-width: 1023px) {
  .module-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
}

/* Mobile: 1 column */
@media (max-width: 767px) {
  .module-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
}
```

---

## 🎭 Animation & Transitions

### Motion Principles

- **Subtle**: Enhance UX without distraction
- **Purposeful**: Guide user attention and feedback
- **Consistent**: Same timing and easing throughout
- **Performance**: 60fps smooth animations

### Transition Specifications

```css
/* Standard transitions */
--transition-fast: 0.15s ease;
--transition-normal: 0.2s ease;
--transition-slow: 0.3s ease;

/* Easing functions */
--ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
--ease-out: cubic-bezier(0, 0, 0.2, 1);
--ease-in: cubic-bezier(0.4, 0, 1, 1);
```

### Common Animations

```css
/* Hover lift effect */
.hover-lift {
  transition: transform var(--transition-normal);
}
.hover-lift:hover {
  transform: translateY(-2px);
}

/* Fade in animation */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 0.3s ease-out;
}

/* Loading spinner */
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.spinner {
  animation: spin 1s linear infinite;
}
```

---

## 🔧 Implementation Guidelines

### CSS Architecture

- **Utility-First**: Tailwind CSS for rapid development
- **Component Classes**: Custom classes for complex components
- **CSS Variables**: For theme customization and consistency
- **BEM Methodology**: For custom component naming

### Accessibility Standards

- **WCAG 2.1 AA Compliance**: Minimum accessibility standard
- **Color Contrast**: 4.5:1 for normal text, 3:1 for large text
- **Focus Indicators**: Visible focus states for all interactive elements
- **Semantic HTML**: Proper heading hierarchy and landmarks
- **Screen Reader Support**: ARIA labels and descriptions

### Performance Considerations

- **Critical CSS**: Inline critical styles for above-the-fold content
- **Font Loading**: Optimize web font loading with font-display: swap
- **Image Optimization**: Responsive images with appropriate formats
- **Animation Performance**: Use transform and opacity for smooth animations

### Browser Support

- **Modern Browsers**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **Graceful Degradation**: Core functionality works without modern features
- **Progressive Enhancement**: Enhanced features for capable browsers

---

## 📋 Design Checklist

### Component Design Review

- [ ] Follows brand color palette
- [ ] Uses consistent typography scale
- [ ] Responsive across all breakpoints
- [ ] Accessible color contrast ratios
- [ ] Proper focus states and interactions
- [ ] Consistent spacing and alignment
- [ ] Smooth transitions and animations
- [ ] Loading and error states defined

### Implementation Review

- [ ] Semantic HTML structure
- [ ] ARIA labels where needed
- [ ] Keyboard navigation support
- [ ] Screen reader compatibility
- [ ] Performance optimized
- [ ] Cross-browser tested
- [ ] Mobile-first responsive design
- [ ] Print styles if applicable

---

This design system ensures consistency, accessibility, and maintainability across the AI Prompting Learning Platform while reflecting the Magnus Consulting brand identity.
