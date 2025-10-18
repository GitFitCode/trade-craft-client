# Algorithmic Trading Client

# Extended By Devs @ <a href="https://www.gitfitcode.com" target="_blank">gitfitcode</a> and huge thanks to <a href="https://github.com/robertjosephwayne" target="_blank">Robert</a> who developed <a href="https://www.financebrain.ai/" target="_blank">FinanceBrain</a> for the initial idea and implementation.

# Project Overview

This is an algorithmic trading dashboard client built with Next.js 13 (App Router), React 18, Redux Toolkit, and TypeScript. The application provides real-time trading data visualization, portfolio management, and market analysis tools.

## Development Commands

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Start production server
npm run start

# Run linting
npm run lint

# Format code with Prettier
npm run format

# Deploy to GitHub Pages
npm run deploy
```

## Architecture

### Tech Stack
- **Framework**: Next.js 13 with App Router (experimental)
- **State Management**: Redux Toolkit with RTK Query for API calls
- **UI Library**: Material-UI (MUI) with custom dark theme
- **Real-time Communication**: Socket.io client for WebSocket connections
- **Charts**: Recharts and TradingView widgets
- **Styling**: Tailwind CSS
- **Code Quality**: ESLint, Prettier, Husky with lint-staged

### Key Directories
- `/app` - Next.js 13 App Router pages and layouts
- `/components` - Reusable React components
- `/api` - RTK Query API slice configuration
- `/redux` - Redux store and feature slices
- `/public` - Static assets

### API Integration
The application connects to a backend server configured in `constants.ts`:
- Development: `http://localhost:8000`
- Production: `https://financial-dashboard-api.herokuapp.com`

### State Architecture
- **RTK Query**: Handles all REST API calls with caching (see `api/apiSlice.ts`)
- **Redux Slices**: `cryptoSlice` manages cryptocurrency market data
- **WebSocket**: Real-time bar data updates via Socket.io

### Key Features
- Real-time price charts with TradingView integration
- Portfolio metrics and history visualization
- Orders and positions management
- Market summary tables
- WebSocket integration for live data updates

## Development Notes

### TypeScript Configuration
- Strict mode enabled
- Target: ES5 for broader compatibility
- JSX: Preserve for Next.js optimization

### Routing
- Default redirect from `/` to `/charts`
- Available routes: `/charts`, `/portfolio-metrics`, `/positions`, `/orders`, `/returns`, `/trade-book`, `/fundamentals`, `/portfolio-history`

### Component Pattern
Each page follows a consistent pattern:
- Page component in `/app/[route]/page.tsx`
- Loading component in `/app/[route]/loading.tsx`
- Data fetching via RTK Query hooks
- Loader component for loading states

### Pre-commit Hooks
Husky runs lint-staged on commits:
- Prettier formatting
- Next.js linting with auto-fix
