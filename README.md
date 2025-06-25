# AI Prompting Learning Platform

A beautiful, simple React website for displaying the "Mastering AI Prompting" learning materials with intuitive navigation, interactive prompts, and Magnus Consulting branding.

## 🎯 Project Overview

### Purpose

Transform the comprehensive AI Prompting syllabus into an engaging, interactive learning platform that helps business professionals master AI prompting skills through structured modules, practical exercises, and easy-to-copy prompts.

### Target Users

- Business professionals learning AI prompting
- Teams with moderate AI experience (2.9/5) but high interest (3.0/5)
- Consultants and knowledge workers seeking practical AI skills

### Key Features

- **10 Learning Modules** with progressive difficulty levels
- **25+ Interactive Prompts** with one-click copying
- **Workshop Exercises** and personal challenges
- **Progress Tracking** with completion indicators
- **Responsive Design** for all devices
- **Magnus Consulting Branding** throughout

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- npm or yarn package manager

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd ai-prompting-platform

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

### Development Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
npm run test         # Run tests
```

## 📁 Project Structure

```
src/
├── components/           # Reusable UI components
│   ├── common/          # Shared components
│   │   ├── Header.jsx
│   │   ├── Sidebar.jsx
│   │   ├── ProgressBar.jsx
│   │   └── CopyButton.jsx
│   ├── content/         # Content-specific components
│   │   ├── ModuleCard.jsx
│   │   ├── LessonContent.jsx
│   │   ├── PromptBox.jsx
│   │   └── ExerciseBox.jsx
│   └── layout/          # Layout components
│       ├── Layout.jsx
│       └── ContentLayout.jsx
├── data/                # Content and configuration
│   ├── modules.js       # Structured learning content
│   ├── prompts.js       # All prompts organized
│   └── config.js        # App configuration
├── hooks/               # Custom React hooks
│   ├── useProgress.js   # Progress tracking
│   ├── useBookmarks.js  # Bookmark management
│   └── useLocalStorage.js # Local storage utilities
├── pages/               # Main application pages
│   ├── Home.jsx         # Landing page
│   ├── ModuleView.jsx   # Module overview
│   └── LessonView.jsx   # Individual lesson
├── styles/              # Global styles
│   └── globals.css      # Tailwind and custom styles
└── utils/               # Utility functions
    ├── contentParser.js # Content processing
    └── progressTracker.js # Progress utilities
```

## 🎨 Design System

### Brand Colors (Magnus Consulting)

- **Primary Orange**: `#E55A2B`
- **Secondary Orange**: `#F4A460`
- **Dark Blue**: `#1E3A8A`
- **Light Gray**: `#F8F9FA`
- **Medium Gray**: `#6B7280`
- **Dark Gray**: `#1F2937`
- **Success Green**: `#10B981`

### Typography

- **Headings**: Inter font family, bold weights
- **Body**: Inter font family, regular/medium weights
- **Code/Prompts**: Fira Code monospace

## 📚 Content Structure

### Learning Levels

- **🟢 Beginner**: Modules 1-3 (Foundation, Techniques, Content Creation)
- **🟡 Intermediate**: Modules 4-7 (Research, Automation, QA, Implementation)
- **🔴 Advanced**: Modules 8-10 (Strategic Applications, Workshops, Future Skills)

### Module Organization

1. **Foundation Principles and Frameworks**
2. **Advanced Techniques and Business Applications**
3. **Content Creation Mastery**
4. **Research and Analysis Excellence**
5. **Business Automation and Workflow Integration**
6. **Common Mistakes and Quality Assurance**
7. **Implementation and Team Development**
8. **Advanced Applications and Future-Ready Skills**
9. **Workshop Exercises and Hands-on Practice**
10. **Continuous Learning and Future Readiness**

## 🛠️ Technology Stack

- **Framework**: React 18 with Vite
- **Styling**: Tailwind CSS
- **State Management**: React Context + localStorage
- **Routing**: React Router v6
- **Icons**: Lucide React
- **Markdown**: react-markdown
- **Build Tool**: Vite
- **Package Manager**: npm

## 📱 Responsive Design

- **Desktop**: 1024px+ (full sidebar, 3-column layout)
- **Tablet**: 768px-1023px (collapsible sidebar, 2-column)
- **Mobile**: <768px (hamburger menu, single column)

## 🎯 Key Features

### Interactive Prompts

- One-click copying to clipboard
- Customizable placeholder text
- Bookmark favorite prompts
- Track usage and completion

### Progress Tracking

- Module completion indicators
- Reading time estimates
- Personal notes and bookmarks
- Achievement system

### Navigation

- Collapsible sidebar with module tree
- Breadcrumb navigation
- Quick search functionality
- Progress indicators

## 🚢 Deployment

### Static Hosting (Recommended)

- **Netlify**: Automatic deployments from Git
- **Vercel**: Optimized for React applications
- **GitHub Pages**: Free hosting for public repositories

### Build Command

```bash
npm run build
```

### Environment Variables

```bash
VITE_APP_TITLE="AI Prompting Learning Platform"
VITE_ANALYTICS_ID="your-analytics-id"
```

## 📈 Success Metrics

### User Experience

- Average session duration >15 minutes
- Module completion rate >70%
- Prompts copied per session >5
- Return rate within 7 days >60%

### Technical Performance

- Initial load time <3 seconds
- Responsive across all devices
- WCAG 2.1 AA compliance
- Modern browser support

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For questions or support, please contact the development team or create an issue in the repository.
