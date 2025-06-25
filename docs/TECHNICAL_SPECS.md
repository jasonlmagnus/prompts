# Technical Specifications

## AI Prompting Learning Platform

**Version**: 1.0  
**Last Updated**: December 2024

---

## 🏗️ Architecture Overview

### System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Client Browser                        │
├─────────────────────────────────────────────────────────┤
│                React Application                         │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐    │
│  │   Pages     │ │ Components  │ │     Hooks       │    │
│  │             │ │             │ │                 │    │
│  │ • Home      │ │ • Layout    │ │ • useProgress   │    │
│  │ • Module    │ │ • Content   │ │ • useBookmarks  │    │
│  │ • Lesson    │ │ • Navigation│ │ • useLocalStore │    │
│  └─────────────┘ └─────────────┘ └─────────────────┘    │
├─────────────────────────────────────────────────────────┤
│                  State Management                        │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐    │
│  │   Context   │ │    Hooks    │ │  Local Storage  │    │
│  │             │ │             │ │                 │    │
│  │ • Progress  │ │ • Custom    │ │ • Persistence   │    │
│  │ • Theme     │ │ • Utilities │ │ • User Data     │    │
│  │ • Content   │ │ • State     │ │ • Preferences   │    │
│  └─────────────┘ └─────────────┘ └─────────────────┘    │
├─────────────────────────────────────────────────────────┤
│                    Static Assets                         │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐    │
│  │   Content   │ │   Styles    │ │     Images      │    │
│  │             │ │             │ │                 │    │
│  │ • Modules   │ │ • Tailwind  │ │ • Icons         │    │
│  │ • Prompts   │ │ • Custom    │ │ • Graphics      │    │
│  │ • Exercises │ │ • Fonts     │ │ • Assets        │    │
│  └─────────────┘ └─────────────┘ └─────────────────┘    │
└─────────────────────────────────────────────────────────┘
```

### Technology Stack

#### Frontend Framework

- **React 18**: Latest stable version with concurrent features
- **Vite**: Fast build tool and development server
- **JavaScript/JSX**: Primary development language

#### Styling & UI

- **Tailwind CSS 3**: Utility-first CSS framework
- **@tailwindcss/typography**: Enhanced typography styling
- **Lucide React**: Consistent icon library
- **Custom CSS**: Component-specific styling

#### Routing & Navigation

- **React Router v6**: Client-side routing
- **History API**: Browser navigation management
- **Dynamic imports**: Code splitting for routes

#### State Management

- **React Context**: Global state management
- **Custom Hooks**: Reusable state logic
- **localStorage**: Client-side data persistence
- **Session Storage**: Temporary data storage

#### Content Processing

- **react-markdown**: Markdown rendering
- **Custom parsers**: Content structure processing
- **JSON data**: Structured content storage

---

## 📁 Project Structure

```
ai-prompting-platform/
├── public/
│   ├── favicon.ico
│   ├── manifest.json
│   └── robots.txt
├── src/
│   ├── components/
│   │   ├── common/
│   │   │   ├── Header.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── ProgressBar.jsx
│   │   │   ├── CopyButton.jsx
│   │   │   ├── SearchBox.jsx
│   │   │   └── ThemeToggle.jsx
│   │   ├── content/
│   │   │   ├── ModuleCard.jsx
│   │   │   ├── LessonContent.jsx
│   │   │   ├── PromptBox.jsx
│   │   │   ├── ExerciseBox.jsx
│   │   │   ├── TableOfContents.jsx
│   │   │   └── ContentRenderer.jsx
│   │   ├── layout/
│   │   │   ├── Layout.jsx
│   │   │   ├── ContentLayout.jsx
│   │   │   ├── Breadcrumbs.jsx
│   │   │   └── Navigation.jsx
│   │   └── ui/
│   │       ├── Button.jsx
│   │       ├── Input.jsx
│   │       ├── Modal.jsx
│   │       ├── Tooltip.jsx
│   │       └── LoadingSpinner.jsx
│   ├── data/
│   │   ├── modules.js
│   │   ├── prompts.js
│   │   ├── exercises.js
│   │   └── config.js
│   ├── hooks/
│   │   ├── useProgress.js
│   │   ├── useBookmarks.js
│   │   ├── useLocalStorage.js
│   │   ├── useSearch.js
│   │   ├── useTheme.js
│   │   └── useClipboard.js
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── ModuleView.jsx
│   │   ├── LessonView.jsx
│   │   ├── SearchResults.jsx
│   │   └── NotFound.jsx
│   ├── contexts/
│   │   ├── ProgressContext.js
│   │   ├── ThemeContext.js
│   │   └── ContentContext.js
│   ├── styles/
│   │   ├── globals.css
│   │   ├── components.css
│   │   └── utilities.css
│   ├── utils/
│   │   ├── contentParser.js
│   │   ├── progressTracker.js
│   │   ├── searchEngine.js
│   │   ├── storageManager.js
│   │   └── constants.js
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── docs/
│   ├── README.md
│   ├── PRD.md
│   ├── DESIGN_SYSTEM.md
│   ├── IMPLEMENTATION_PLAN.md
│   └── TECHNICAL_SPECS.md
├── package.json
├── vite.config.js
├── tailwind.config.js
├── eslint.config.js
└── .gitignore
```

---

## 🔧 Component Specifications

### Core Components

#### Layout Components

##### Header Component

```jsx
// Header.jsx
import { useState } from "react";
import { Search, Menu, User } from "lucide-react";
import { useProgress } from "../hooks/useProgress";

