# POC_QueerPlace

## Stack

- TypeScript
- React 18/19 (Frontend)
- Next.js (App Router, Server Actions)
- Vercel (Hosting)
- Turso (Distributed libSQL / SQLite)
- DrizzleORM (ORM)
- Tailwind CSS (Utility-first styling)
- Cloudflare (Image hosting optimization)
- GitHub Actions (CI/CD)
- Docker

## Project Overview

MVP (Minimum Viable Product): A specialized platform to book LGBTQ+ friendly tour guides and inclusive hotels, currently focused on the Tokyo area. take inspiration of the web page JapanGayGuide

## Purpose

To demonstrate a scalable, high-performance booking architecture using a modern Next.js stack. It showcases real-world software engineering practices including database modeling, strict type validation, and concurrency state management for booking systems.

## Architecture Design

### Folder Directory

The project follows a modular architecture using the `src/` directory pattern, enforcing strict separation of concerns, testing, and containerization.

├── .agents/              # AI agent configurations and workflows (e.g., react-doctor)
├── .windsurf/rules/      # Architecture rules and AI behavior guidelines
├── public/               # Static assets (images, icons)
├── src/                  # Main application source code
│   ├── __tests__/        # Unit and integration tests (Vitest)
│   ├── app/              # Application Routes (Next.js App Router)
│   ├── components/       # Reusable UI & Domain Components (shadcn/ui, booking)
│   ├── db/               # Database schema (Drizzle ORM) and migrations
│   ├── doc/              # Internal project documentation
│   ├── hooks/            # Custom React hooks for state management
│   ├── lib/              # Utilities (date formatting, Turso client config)
│   └── types/            # Global TypeScript definitions (e.g., auth.ts, index.ts)
├── .env.example          # Template for environment variables
├── docker-compose.yml    # Local container orchestration
├── Dockerfile            # Production image build recipe
├── middleware.ts         # Next.js middleware (Route protection & Auth)
└── vitest.config.ts      # Testing framework configuration

## Core User Flow (MVP Scope)

1. **Discovery:** User browses available LGBT-friendly hotels and tour guides using dynamic filters (e.g., location, LGBTQ+ owned, trans-inclusive staff).
2. **Details & Availability:** User selects a specific listing to view details, gallery, and real-time date availability.
3. **Booking Process:** User selects dates and guest count. The system creates a pending reservation (avoiding double-booking).
4. **Confirmation:** The booking state transitions to 'Confirmed', and the user views the summary in their dashboard.

## Data Model (Drizzle ORM Outline)

- `users`: Manages authentication and user profiles.
- `listings`: Stores data for hotels and tour guides (Type, Name, Description, Pricing).
- `bookings`: Associates users with listings based on Date ranges and Status (Pending/Confirmed/Canceled).

## Functional Requirements

- **Validations:** Uses Zod with TypeScript for strict date and form validations.
- **Payment Mock:** As an MVP, the payment gateway is mocked to focus on the core booking state machine.

## Technical Vision & Integration Strategy

While this MVP is built using a modern decoupled JavaScript stack to showcase robust software architecture, the underlying database schema and booking logic are platform-agnostic. This architecture is designed with a "Headless" mindset, meaning it could eventually serve as a booking engine operating alongside an existing CMS (such as WordPress).
