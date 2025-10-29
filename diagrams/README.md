# 📊 Trading Alerts SaaS - System Diagrams

Visual documentation for the Trading Alerts SaaS platform architecture, data flows, and implementation timeline.

## 🎯 Overview

This folder contains **12 Mermaid diagrams** providing comprehensive visual documentation of the system architecture, from high-level context down to detailed sequences and database schemas.

**Last Updated:** October 29, 2025  
**Version:** 1.1.0  
**Architecture Doc:** [trading-saas-v4_Realignment of V3.md](../trading-saas-v4_Realignment%20of%20V3.md)

## 📋 Diagram Index

### Architecture & Context Diagrams

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **01** | [System Overview](./01-system-overview.mmd) | C4 Context diagram showing external actors, system boundary, and major components | Context |
| **02** | [Components](./02-components.mmd) | Detailed component architecture including Next.js layers, Flask service, error tracking, and data layer | Container |
| **03** | [API Endpoints](./03-api-endpoints.mmd) | Complete mapping of all REST API endpoints organized by feature area | Component |
| **04** | [Database Schema](./04-database-schema.mmd) | Entity-Relationship diagram with all 15 tables, relationships, and constraints | Data |

### Sequence & Flow Diagrams

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **05** | [Auth Flow](./05-auth-flow.mmd) | Complete authentication sequence: registration → email verification → login → session | Sequence |
| **06** | [Indicator Flow](./06-indicator-flow.mmd) | MT5 indicator data flow from terminal through Flask service to TradingView charts | Sequence |
| **07** | [Alert Flow](./07-alert-flow.mmd) | Alert system lifecycle: creation → background checking → multi-channel notifications | Sequence |
| **11** | [WebSocket Architecture](./11-websocket-architecture.mmd) | Real-time notification system using Socket.IO and Redis Pub/Sub | Sequence |
| **12** | [Error Handling](./12-error-handling.mmd) | Comprehensive error handling flows covering 10 scenarios from MT5 failures to recovery | Sequence |

### Deployment & Infrastructure

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **08** | [Docker Architecture](./08-docker-architecture.mmd) | Local development Docker Compose setup with all services and networks | Infrastructure |
| **09** | [Deployment](./09-deployment.mmd) | Production deployment architecture: Vercel + Railway + Upstash + external services | Infrastructure |

### Project Management

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **10** | [Implementation Phases](./10-implementation-phases.mmd) | 10-week Gantt chart with phases, milestones, dependencies, and error handling tasks | Timeline |

## 📖 Viewing Diagrams

### Option 1: GitHub (Recommended)
GitHub automatically renders `.mmd` files with proper syntax highlighting. Simply click any diagram link above.