const Header = ({ onMenuToggle, sidebarOpen }) => {
  const { overallProgress } = useProgress();

  return (
    <header className="sticky top-0 z-50 bg-white shadow-sm border-b border-gray-200">
      <div className="flex items-center justify-between px-4 h-16">
        <div className="flex items-center space-x-4">
          <button
            onClick={onMenuToggle}
            className="lg:hidden p-2 rounded-md hover:bg-gray-100"
          >
            <Menu className="w-5 h-5" />
          </button>
          <div className="flex items-center space-x-3">
            <img src="/logo.svg" alt="Magnus Consulting" className="h-8" />
            <h1 className="text-xl font-semibold text-gray-900">
              AI Prompting Mastery
            </h1>
          </div>
        </div>

        <div className="flex items-center space-x-4">
          <SearchBox />
          <ProgressIndicator progress={overallProgress} />
          <UserMenu />
        </div>
      </div>
    </header>
  );
};

export default Header;
```

##### Sidebar Component

```jsx
// Sidebar.jsx
import { useState } from "react";
import { ChevronDown, ChevronRight, BookOpen, Target } from "lucide-react";
import { useProgress } from "../hooks/useProgress";
import { modules } from "../data/modules";

const Sidebar = ({ isOpen, onClose }) => {
  const [expandedModules, setExpandedModules] = useState(new Set());
  const { moduleProgress } = useProgress();

  const toggleModule = (moduleId) => {
    const newExpanded = new Set(expandedModules);
    if (newExpanded.has(moduleId)) {
      newExpanded.delete(moduleId);
    } else {
      newExpanded.add(moduleId);
    }
    setExpandedModules(newExpanded);
  };

  return (
    <aside
      className={`
      fixed lg:static inset-y-0 left-0 z-40 w-80 bg-gray-50 border-r border-gray-200
      transform transition-transform duration-300 ease-in-out
      ${isOpen ? "translate-x-0" : "-translate-x-full lg:translate-x-0"}
    `}
    >
      <div className="flex flex-col h-full">
        <div className="p-4 border-b border-gray-200">
          <h2 className="text-lg font-semibold text-gray-900">
            Course Content
          </h2>
        </div>

        <nav className="flex-1 overflow-y-auto p-4">
          <ModuleTree
            modules={modules}
            expandedModules={expandedModules}
            onToggleModule={toggleModule}
            moduleProgress={moduleProgress}
          />
        </nav>

        <div className="p-4 border-t border-gray-200">
          <QuickActions />
        </div>
      </div>
    </aside>
  );
};

export default Sidebar;
```

#### Content Components

##### PromptBox Component

```jsx
// PromptBox.jsx
import { useState } from "react";
import { Copy, Check, Bookmark, Star } from "lucide-react";
import { useClipboard } from "../hooks/useClipboard";
import { useBookmarks } from "../hooks/useBookmarks";

