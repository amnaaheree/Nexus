# Nexus Business Platform - Architecture Documentation

## Overview
Nexus is a React-based business networking platform built with TypeScript, Vite, and Tailwind CSS. It connects entrepreneurs with investors through a comprehensive dashboard interface.

## Technology Stack
- **Frontend Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS with custom design system
- **Routing**: React Router DOM v6
- **Icons**: Lucide React
- **State Management**: React Context API
- **Calendar**: FullCalendar React
- **Date Handling**: date-fns

## Project Structure

### Root Level
```
/
├── src/
│   ├── components/          # Reusable UI components
│   ├── context/            # React context providers
│   ├── data/               # Static data and mock APIs
│   ├── pages/              # Page components (routes)
│   ├── types/              # TypeScript type definitions
│   └── ...
├── public/                 # Static assets
├── dist/                   # Build output
└── package.json
```

### Components Architecture (`src/components/`)

#### Layout Components (`layout/`)
- **DashboardLayout**: Main layout wrapper with sidebar and navbar
- **Navbar**: Top navigation bar
- **Sidebar**: Left sidebar navigation with role-based menu items

#### UI Components (`ui/`)
- **Avatar**: User avatar display
- **Badge**: Status and category badges
- **Button**: Customizable button component
- **Card**: Card container with header/body variants
- **Calendar**: FullCalendar integration component
- **Input**: Form input field

#### Feature Components
- **chat/**: Chat-related components (ChatMessage, ChatUserList)
- **collaboration/**: Collaboration request components
- **entrepreneur/**: Entrepreneur profile cards
- **investor/**: Investor profile cards

### Context Architecture (`src/context/`)

#### AuthContext
- Manages user authentication state
- Provides login, register, logout functions
- Mock authentication with localStorage persistence
- Role-based access control (entrepreneur/investor)

### Data Layer (`src/data/`)

#### Static Data Files
- **users.ts**: Mock user data (entrepreneurs and investors)
- **messages.ts**: Mock chat messages
- **collaborationRequests.ts**: Mock collaboration requests
- **meetings.ts**: Mock meetings, requests, and availability data

### Pages Architecture (`src/pages/`)

#### Authentication Pages (`auth/`)
- LoginPage, RegisterPage, ForgotPasswordPage, ResetPasswordPage

#### Dashboard Pages (`dashboard/`)
- EntrepreneurDashboard: Entrepreneur-specific dashboard
- InvestorDashboard: Investor-specific dashboard

#### Feature Pages
- **investors/**: Investor discovery and profiles
- **entrepreneurs/**: Entrepreneur discovery and profiles
- **messages/**: Messaging interface
- **notifications/**: Notification center
- **documents/**: Document management
- **settings/**: User settings
- **help/**: Help and support
- **deals/**: Deal tracking
- **chat/**: Real-time chat interface
- **calendar/**: Meeting scheduling calendar

#### Profile Pages (`profile/`)
- EntrepreneurProfile, InvestorProfile

### Type Definitions (`src/types/`)

#### Core Types
- **User**: Base user interface with role discrimination
- **Entrepreneur**: Extended user for entrepreneurs
- **Investor**: Extended user for investors
- **Message**: Chat message structure
- **ChatConversation**: Chat thread metadata

#### Business Logic Types
- **CollaborationRequest**: Investment interest requests
- **Document**: File management structure
- **AuthContextType**: Authentication context interface

#### Calendar Types (New)
- **Meeting**: Scheduled meeting data
- **MeetingRequest**: Meeting invitation structure
- **AvailabilitySlot**: User availability time slots

## Design System

### Color Palette
- **Primary**: Blue tones (#3B82F6 - #1E3A8A)
- **Secondary**: Teal tones (#14B8A6 - #042F2E)
- **Accent**: Amber tones (#F59E0B - #451A03)
- **Success**: Green tones (#22C55E)
- **Warning**: Yellow tones (#F59E0B)
- **Error**: Red tones (#EF4444)

### Typography
- **Font Family**: Inter var (sans-serif)
- **Responsive scaling** with Tailwind utilities

### Responsive Grid
- Mobile-first approach
- Breakpoints: sm (640px), md (768px), lg (1024px), xl (1280px)
- Grid columns: 1-12 with auto-fit layouts

## Routing Structure

### Public Routes
- `/login` - User login
- `/register` - User registration

### Protected Routes (Dashboard Layout)
- `/dashboard/entrepreneur` - Entrepreneur dashboard
- `/dashboard/investor` - Investor dashboard
- `/profile/*` - User profiles
- `/investors` - Investor discovery
- `/entrepreneurs` - Entrepreneur discovery
- `/messages` - Messaging
- `/notifications` - Notifications
- `/documents` - Documents
- `/settings` - Settings
- `/help` - Help
- `/deals` - Deals
- `/chat` - Chat interface
- `/calendar` - Meeting calendar (New)

## State Management

### Authentication State
- User session persistence via localStorage
- Role-based UI rendering
- Protected route guards

### Component State
- Local state for forms and interactions
- Context for global app state
- Mock data for development

## Calendar Integration (Milestone 2)

### Features Implemented
- **FullCalendar Integration**: Month, week, day views
- **Meeting Display**: Confirmed meetings on dashboard calendars
- **Meeting Requests**: Accept/decline functionality
- **Availability Management**: Display user availability slots
- **Calendar Page**: Dedicated calendar management interface

### Data Flow
1. Meetings loaded from mock data based on user participation
2. Calendar events rendered with meeting details
3. Click handlers for date selection and event interaction
4. Request status updates trigger UI re-renders

## Development Workflow

### Scripts
- `npm run dev` - Development server
- `npm run build` - Production build
- `npm run lint` - ESLint checking
- `npm run preview` - Preview production build

### Build Process
- Vite handles bundling and optimization
- TypeScript compilation
- Tailwind CSS purging
- Asset optimization

## Future Enhancements

### Potential Improvements
- Real API integration replacing mock data
- Real-time notifications with WebSockets
- Advanced calendar features (recurring meetings, time zones)
- File upload for documents
- Advanced search and filtering
- Mobile app development
- Multi-language support