### Option 2: Mermaid Live Editor
1. Copy diagram content from any `.mmd` file
2. Visit [mermaid.live](https://mermaid.live)
3. Paste content into the editor
4. View rendered diagram and optionally export as SVG/PNG

### Option 3: VS Code
Install the [Mermaid Preview](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid) extension for inline diagram rendering.

## 🛠️ Technology Stack Reference

All diagrams are validated against these specifications:

| Component | Technology | Version | Specification |
|-----------|-----------|---------|---------------|
| **Frontend** | Next.js + React + TypeScript | 14.x, 18.x, 5.x | [Architecture Doc](../trading-saas-v4_Realignment%20of%20V3.md) |
| **Backend API** | Next.js API Routes + NextAuth.js | 14.x, 5.x | [openapi.yaml](../openapi.yaml) |
| **MT5 Service** | Flask + Python | 3.0, 3.11+ | [openapi-flask.yaml](../openapi-flask.yaml) |
| **Database** | PostgreSQL + Prisma ORM | 15.x, 5.x | [Prisma Schema](../prisma/schema.prisma) |
| **Cache/Queue** | Redis + BullMQ | 7.x | [Architecture Doc](../trading-saas-v4_Realignment%20of%20V3.md) |
| **Real-time** | Socket.IO | Latest | [11-websocket-architecture.mmd](./11-websocket-architecture.mmd) |
| **Charts** | TradingView Lightweight Charts | 4.x | [06-indicator-flow.mmd](./06-indicator-flow.mmd) |
| **Error Tracking** | Sentry.io | Latest | [12-error-handling.mmd](./12-error-handling.mmd) |

## 📚 Diagram Relationships

Understanding how diagrams connect:
```
01-system-overview.mmd (Context)
    ↓ zooms into
02-components.mmd (Containers & Components)
    ↓ expands API layer
03-api-endpoints.mmd (All REST endpoints)
    ↓ uses database
04-database-schema.mmd (15 tables + relationships)

05-auth-flow.mmd (Authentication sequences)
    ↓ user authenticated, then
06-indicator-flow.mmd (Fetch MT5 data)
    ↓ which triggers
07-alert-flow.mmd (Alert checking & notification)
    ↓ notifies via
11-websocket-architecture.mmd (Real-time WebSocket)

All flows handle errors via:
12-error-handling.mmd (10 error scenarios + recovery)

08-docker-architecture.mmd (Local dev environment)
    ↓ deploys to
09-deployment.mmd (Production infrastructure)

10-implementation-phases.mmd (Build timeline for all above)
```

## ✅ Validation Checklist

All diagrams have been validated against:

- ✅ **Architecture Document:** [trading-saas-v4_Realignment of V3.md](../trading-saas-v4_Realignment%20of%20V3.md) (5700+ lines)
- ✅ **Next.js API Spec:** [openapi.yaml](../openapi.yaml) (40+ endpoints)
- ✅ **Flask MT5 API Spec:** [openapi-flask.yaml](../openapi-flask.yaml) (2 endpoints)
- ✅ **Prisma Database Schema:** Section 6.1 in architecture doc (15 tables)
- ✅ **Phase Milestones:** [PHASE-BY-PHASE SETUP MILESTONES.txt](../PHASE-BY-PHASE%20SETUP%20MILESTONES.txt)
- ✅ **Error Handling Patterns:** Comprehensive 10-scenario coverage

**Validation Date:** October 29, 2025  
**Review Status:** ✅ Approved for Phase 1.3

## 🔄 Updating Diagrams

### When to Update
Update diagrams when:
- Adding new API endpoints
- Modifying database schema
- Changing system architecture
- Adding new services or components
- Updating deployment infrastructure
- Modifying error handling strategies

### Update Process
1. Edit the `.mmd` file directly in your code editor
2. Validate syntax at [mermaid.live](https://mermaid.live)
3. Ensure consistency with related diagrams
4. Update this README if adding/removing diagrams
5. Commit with descriptive message:
```bash
   git add diagrams/
   git commit -m "docs: update 04-database-schema - add PaymentMethod table"
   git push
```

### Style Guidelines
- **Colors:** Use consistent color schemes across related diagrams
- **Labels:** All arrows and connections must have descriptive labels
- **Subgraphs:** Group related components using subgraphs
- **Comments:** Add `Note over` annotations for complex interactions
- **Technology:** Always specify versions (e.g., "Next.js 14", "Python 3.11+")
- **Indentation:** Use 4 spaces for Gantt chart configurations

## 🎨 Color Coding Reference

Consistent color scheme used across all diagrams:

| Color | Hex Code | Usage |
|-------|----------|-------|
| 🔵 **Blue** | `#1976D2` | Next.js, Frontend, Browser |
| 🟢 **Green** | `#388E3C` | Flask, Backend Services, Success states |
| 🟡 **Yellow** | `#FBC02D` | PostgreSQL, Databases |
| 🔴 **Red** | `#D32F2F` | Redis, Cache, Alert states |
| 🟣 **Purple** | `#7B1FA2`, `#5E35B1` | WebSocket, Real-time features |
| 🟠 **Orange** | `#F57C00`, `#E65100` | External systems (MT5, Stripe) |
| ⚪ **Gray** | `#9E9E9E` | System utilities, Health checks |
| 🩷 **Pink** | `#FCE4EC` | Error tracking, Monitoring (Sentry) |

## 🎯 Key Features Documented

### Error Handling Infrastructure (NEW)
Diagram 12 provides comprehensive coverage of:
- **MT5 Connection Failures:** Retry logic with exponential backoff (3 attempts)
- **Flask Service Timeouts:** 30-second timeout with graceful degradation
- **Database Errors:** Connection pool management and retry strategies
- **Redis Cache Failures:** Graceful degradation to direct data fetch
- **Rate Limiting:** User-tier based limits with clear error messages
- **Validation Errors:** Client-side form validation with inline feedback
- **Authentication Failures:** Session expiry handling and re-authentication
- **Symbol Not Found:** MT5 symbol availability checking
- **Critical System Errors:** Global exception handler with Sentry integration
- **Recovery Patterns:** Automatic retry and user notification flows

### Component Updates
Diagram 02 now includes:
- **Error Boundary:** React error catching component
- **Error Handler:** Global error handling service
- **Sentry Client:** Error tracking integration
- **Logger Service:** SystemLog database writer
- **Flask Error Handler:** MT5 retry logic

### Database Schema Updates
Diagram 04 improvements:
- ✅ Removed incorrect VerificationToken relationship (uses identifier, not FK)
- ✅ Expanded AlertType enum to show all 6 values
- ✅ Enhanced SystemLog source field documentation

### Implementation Timeline Updates
Diagram 10 enhancements:
- ✅ Added error handling tasks across all phases (17 new tasks)
- ✅ Included Sentry integration in Phase 4
- ✅ Added ongoing error monitoring in Phase 5
- ✅ Proper Gantt chart indentation syntax

## 📖 Related Documentation

- **Main Architecture:** [trading-saas-v4_Realignment of V3.md](../trading-saas-v4_Realignment%20of%20V3.md)
- **API Specifications:**
  - [openapi.yaml](../openapi.yaml) - Next.js API
  - [openapi-flask.yaml](../openapi-flask.yaml) - Flask MT5 Service
- **Implementation Guide:** [PHASE-BY-PHASE SETUP MILESTONES.txt](../PHASE-BY-PHASE%20SETUP%20MILESTONES.txt)
- **Database Schema:** See Prisma section in architecture doc
- **Deployment Guide:** Section 12 in architecture doc

## 📞 Support & Questions

For questions about these diagrams:
1. Review the [Architecture Document](../trading-saas-v4_Realignment%20of%20V3.md) first
2. Check the corresponding OpenAPI specification
3. Validate against the Prisma schema
4. Cross-reference with related diagrams using the [Diagram Relationships](#-diagram-relationships) section
5. For error handling patterns, consult [12-error-handling.mmd](./12-error-handling.mmd)

## 📜 Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| **1.1.0** | **Oct 29, 2025** | **Error handling infrastructure updates** | **Phase 1.2 Completion** |
| | | • **Added diagram 12:** Comprehensive error handling (10 scenarios) | |
| | | • **Updated diagram 02:** Added error tracking components (Sentry, ErrorBoundary, ErrorHandler) | |
| | | • **Updated diagram 04:** Fixed VerificationToken relationship, expanded AlertType enum | |
| | | • **Updated diagram 10:** Added 17 error handling tasks across all phases | |
| | | • **Total diagrams:** 12 (increased from 11) | |
| 1.0.0 | Oct 2025 | Initial release - 11 diagrams covering complete system architecture | Phase 1.2 |
| | | • Added System Overview (C4 Context) | |
| | | • Added Component Architecture | |
| | | • Added API Endpoint mapping (40+ endpoints) | |
| | | • Added Database ER diagram (15 tables) | |
| | | • Added Auth, Indicator, Alert sequence flows | |
| | | • Added WebSocket architecture | |
| | | • Added Docker & Deployment diagrams | |
| | | • Added 10-week Implementation Gantt chart | |

## 🎉 Phase 1.2 Completion Status

**✅ ALL DIAGRAMS VALIDATED AND APPROVED**

| Diagram | Status | Last Updated |
|---------|--------|--------------|
| 01-system-overview.mmd | ✅ Approved | Oct 2025 |
| 02-components.mmd | ✅ Updated & Approved | Oct 29, 2025 |
| 03-api-endpoints.mmd | ✅ Approved | Oct 2025 |
| 04-database-schema.mmd | ✅ Updated & Approved | Oct 29, 2025 |
| 05-auth-flow.mmd | ✅ Approved | Oct 2025 |
| 06-indicator-flow.mmd | ✅ Approved | Oct 2025 |
| 07-alert-flow.mmd | ✅ Approved | Oct 2025 |
| 08-docker-architecture.mmd | ✅ Approved | Oct 2025 |
| 09-deployment.mmd | ✅ Approved | Oct 2025 |
| 10-implementation-phases.mmd | ✅ Updated & Approved | Oct 29, 2025 |
| 11-websocket-architecture.mmd | ✅ Approved | Oct 2025 |
| 12-error-handling.mmd | ✅ New - Approved | Oct 29, 2025 |

**Ready to proceed to Phase 1.3: Architecture Documentation** 🚀

## 📄 License

These diagrams are part of the Trading Alerts SaaS project and follow the same license as the main project (MIT).

---

## 📊 Quick Stats

- **Total Diagrams:** 12
- **Total Lines of Mermaid Code:** ~3,000
- **API Endpoints Documented:** 40+
- **Database Tables Documented:** 15
- **Error Scenarios Covered:** 10
- **Implementation Weeks:** 10
- **External Services:** 5 (MT5, Stripe, Resend, Sentry, Railway)
- **Technology Stack Components:** 15+