const PromptBox = ({
  id,
  title,
  content,
  category = "try-this",
  customizable = false,
}) => {
  const [isExpanded, setIsExpanded] = useState(false);
  const [customContent, setCustomContent] = useState(content);
  const { copyToClipboard, isCopied } = useClipboard();
  const { isBookmarked, toggleBookmark } = useBookmarks();

  const handleCopy = () => {
    copyToClipboard(customizable ? customContent : content);
  };

  const getCategoryIcon = () => {
    switch (category) {
      case "try-this":
        return <Target className="w-4 h-4" />;
      case "exercise":
        return <BookOpen className="w-4 h-4" />;
      case "challenge":
        return <Star className="w-4 h-4" />;
      default:
        return <Target className="w-4 h-4" />;
    }
  };

  return (
    <div className="prompt-box bg-orange-50 border border-orange-200 border-l-4 border-l-orange-500 rounded-lg p-5 my-4">
      <div className="flex items-center justify-between mb-3">
        <div className="flex items-center space-x-2">
          {getCategoryIcon()}
          <h3 className="font-semibold text-gray-900">{title}</h3>
        </div>
        <div className="flex items-center space-x-2">
          <button
            onClick={() => toggleBookmark(id)}
            className={`p-1 rounded ${
              isBookmarked(id) ? "text-orange-500" : "text-gray-400"
            } hover:text-orange-500`}
          >
            <Bookmark className="w-4 h-4" />
          </button>
          <button
            onClick={handleCopy}
            className="flex items-center space-x-1 px-3 py-1 bg-orange-500 text-white rounded-md hover:bg-orange-600 transition-colors"
          >
            {isCopied ? (
              <Check className="w-4 h-4" />
            ) : (
              <Copy className="w-4 h-4" />
            )}
            <span className="text-sm font-medium">
              {isCopied ? "Copied!" : "Copy"}
            </span>
          </button>
        </div>
      </div>

      {customizable ? (
        <textarea
          value={customContent}
          onChange={(e) => setCustomContent(e.target.value)}
          className="w-full h-32 p-3 font-mono text-sm bg-white border border-gray-200 rounded-md resize-none focus:ring-2 focus:ring-orange-500 focus:border-transparent"
        />
      ) : (
        <pre className="whitespace-pre-wrap font-mono text-sm text-gray-700 leading-relaxed">
          {content}
        </pre>
      )}

      {content.length > 300 && (
        <button
          onClick={() => setIsExpanded(!isExpanded)}
          className="mt-2 text-sm text-orange-600 hover:text-orange-700"
        >
          {isExpanded ? "Show Less" : "Show More"}
        </button>
      )}
    </div>
  );
};

