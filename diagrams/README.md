# 📊 Trading Alerts SaaS - System Diagrams

Visual documentation for the Trading Alerts SaaS platform architecture, data flows, and implementation timeline.

## 🎯 Overview

This folder contains 11 Mermaid diagrams providing comprehensive visual documentation of the system architecture, from high-level context down to detailed sequences and database schemas.

**Last Updated:** October 2025  
**Version:** 1.0.0  
**Architecture Doc:** [trading-saas-v4_Realignment of V3.md](../trading-saas-v4_Realignment%20of%20V3.md)

## 📋 Diagram Index

### Architecture & Context Diagrams

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **01** | [System Overview](./01-system-overview.mmd) | C4 Context diagram showing external actors, system boundary, and major components | Context |
| **02** | [Components](./02-components.mmd) | Detailed component architecture including Next.js layers, Flask service, and data layer | Container |
| **03** | [API Endpoints](./03-api-endpoints.mmd) | Complete mapping of all REST API endpoints organized by feature area | Component |
| **04** | [Database Schema](./04-database-schema.mmd) | Entity-Relationship diagram with all 15 tables, relationships, and constraints | Data |

### Sequence & Flow Diagrams

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **05** | [Auth Flow](./05-auth-flow.mmd) | Complete authentication sequence: registration → email verification → login → session | Sequence |
| **06** | [Indicator Flow](./06-indicator-flow.mmd) | MT5 indicator data flow from terminal through Flask service to TradingView charts | Sequence |
| **07** | [Alert Flow](./07-alert-flow.mmd) | Alert system lifecycle: creation → background checking → multi-channel notifications | Sequence |
| **11** | [WebSocket Architecture](./11-websocket-architecture.mmd) | Real-time notification system using Socket.IO and Redis Pub/Sub | Sequence |

### Deployment & Infrastructure

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **08** | [Docker Architecture](./08-docker-architecture.mmd) | Local development Docker Compose setup with all services and networks | Infrastructure |
| **09** | [Deployment](./09-deployment.mmd) | Production deployment architecture: Vercel + Railway + Upstash + external services | Infrastructure |

### Project Management

| # | Diagram | Description | Type |
|---|---------|-------------|------|
| **10** | [Implementation Phases](./10-implementation-phases.mmd) | 10-week Gantt chart with phases, milestones, and dependencies | Timeline |

## 🔍 Viewing Diagrams

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

## 📚 Diagram Relationships

Understanding how diagrams connect:

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

08-docker-architecture.mmd (Local dev environment)
    ↓ deploys to
09-deployment.mmd (Production infrastructure)

10-implementation-phases.mmd (Build timeline for all above)

## ✅ Validation Checklist

All diagrams have been validated against:

- ✅ **Architecture Document:** [trading-saas-v4_Realignment of V3.md](../trading-saas-v4_Realignment%20of%20V3.md) (5700+ lines)
- ✅ **Next.js API Spec:** [openapi.yaml](../openapi.yaml) (40+ endpoints)
- ✅ **Flask MT5 API Spec:** [openapi-flask.yaml](../openapi-flask.yaml) (2 endpoints)
- ✅ **Prisma Database Schema:** Section 6.1 in architecture doc (15 tables)
- ✅ **Phase Milestones:** [PHASE-BY-PHASE SETUP MILESTONES.txt](../PHASE-BY-PHASE%20SETUP%20MILESTONES.txt)

**Validation Date:** October 2025  
**Review Status:** ✅ Approved for Phase 1.3

## 🔄 Updating Diagrams

### When to Update
Update diagrams when:
- Adding new API endpoints
- Modifying database schema
- Changing system architecture
- Adding new services or components
- Updating deployment infrastructure

### Update Process
1. Edit the `.mmd` file directly in your code editor
2. Validate syntax at [mermaid.live](https://mermaid.live)
3. Ensure consistency with related diagrams
4. Update this README if adding/removing diagrams
5. Commit with descriptive message:
   
   bash
   git add diagrams/
   git commit -m "docs: update 04-database-schema - add PaymentMethod table"
   git push

### Style Guidelines
- **Colors:** Use consistent color schemes across related diagrams
- **Labels:** All arrows and connections must have descriptive labels
- **Subgraphs:** Group related components using subgraphs
- **Comments:** Add `Note over` annotations for complex interactions
- **Technology:** Always specify versions (e.g., "Next.js 14", "Python 3.11+")

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

## 📜 Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0.0 | Oct 2025 | Initial release - 11 diagrams covering complete system architecture | Phase 1.2 |
| | | - Added System Overview (C4 Context) | |
| | | - Added Component Architecture | |
| | | - Added API Endpoint mapping (40+ endpoints) | |
| | | - Added Database ER diagram (15 tables) | |
| | | - Added Auth, Indicator, Alert sequence flows | |
| | | - Added WebSocket architecture | |
| | | - Added Docker & Deployment diagrams | |
| | | - Added 10-week Implementation Gantt chart | |

## 📄 License

These diagrams are part of the Trading Alerts SaaS project and follow the same license as the main project (MIT).