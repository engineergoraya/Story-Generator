# StorySpark - AI Story Generator for Kids

## Overview

StorySpark is a kid-friendly AI-powered story generation application that creates magical fantasy stories for children. The application focuses on educational, uplifting content with positive values and moral lessons. Users can either provide custom story ideas or request surprise stories, with content moderation ensuring age-appropriate material.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Library**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom theme variables and Fredoka One font for branding
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Design System**: Component-based architecture with reusable UI components in `/components/ui/`

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **API Design**: RESTful endpoints with JSON responses
- **Error Handling**: Centralized error middleware with structured error responses
- **Logging**: Custom request/response logging middleware

### Data Storage Solutions
- **Database**: PostgreSQL configured through Drizzle ORM
- **Schema Management**: Drizzle Kit for migrations and schema definitions
- **Development Storage**: In-memory storage implementation for development/testing
- **Connection**: Neon Database serverless connection for PostgreSQL

### Database Schema
- **Users Table**: Basic user management with username/password authentication
- **Stories Table**: Generated stories with metadata including title, content, moral, word count, age group, and story type
- **Validation**: Zod schemas for runtime type checking and API validation

### Authentication and Authorization
- **Current Implementation**: Basic user schema prepared for future authentication
- **Session Management**: PostgreSQL session store configured (connect-pg-simple)
- **Security**: Input validation and content moderation for user-generated content

### API Structure
- **Story Generation**: POST `/api/stories/generate` with content moderation and AI generation
- **Story Retrieval**: GET `/api/stories/:id` for individual story access
- **Story Listing**: GET `/api/stories/recent` for browsing recent stories
- **Request Validation**: Zod schema validation for all API endpoints

### Development Workflow
- **Build Process**: Vite for frontend, esbuild for backend bundling
- **Development Server**: Concurrent frontend/backend development with HMR
- **TypeScript**: Strict type checking across frontend, backend, and shared modules
- **Path Aliases**: Configured aliases for clean imports (`@/`, `@shared/`)

## External Dependencies

### AI Services
- **OpenAI GPT-4o**: Primary story generation with structured JSON responses
- **Content Moderation**: Built-in OpenAI moderation for inappropriate content filtering
- **Prompt Engineering**: Custom prompts for age-appropriate, educational storytelling

### Database Services
- **Neon Database**: Serverless PostgreSQL hosting
- **Drizzle ORM**: Type-safe database operations and migrations
- **Database Pooling**: Connection pooling through Neon serverless driver

### UI and Styling
- **Shadcn/ui**: Comprehensive React component library
- **Radix UI**: Accessible headless UI primitives
- **Tailwind CSS**: Utility-first CSS framework
- **Google Fonts**: Fredoka One for branding, Inter for content
- **Font Awesome**: Icon library for UI elements

### Development Tools
- **Replit Integration**: Custom Vite plugins for Replit environment
- **Cartographer Plugin**: Development mode mapping for Replit
- **Runtime Error Overlay**: Enhanced error reporting during development

### Build and Deployment
- **Vite**: Frontend build tool with React plugin
- **esbuild**: Backend bundling for production
- **PostCSS**: CSS processing with Tailwind integration
- **TypeScript Compiler**: Type checking and compilation