export default PromptBox;
```

---

## 🗄️ Data Structure

### Content Data Model

#### Module Structure

```javascript
// modules.js
export const modules = [
  {
    id: "module-1",
    title: "Foundation Principles and Frameworks",
    slug: "foundation-principles",
    level: "beginner", // beginner | intermediate | advanced
    estimatedTime: 45, // minutes
    description: "Core prompting principles that transform results",
    learningObjectives: [
      "Understand the fundamental principles of effective prompting",
      "Master the CLEAR framework for systematic improvement",
      "Learn role-based prompting for expertise simulation",
    ],
    sections: [
      {
        id: "section-1-1",
        title: "Core prompting principles that transform results",
        slug: "core-principles",
        content: "...", // Markdown content
        estimatedTime: 15,
        prompts: [
          {
            id: "prompt-1-1-1",
            title: "Transform Your Basic Prompts",
            category: "try-this",
            content: "...",
            customizable: true,
            tags: ["basic", "improvement", "sopra-steria"],
          },
        ],
      },
    ],
    prerequisites: [],
    nextModules: ["module-2"],
    resources: [
      {
        title: "Additional Reading",
        url: "https://example.com",
        type: "external",
      },
    ],
  },
];
```

#### Progress Data Model

```javascript
// Progress tracking structure
const progressSchema = {
  userId: "local-user", // For future multi-user support
  overallProgress: 0, // 0-100 percentage
  modules: {
    "module-1": {
      id: "module-1",
      progress: 60, // 0-100 percentage
      completedSections: ["section-1-1", "section-1-2"],
      startedAt: "2024-01-01T10:00:00Z",
      lastAccessedAt: "2024-01-02T15:30:00Z",
      timeSpent: 2700, // seconds
      sections: {
        "section-1-1": {
          id: "section-1-1",
          completed: true,
          completedAt: "2024-01-01T10:45:00Z",
          timeSpent: 1800,
          promptsUsed: ["prompt-1-1-1"],
        },
      },
    },
  },
  bookmarks: [
    {
      id: "bookmark-1",
      type: "section", // section | prompt | exercise
      targetId: "section-1-1",
      title: "Core prompting principles",
      createdAt: "2024-01-01T11:00:00Z",
    },
  ],
  notes: [
    {
      id: "note-1",
      targetId: "section-1-1",
      content: "Important: Remember to be specific...",
      createdAt: "2024-01-01T11:15:00Z",
      updatedAt: "2024-01-01T11:15:00Z",
    },
  ],
  preferences: {
    theme: "light", // light | dark
    fontSize: "medium", // small | medium | large
    sidebarCollapsed: false,
    completedOnboarding: true,
  },
};
```

### Configuration

#### App Configuration

```javascript
// config.js
export const config = {
  app: {
    name: "AI Prompting Learning Platform",
    version: "1.0.0",
    description: "Master AI prompting with Magnus Consulting",
    author: "Magnus Consulting",
  },

  features: {
    search: true,
    bookmarks: true,
    notes: true,
    darkMode: true,
    analytics: false, // Privacy-first approach
    offline: false, // Future feature
  },

  ui: {
    sidebarWidth: 320,
    headerHeight: 64,
    maxContentWidth: 1200,
    animationDuration: 200,
  },

  storage: {
    prefix: "ai-prompting-",
    version: "1.0",
    keys: {
      progress: "progress",
      bookmarks: "bookmarks",
      notes: "notes",
      preferences: "preferences",
    },
  },

  performance: {
    lazyLoadThreshold: 100, // pixels
    debounceDelay: 300, // milliseconds
    cacheExpiry: 86400000, // 24 hours in milliseconds
  },
};
```

---

## 🔌 Custom Hooks

### Progress Management Hook

```javascript
// useProgress.js
import { useState, useEffect, useContext } from "react";
import { ProgressContext } from "../contexts/ProgressContext";
import { storageManager } from "../utils/storageManager";

export const useProgress = () => {
  const context = useContext(ProgressContext);

  if (!context) {
    throw new Error("useProgress must be used within ProgressProvider");
  }

  const {
    progress,
    setProgress,
    markSectionComplete,
    markSectionIncomplete,
    updateTimeSpent,
    getModuleProgress,
    getOverallProgress,
  } = context;

  const markComplete = (sectionId) => {
    markSectionComplete(sectionId);
    storageManager.saveProgress(progress);
  };

  const trackTimeSpent = (sectionId, timeSpent) => {
    updateTimeSpent(sectionId, timeSpent);
    storageManager.saveProgress(progress);
  };

  return {
    progress,
    markComplete,
    markSectionIncomplete,
    trackTimeSpent,
    getModuleProgress,
    getOverallProgress: getOverallProgress(),
    moduleProgress: progress.modules,
    overallProgress: getOverallProgress(),
  };
};
```

### Clipboard Management Hook

```javascript
// useClipboard.js
import { useState, useCallback } from "react";

export const useClipboard = () => {
  const [isCopied, setIsCopied] = useState(false);
  const [error, setError] = useState(null);

  const copyToClipboard = useCallback(async (text) => {
    try {
      if (navigator.clipboard && window.isSecureContext) {
        await navigator.clipboard.writeText(text);
      } else {
        // Fallback for older browsers
        const textArea = document.createElement("textarea");
        textArea.value = text;
        textArea.style.position = "fixed";
        textArea.style.left = "-999999px";
        textArea.style.top = "-999999px";
        document.body.appendChild(textArea);
        textArea.focus();
        textArea.select();
        document.execCommand("copy");
        textArea.remove();
      }

      setIsCopied(true);
      setError(null);

      // Reset copied state after 2 seconds
      setTimeout(() => setIsCopied(false), 2000);
    } catch (err) {
      setError(err.message);
      setIsCopied(false);
    }
  }, []);

  return { copyToClipboard, isCopied, error };
};
```

### Local Storage Hook

```javascript
// useLocalStorage.js
import { useState, useEffect } from "react";
import { config } from "../data/config";

