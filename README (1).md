# APEdge - Intelligent Process Automation Platform

> A modern, feature-rich web application for workflow management, document processing, and multi-tenant business process automation.

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Architecture & Project Structure](#-architecture--project-structure)
- [Technology Stack](#-technology-stack)
- [Quick Start Guide](#-quick-start-guide)
- [Configuration](#-configuration)
- [Build & Deployment](#-build--deployment)
- [Component Library](#-component-library)
- [State Management & Data Flow](#-state-management--data-flow)
- [Development Guidelines](#-development-guidelines)
- [Contributing](#-contributing)
- [Troubleshooting](#-troubleshooting)
- [Additional Resources](#-additional-resources)

---

## 🎯 Project Overview

**APEdge** is an enterprise-grade **Business Process Automation** platform designed to streamline workflow management, document processing, and approval chains across multiple tenants and organizational units.

### Core Capabilities

- **Workflow Orchestration** - Visual workflow designer with drag-and-drop interface and JSON-based definitions
- **Document Intelligence** - Automated document ingestion, OCR extraction, validation, and audit trails
- **Multi-Tenant Architecture** - Isolated organizational data with custom branding and role-based access
- **Queue Management** - Process queues, document queues, and approval queues with workload distribution
- **Real-time Analytics** - Interactive dashboards tracking performance, SLA compliance, and operational metrics
- **Role-Based Access Control** - Granular permissions for Users, Admins, and Super Admins

### Key Features

- 🔐 **Multi-Level Authentication** - Login, session management, password recovery, auto-logout on idle
- 👥 **Role-Based UI** - Different interfaces for Users, Admins, and Super Admins
- 📊 **Interactive Dashboards** - Real-time metrics, charts, and process insights
- 📁 **File Upload & Processing** - Drag-and-drop uploads with validation and preview
- 🎨 **Modern UI/UX** - Tailwind CSS, smooth animations, responsive design
- 🔍 **Advanced Filtering** - Powerful search and filter capabilities for data tables
- 📱 **Responsive Design** - Optimized for desktop, tablet, and mobile devices
- 🎭 **Product Tours** - Built-in onboarding and guidance system
- ⚡ **Performance Optimized** - Code splitting, lazy loading, skeleton loaders, Web Workers
- 🛡️ **Security First** - JWT tokens, encrypted storage, CSRF protection

## 🏗️ Architecture & Project Structure

### Complete Directory Structure

```
apedge/
├── src/
│   ├── components/                 # UI components organized by feature
│   │   ├── Admin/                  # Admin-specific features
│   │   │   ├── Masters.jsx
│   │   │   ├── Parameters.jsx
│   │   │   ├── ProcessFieldConfig.jsx
│   │   │   ├── TenantLogoManagement.jsx
│   │   │   └── UserRegistration.jsx
│   │   ├── Auth/                   # Authentication & authorization
│   │   │   ├── ForgetPassword.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── SessionExpired.jsx
│   │   │   └── Unauthorized.jsx
│   │   ├── JsonFlow/               # Workflow & process management
│   │   │   ├── Editor_components/  # Process editor UI
│   │   │   ├── Process/            # Process views
│   │   │   ├── Queues/             # Queue management
│   │   │   ├── Reports/            # Reporting & analytics
│   │   │   └── Processdashboard.jsx
│   │   ├── SuperAdmin/             # Super Admin features
│   │   │   ├── DefaultConfig.jsx
│   │   │   ├── GenericFieldsConfig.jsx
│   │   │   ├── ModuleRegistration.jsx
│   │   │   ├── ProcessRegistration.jsx
│   │   │   └── TenantRegistration.jsx
│   │   ├── Upload/                 # File upload functionality
│   │   ├── View/                   # Document viewing
│   │   ├── common/                 # Reusable UI component library
│   │   │   ├── buttons/            # Button components
│   │   │   ├── forms/              # Form inputs
│   │   │   ├── tables/             # Data tables
│   │   │   ├── popups/             # Modal dialogs
│   │   │   ├── layout/             # Navigation & layout
│   │   │   ├── feedback/           # Status indicators
│   │   │   ├── file-management/    # File & workflow UI
│   │   │   ├── tour/               # Product tours
│   │   │   ├── utilities/          # Utility components
│   │   │   ├── pages/              # Page-level components
│   │   │   └── index.js            # Central exports
│   │   ├── refactored/             # Optimized components
│   │   │   ├── MainLayout.jsx
│   │   │   ├── PrivateRoute.jsx
│   │   │   ├── SkeletonLoader.jsx
│   │   │   ├── SuspenseWrapper.jsx
│   │   │   ├── routes.js
│   │   │   ├── skeletonTypes.js
│   │   │   └── useIdleTimeout.js
│   ├── hooks/                      # Global custom React hooks
│   │   ├── useCardPopup.jsx
│   │   ├── useProcessInsights.js
│   │   ├── useProcessStats.js
│   │   └── useProcessWorkflow.js
│   ├── store/                      # Redux state management
│   │   ├── authSlice.js            # Authentication state
│   │   └── store.js                # Redux store config
│   ├── utils/                      # Utility functions
│   │   ├── validations/            # Web Worker validations
│   │   ├── authInterceptor.js      # Axios interceptors
│   │   ├── cryptoUtils.js          # Encryption utilities
│   │   ├── dateUtils.js            # Date manipulation
│   │   ├── fileUtils.js            # File handling
│   │   ├── secureStorage.js        # Encrypted storage
│   │   └── ...                     # Other utilities
│   ├── data/                       # Static data & schema docs
│   ├── styles/                     # Global stylesheets
│   ├── App.jsx                     # Main app & routing
│   ├── main.jsx                    # Application entry point
│   ├── index.css                   # Entry CSS (Tailwind)
│   └── permissions.js              # RBAC configuration
├── public/                         # Static assets
├── vite.config.js                  # Vite configuration
├── tailwind.config.js              # Tailwind CSS configuration
├── eslint.config.js                # ESLint rules
├── package.json                    # Dependencies & scripts
└── README.md                       # This file
```

### Architectural Design Principles

- **Feature-Based Organization** - Components grouped by feature/domain for scalability
- **Role-Based Separation** - Distinct component trees for Admin/SuperAdmin/User roles
- **Reusable Component Library** - `common/` folder serves as internal design system
- **Centralized State** - Redux for global state, React Query for server state
- **Performance First** - Web Workers, code splitting, lazy loading, memoization

## 🛠️ Technology Stack

| Category | Technology | Purpose |
|----------|-----------|---------|
| **Core** | React 19.1.1, Vite 7.1.6 | UI framework & build tool |
| **State** | Redux Toolkit 2.9.0, TanStack Query 5.90.12 | Global & server state |
| **Routing** | React Router DOM 7.9.1 | Client-side routing |
| **Styling** | Tailwind CSS 3.4.17, Poppins Font | Utility-first CSS |
| **Charts** | Recharts 3.2.1, Chart.js 5.3.0 | Data visualization |
| **Tables** | TanStack Table 8.21.3 | Advanced data tables |
| **Drag & Drop** | dnd-kit 6.3.1 | Drag-and-drop functionality |
| **Documents** | react-pdf 10.1.0, jsPDF 3.0.3, ExcelJS 4.4.0 | PDF & Excel handling |
| **HTTP** | Axios 1.12.2, jwt-decode 4.0.0, Crypto-JS 4.2.0 | API & security |
| **UX** | Reactour 3.8.0, React Toastify 11.0.5 | Tours & notifications |

## 🚀 Quick Start Guide

### Prerequisites

Ensure you have the following installed before starting:

- **Node.js** ≥ 18.x ([Download](https://nodejs.org/))
- **npm** ≥ 9.x (comes with Node.js) or **yarn** ≥ 1.22.x
- **Git** (for version control)

### Installation Steps

#### 1. Clone the Repository

```bash
git clone <repository-url>
cd "apedge new flow v2"
```

#### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

#### 3. Configure API Proxy

Open [`vite.config.js`](./vite.config.js) and set the backend target for your environment:

```javascript
server: {
  proxy: {
    '/api': {
      // Choose ONE target based on your environment:
      
      // Development (local backend)
      target: 'http://localhost:8580',
      
      // Production (uncomment to use)
      // target: 'https://apedge.automationedge.com:8680',
      
      // QA (uncomment to use)
      // target: 'http://31.97.61.83:8580',
      
      changeOrigin: true,
      secure: false,
      rewrite: (path) => path.replace(/^\/api/, ''),
    },
  },
}
```

#### 4. Start Development Server

```bash
npm run dev
# or
yarn dev
```

The application will start on **`http://localhost:8081`** (configured in `vite.config.js`).

#### 5. Access the Application

Open your browser and navigate to `http://localhost:8081`. You should see the login page.

---

### Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build production-ready bundle |

## ⚙️ Configuration

### Vite Configuration ([`vite.config.js`](./vite.config.js))

Vite provides ultra-fast development with hot module replacement (HMR) and optimized production builds.

#### Core Configuration

**Plugins:**
```javascript
plugins: [react()]
```
- **@vitejs/plugin-react**: Enables Fast Refresh using Babel for instant updates without full page reloads

**Development Server:**
```javascript
server: {
  port: 8081,        // Custom dev server port
  hmr: {
    overlay: false   // Disable error overlay
  },
  proxy: { ... }
}
```

### API Proxy Setup

The Vite dev server proxy solves CORS issues during development by forwarding API requests to the backend.

#### How It Works

```javascript
proxy: {
  '/api': {
    target: 'http://localhost:8580',  // Backend server
    changeOrigin: true,
    secure: false,
    rewrite: (path) => path.replace(/^\/api/, ''),
  },
}
```

#### Configuration Breakdown

| Property | Value | Purpose |
|----------|-------|---------|
| **`/api`** | Route prefix | Intercepts all requests starting with `/api` |
| **`target`** | `http://localhost:8580` | Backend API server address |
| **`changeOrigin`** | `true` | Required for virtual hosting |
| **`secure`** | `false` | Allows self-signed HTTPS certificates |
| **`rewrite`** | Removes `/api` prefix | Transforms `/api/users` → `/users` |

#### Environment Targets

Multiple backend targets are available (comment/uncomment as needed):

```javascript
// Local Development
target: 'http://localhost:8580',

// QA Environment
// target: 'http://31.97.61.83:8580',

// Alternative QA
// target: 'http://194.164.150.6:8589',

// Production
// target: 'https://apedge.automationedge.com:8680',
```

#### Request Flow Example

**Frontend Code:**
```javascript
axios.get('/api/users/123')
```

**What Happens:**
1. Browser sends request to: `http://localhost:8081/api/users/123`
2. Vite proxy intercepts `/api/*` requests
3. Rewrites path: `/api/users/123` → `/users/123`
4. Forwards to backend: `http://localhost:8580/users/123`
5. Backend responds with user data
6. Vite returns response to frontend

#### Why Use a Proxy?

✅ **No CORS Issues** - Browser sees requests as same-origin  
✅ **Cleaner Code** - Use relative paths (`/api/...`) instead of full URLs  
✅ **Easy Environment Switching** - Change target URL in one place  
✅ **No Backend Changes** - Backend doesn't need CORS configuration for dev

### Build Optimizations

The configuration includes production build optimizations:

**Code Splitting:**
```javascript
manualChunks: {
  vendor: ['react', 'react-dom', 'react-router-dom'],
  redux: ['@reduxjs/toolkit', 'react-redux'],
  charts: ['chart.js', 'react-chartjs-2'],
  utils: ['axios', 'jwt-decode', 'crypto-js']
}
```

**Asset Optimization:**
- **CSS code splitting** enabled for better caching
- **Hash-based filenames** for cache busting
- **Organized output**: CSS in `/css`, images in `/images`
- **Inline small assets** (< 4KB) for performance
- **Optimized dependencies** pre-bundling

**Build Limits:**
- Chunk size warning limit: 1000 KB
- Assets inline limit: 4096 bytes

## 📦 Build & Deployment

### Production Build

```bash
npm run build
```

**What happens:**
- Minifies JavaScript and CSS
- Splits code into optimized chunks (vendor, redux, charts, utils)
- Adds content hashes for cache busting
- Organizes assets: CSS in `/css`, images in `/images`
- Generates `dist/` folder with production-ready bundle

### Deployment

The `dist/` folder contains all static assets ready for deployment to any static file server (Nginx, Apache, AWS S3, etc.).

### Key Architectural Decisions

**1. Feature-Based Organization**
- Components grouped by feature/domain rather than type
- Easier to locate related components and maintain boundaries
- Scales better as codebase grows

**2. Role-Based Component Separation**
- **Admin/** - Components for admin users
- **SuperAdmin/** - Components for super admin users
- **common/** - Shared components across all roles

**3. Centralized State Management**
- Redux for global state (auth, user preferences)
- React Query for server state (API data, caching)
- Local state for component-specific data

**4. Performance Optimizations**
- Web Workers for heavy validation tasks
- React.memo and useMemo for render optimization
- Code splitting via dynamic imports
- Skeleton loaders for better UX during loading

**5. Security Measures**
- JWT token management via interceptors
- Encrypted storage for sensitive data
- Route guards for protected pages
- Permission-based UI rendering

---

## 🎨 Component Library

### Reusable Components ([`src/components/common/`](./src/components/common/))

The `common/` folder is an **internal design system** with 10 categorized subdirectories containing reusable UI components:

**Categories:**
- **buttons/** - Button components (Button, ActionButton)
- **forms/** - Form inputs (InputOptions, SearchableSelect, DropdownOptions)
- **tables/** - Data tables (TableComponent, AdvancedFilterPanel)
- **popups/** - Modal dialogs (9 variants: CardPopup, ModernPopup, ErrorPopup, etc.)
- **layout/** - Navigation (Navbar, Sidebar, TabComponent)
- **feedback/** - Status indicators (StatusBadge, StatusCard, MessageDisplay)
- **file-management/** - File UI (FileCard, Workflowstepper)
- **tour/** - Onboarding (TourManager, TourProviderWrapper)
- **utilities/** - Helpers (StageDisplay, DefaultDateRangeBadge, AgentStatusDrawer)
- **pages/** - Page components (NotFound, InProcess, UserProfile)

**Import Examples:**
```jsx
// Central import (recommended for multiple components)
import { Button, TableComponent, StatusBadge } from '../common';

// Direct import (better tree-shaking)
import Button from '../common/buttons/Button';
```

**Design Principles:**
- Tailwind CSS utility classes only (no custom CSS)
- Reusable, no business logic
- PropTypes for type checking
- Responsive, mobile-first design
- Accessible markup with ARIA labels

---

## 🔄 State Management & Data Flow

### Global Custom Hooks ([`src/hooks/`](./src/hooks/))

Reusable logic extracted as custom hooks:

- **useCardPopup** - Manage card popup state (open/close, content)
- **useProcessInsights** - Process analytics and insights
- **useProcessStats** - Process statistics and metrics
- **useProcessWorkflow** - Workflow state and actions

**Usage Example:**
```jsx
import { useCardPopup } from '../hooks/useCardPopup';

const MyComponent = () => {
  const { isCardPopupOpen, popupContent, openCardPopup, closeCardPopup } = useCardPopup();
  
  const handleShowPopup = () => {
    openCardPopup('Title', 'Content', true, 'item-123');
  };
  
  return (/* JSX */);
};
```

### Redux Store ([`src/store/`](./src/store/))

- **store.js** - Redux store setup with middleware and reducers
- **authSlice.js** - Authentication state (user, tokens, permissions)

**State Flow:**
```
User Action → Redux Action → Reducer → State Update → Component Re-render
```

### Utility Functions ([`src/utils/`](./src/utils/))

Organized by purpose:

**Security & Auth:**
- **authInterceptor.js** - Axios interceptors for JWT token management
- **cryptoUtils.js** - Encryption/decryption utilities
- **secureStorage.js** - Encrypted local/session storage

**Data Processing:**
- **validations/** - Web Workers for background validation processing
- **dateUtils.js**, **timezoneUtils.js** - Date and timezone operations
- **fileUtils.js** - File validation and upload utilities
- **documentStageSummary.js** - Document workflow stage calculations

**UI Utilities:**
- **Statuscolorutils.js** - Maps status values to colors
- **customValuesParser.jsx** - Parse and format custom values

## 📝 Development Guidelines

### Adding New Features

1. Identify the feature category (Admin, User, common, etc.)
2. Create components in the appropriate folder
3. Use existing common components where possible
4. Add hooks to `hooks/` if logic is reusable
5. Add utilities to `utils/` if general-purpose
6. Update routes in `App.jsx` or `components/refactored/routes.js`

### Naming Conventions

| Type | Convention | Example |
|------|------------|--------|
| **Component files** | PascalCase | `UserProfile.jsx` |
| **Custom hooks** | camelCase (use prefix) | `useProcessInsights.js` |
| **Utility files** | camelCase | `dateUtils.js` |
| **Variables/Functions** | camelCase | `formatDate` |
| **Constants** | UPPER_SNAKE_CASE | `MAX_RETRIES` |

### Import Patterns

```jsx
// Common components
import { Button, TableComponent } from '../common';

// Feature components
import Masters from '../Admin/Masters';

// Hooks
import { useProcessInsights } from '../../hooks/useProcessInsights';

// Utils
import { formatDate } from '../../utils/dateUtils';

// Redux
import { useSelector, useDispatch } from 'react-redux';
```

### Styling Guidelines

- Use **Tailwind CSS** utility classes (avoid inline styles)
- Use CSS modules or styled-components only for complex styling needs
- Maintain responsive design patterns

### Code Quality Standards

- Use **functional components** with hooks
- Follow **single responsibility principle** for components
- Add **PropTypes** for runtime type checking
- Write **descriptive variable names** (avoid abbreviations)
- Keep components **small and focused** (< 300 lines recommended)
- Document complex logic with JSDoc comments

---

## 🤝 Contributing

### Git Workflow

1. Create feature branch: `git checkout -b feature/feature-name`
2. Make changes and commit: `git commit -m "feat: add feature description"`
3. Push to remote: `git push origin feature/feature-name`
4. Create Pull Request

### Pull Request Guidelines

- Provide clear description of changes
- Include screenshots for UI changes
- Test across different browsers and screen sizes
- Ensure no console errors or warnings
- Follow existing code patterns

---

## 🐛 Troubleshooting

### Common Issues

**1. Dev server won't start**
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

**2. API requests failing**
- Ensure backend server is running on correct port
- Check proxy configuration in `vite.config.js`
- Verify CORS settings on backend

**3. Build fails with chunk size warning**
- Review `manualChunks` configuration in `vite.config.js`
- Consider lazy loading large libraries

**4. Styling issues**
- Ensure Tailwind is scanning all component files
- Check `tailwind.config.js` content paths
- Rebuild if CSS is missing

**5. Import path errors**
- Verify correct relative path (`../` vs `../../`)
- Check file exists at target location
- Ensure component is exported correctly

---

## 📚 Additional Resources

### External Resources
- **[Vite Documentation](https://vitejs.dev/)** - Official Vite docs
- **[React Documentation](https://react.dev/)** - Official React docs
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[Redux Toolkit](https://redux-toolkit.js.org/)** - State management
- **[TanStack Query](https://tanstack.com/query/latest)** - Data fetching

---

**Last Updated:** May 2026  
**Version:** 2.0  
**Maintained By:** APEdge Development Team