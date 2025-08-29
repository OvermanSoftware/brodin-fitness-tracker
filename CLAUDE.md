# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Brodin Fitness Tracker is a React + TypeScript fitness tracking application built with Vite. It's designed as a Capacitor mobile app with Supabase authentication and database integration.

## Development Commands

- `npm run dev` - Start development server
- `npm run build` - Build for production (runs TypeScript check first)
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run lint:fix` - Fix ESLint issues automatically
- `npm run format` - Format code with Prettier
- `npm run type-check` - Run TypeScript type checking without emitting files

## Architecture

### Tech Stack
- **Frontend**: React 19 + TypeScript
- **Styling**: Mantine UI components + TailwindCSS
- **Build Tool**: Vite
- **Mobile**: Capacitor for iOS/Android
- **Backend**: Supabase (auth + database)
- **State Management**: SWR for data fetching
- **Forms**: React Hook Form
- **Routing**: React Router v7

### Project Structure
```
src/
├── app/                    # Main app setup
│   ├── App.tsx            # Root component with auth logic
│   ├── Providers.tsx      # Mantine provider setup
│   ├── Router.tsx         # React Router setup
│   ├── pages/             # Route components
│   └── supabaseClient.ts  # Supabase client config
├── components/            # Shared UI components
├── features/              # Feature-based modules
│   ├── settings/          # User settings feature
│   └── progress-pics/     # Progress photos feature
├── hooks/                 # Shared React hooks
└── layouts/               # Layout components
```

### Feature Organization
Features follow Bulletproof React conventions with modular structure under `src/features/`:
- `api/` - API calls and data fetching
- `components/` - Feature-specific components  
- `hooks/` - Feature-specific custom hooks
- `types/` - TypeScript type definitions

Each feature is self-contained with its own API layer, components, and business logic.

### Authentication Flow
The app uses Supabase Auth UI for authentication. `App.tsx` handles the auth state:
- Shows loading spinner while checking session
- Shows auth UI if no session
- Shows main app if authenticated

## Code Style & Linting

- Uses Airbnb ESLint config with TypeScript support
- Prettier for code formatting
- Arrow functions enforced for React components
- React 18+ patterns (no need for React import in JSX)

## Mobile App

Configured with Capacitor for cross-platform mobile deployment:
- App ID: `com.mogware.brodin`
- App Name: "Brodin Fitness" 
- Build output goes to `dist/` directory

## Key Dependencies

- **UI**: @mantine/core, @mantine/form, @mantine/notifications
- **Icons**: @tabler/icons-react (aliased in Vite config for performance)
- **Data**: @supabase/supabase-js, swr
- **Charts**: recharts
- **Date**: react-datepicker