export const useLocalStorage = (key, initialValue) => {
  const prefixedKey = `${config.storage.prefix}${key}`;

  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(prefixedKey);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.warn(`Error reading localStorage key "${prefixedKey}":`, error);
      return initialValue;
    }
  });

  const setValue = (value) => {
    try {
      const valueToStore =
        value instanceof Function ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(prefixedKey, JSON.stringify(valueToStore));
    } catch (error) {
      console.warn(`Error setting localStorage key "${prefixedKey}":`, error);
    }
  };

  const removeValue = () => {
    try {
      setStoredValue(initialValue);
      window.localStorage.removeItem(prefixedKey);
    } catch (error) {
      console.warn(`Error removing localStorage key "${prefixedKey}":`, error);
    }
  };

  return [storedValue, setValue, removeValue];
};
```

---

## 🎨 Styling Architecture

### Tailwind Configuration

```javascript
// tailwind.config.js
module.exports = {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        primary: {
          50: "#FFF7ED",
          100: "#FFEDD5",
          200: "#FED7AA",
          300: "#FDBA74",
          400: "#FB923C",
          500: "#E55A2B", // Magnus primary orange
          600: "#D14A1F",
          700: "#C2410C",
          800: "#9A3412",
          900: "#7C2D12",
        },
        blue: {
          900: "#1E3A8A", // Magnus dark blue
        },
        gray: {
          50: "#F8F9FA",
          100: "#F3F4F6",
          200: "#E5E7EB",
          300: "#D1D5DB",
          400: "#9CA3AF",
          500: "#6B7280",
          600: "#4B5563",
          700: "#374151",
          800: "#1F2937",
          900: "#111827",
        },
      },
      fontFamily: {
        sans: ["Inter", "system-ui", "sans-serif"],
        mono: ["Fira Code", "Monaco", "Consolas", "monospace"],
      },
      fontSize: {
        "2xs": "0.625rem",
      },
      spacing: {
        18: "4.5rem",
        88: "22rem",
      },
      maxWidth: {
        "8xl": "88rem",
      },
      animation: {
        "fade-in": "fadeIn 0.3s ease-out",
        "slide-in": "slideIn 0.3s ease-out",
        "pulse-soft": "pulseSoft 2s infinite",
      },
      keyframes: {
        fadeIn: {
          "0%": { opacity: "0", transform: "translateY(10px)" },
          "100%": { opacity: "1", transform: "translateY(0)" },
        },
        slideIn: {
          "0%": { transform: "translateX(-100%)" },
          "100%": { transform: "translateX(0)" },
        },
        pulseSoft: {
          "0%, 100%": { opacity: "1" },
          "50%": { opacity: "0.7" },
        },
      },
    },
  },
  plugins: [require("@tailwindcss/typography"), require("@tailwindcss/forms")],
};
```

### Custom CSS Classes

```css
/* globals.css */
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";

@layer base {
  html {
    scroll-behavior: smooth;
  }

  body {
    @apply font-sans antialiased;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    @apply font-semibold text-gray-900;
  }
}

@layer components {
  .btn-primary {
    @apply bg-primary-500 text-white px-4 py-2 rounded-lg font-medium hover:bg-primary-600 focus:ring-2 focus:ring-primary-500 focus:ring-offset-2 transition-colors;
  }

  .btn-secondary {
    @apply bg-transparent text-primary-500 border-2 border-primary-500 px-4 py-2 rounded-lg font-medium hover:bg-primary-500 hover:text-white focus:ring-2 focus:ring-primary-500 focus:ring-offset-2 transition-colors;
  }

  .prompt-box {
    @apply bg-primary-50 border border-primary-200 border-l-4 border-l-primary-500 rounded-lg p-5 my-4;
  }

  .module-card {
    @apply bg-white border border-gray-200 rounded-xl p-6 shadow-sm hover:shadow-md transition-shadow cursor-pointer;
  }

  .sidebar-nav-item {
    @apply flex items-center px-3 py-2 text-sm font-medium rounded-md hover:bg-gray-100 transition-colors;
  }

  .sidebar-nav-item.active {
    @apply bg-primary-100 text-primary-700;
  }
}

@layer utilities {
  .text-balance {
    text-wrap: balance;
  }

  .scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }

  .scrollbar-hide::-webkit-scrollbar {
    display: none;
  }
}
```

---

## 🚀 Build & Deployment

### Vite Configuration

```javascript
// vite.config.js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { resolve } from "path";

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": resolve(__dirname, "src"),
      "@components": resolve(__dirname, "src/components"),
      "@hooks": resolve(__dirname, "src/hooks"),
      "@utils": resolve(__dirname, "src/utils"),
      "@data": resolve(__dirname, "src/data"),
    },
  },
  build: {
    outDir: "dist",
    sourcemap: true,
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ["react", "react-dom"],
          router: ["react-router-dom"],
          markdown: ["react-markdown"],
          icons: ["lucide-react"],
        },
      },
    },
  },
  server: {
    port: 3000,
    open: true,
  },
  preview: {
    port: 4173,
  },
});
```

### Package.json Scripts

```json
{
  "name": "ai-prompting-platform",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "lint": "eslint src --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "lint:fix": "eslint src --ext js,jsx --fix",
    "format": "prettier --write \"src/**/*.{js,jsx,css,md}\"",
    "test": "vitest",
    "test:coverage": "vitest --coverage",
    "analyze": "npm run build && npx vite-bundle-analyzer dist/stats.html"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.8.0",
    "react-markdown": "^8.0.5",
    "lucide-react": "^0.263.1",
    "@headlessui/react": "^1.7.13"
  },
  "devDependencies": {
    "@types/react": "^18.0.28",
    "@types/react-dom": "^18.0.11",
    "@vitejs/plugin-react": "^3.1.0",
    "vite": "^4.1.0",
    "tailwindcss": "^3.2.7",
    "@tailwindcss/typography": "^0.5.9",
    "@tailwindcss/forms": "^0.5.3",
    "autoprefixer": "^10.4.14",
    "postcss": "^8.4.21",
    "eslint": "^8.35.0",
    "eslint-plugin-react": "^7.32.2",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.3.4",
    "prettier": "^2.8.4",
    "vitest": "^0.28.5"
  }
}
```

---

## 🔒 Security Considerations

### Content Security Policy

```html
<!-- CSP Header -->
<meta
  http-equiv="Content-Security-Policy"
  content="default-src 'self'; 
               script-src 'self' 'unsafe-inline'; 
               style-src 'self' 'unsafe-inline'; 
               img-src 'self' data: https:; 
               font-src 'self' https://fonts.gstatic.com;"
/>
```

### Data Privacy

- **No External Data Collection**: All user data stored locally
- **No Tracking**: Privacy-first approach
- **No Cookies**: Using localStorage only
- **No Analytics**: Unless explicitly configured

### XSS Prevention

- **Content Sanitization**: All user inputs sanitized
- **React's Built-in Protection**: JSX prevents XSS by default
- **Markdown Sanitization**: react-markdown with safe defaults
- **No dangerouslySetInnerHTML**: Avoided throughout application

---

## 📊 Performance Specifications

### Performance Targets

- **First Contentful Paint**: <1.5 seconds
- **Largest Contentful Paint**: <2.5 seconds
- **Time to Interactive**: <3.0 seconds
- **Cumulative Layout Shift**: <0.1
- **First Input Delay**: <100ms

### Optimization Strategies

- **Code Splitting**: Route-based and component-based
- **Lazy Loading**: Images and non-critical components
- **Bundle Optimization**: Tree shaking and minification
- **Caching**: Browser caching and service worker (future)
- **Asset Optimization**: Compressed images and fonts

---

This technical specification provides the complete technical foundation for building the AI Prompting Learning Platform with React, ensuring scalability, maintainability, and optimal performance.
