# 02 - Requirements

**Version:** 1.1
**Last Updated:** Enero 2026

## 4. ALCANCE DEL PROYECTO

### 4.1 MVP Scope (Phase 1)

**Core Features:**

✅ Mobile App (React Native Expo - iOS/Android)
✅ Admin Dashboard (Web-based para comercios)
✅ Route Discovery System con filtros y metadata
✅ Pre-Order Flow (cart + checkout + payment processing)
✅ Merchant Profiles con inventory management
✅ Authentication & Authorization (Supabase Auth)
✅ Offline-First Architecture (mapas descargables + sync strategy)
✅ Payment Gateway Integration (Stripe/MercadoPago)

**Technical Capabilities:**
- Real-time order status updates (WebSockets via Supabase Realtime)
- Geospatial queries para route filtering (PostGIS)
- Progressive Web App (PWA) para merchant dashboard
- Image optimization & CDN delivery (Supabase Storage)

### 4.2 Out of Scope (Phase 2+)

❌ Delivery logistics (last-mile delivery)
❌ Social network features (post sharing, comments, likes)
❌ Wearable integrations (Strava, Garmin Connect)
❌ Review/Rating system completo
❌ Advanced payment methods (crypto, BNPL)
❌ Full-featured web client para ciclistas
❌ Third-party API integrations (weather, traffic)

## 5. STAKEHOLDER ANALYSIS

| Stakeholder | Interest/Value Proposition | Influence Level | Engagement Strategy |
|-------------|---------------------------|-----------------|---------------------|
| Ciclistas Locales | Route safety + service discovery | 🔴 Critical (end users) | Beta testing, feedback loops |
| Ciclistas Turísticos | Curated local experiences | 🟡 High | Partnerships con hoteles/tours |
| Pequeños Comercios | Revenue increase + demand forecasting | 🔴 Critical (supply side) | Onboarding workshops, commission model |
| Universidad | Academic rigor + social impact | 🔴 Critical (evaluadores) | Weekly sync, documentation |
| Comunidades Locales | Economic development distribuido | 🟡 Medium | Community presentations |
| Gobierno Municipal | Tourism promotion + data insights | 🟢 Low | Quarterly reports (opcional) |

## 6. REQUERIMIENTOS FUNCIONALES

### 6.1 User Module (Mobile App)

| ID | Requirement | Priority | Acceptance Criteria | Edge Cases Considerados |
|----|-------------|----------|---------------------|------------------------|
| RF-001 | User Registration | P0 | Email/password signup con email verification | Rate limiting (5 attempts/hour), validation de email format, duplicate account detection |
| RF-002 | Route Discovery | P0 | Interactive map con filters (distance, difficulty, type) | Empty state cuando no hay routes nearby, filter combinations sin results |
| RF-003 | Route Detail View | P0 | Display: distance, elevation profile, POIs, nearby merchants | Missing elevation data fallback, merchants sin inventory |
| RF-004 | Offline Route Download | P0 | Store map tiles + route metadata locally (max 50MB/route) | Storage full scenario, corrupted download recovery, sync conflict resolution |
| RF-005 | Merchant Search | P0 | Filter por category (food, repair, etc.) along route | No merchants on selected route, closed merchants handling |
| RF-006 | Pre-Order Placement | P0 | Product selection + ETA specification + payment | Payment gateway timeout (60s), inventory sold out during checkout, merchant offline |
| RF-007 | Order History | P1 | Chronological list con status tracking | Pagination para >100 orders, cancelled orders display |
| RF-008 | Route Sharing | P2 | Share via deeplink (social/messaging) | Recipient sin app installed (web fallback), expired share links |

### 6.2 Merchant Module (Web Dashboard)

| ID | Requirement | Priority | Acceptance Criteria | Edge Cases Considerados |
|----|-------------|----------|---------------------|------------------------|
| RF-101 | Merchant Registration | P0 | Form: business info, location (geocoded), hours | Duplicate business detection, invalid coordinates handling |
| RF-102 | Product Management | P0 | CRUD operations: name, price, stock, images | Concurrent edits by multiple admins, out-of-stock handling |
| RF-103 | Order Queue Management | P0 | Real-time order list con filtering/sorting | Simultaneous orders spike (>10 concurrent), missed order alerts |
| RF-104 | Order Status Updates | P0 | State machine: pending → preparing → ready → completed → cancelled | State transition validation, customer notification failures |
| RF-105 | Basic Analytics | P1 | Daily/weekly order volume, revenue charts | Insufficient data (<7 days), timezone handling |

### 6.3 Admin Module

| ID | Requirement | Priority | Acceptance Criteria |
|----|-------------|----------|---------------------|
| RF-201 | Route Management | P0 | CRUD routes + GPX upload + metadata editing |
| RF-202 | Merchant Approval Workflow | P1 | Review → Approve/Reject con notifications |
| RF-203 | Content Moderation | P2 | Flagging system para reportes de usuarios |

## 7. REQUERIMIENTOS NO FUNCIONALES

| Categoría | Requirement | Métrica | Target | Monitoring Strategy |
|-----------|-------------|---------|--------|---------------------|
| Performance | API Response Time | P95 latency | <500ms | Supabase Logs + Sentry |
| Performance | Map Tile Loading | Time to interactive | <2s | Custom analytics event |
| Availability | Uptime durante horario operacional | % uptime | 99.5% (8 AM - 10 PM) | UptimeRobot + PagerDuty |
| Scalability | Concurrent Users | Simultaneous connections | 100 users | Load testing con k6 |
| Scalability | Database Connections | Connection pool | 20 max connections | Supabase metrics |
| Security | Data Encryption | In-transit + at-rest | TLS 1.3 + AES-256 | Supabase default |
| Security | Authentication | Token management | JWT con 7-day expiry + refresh | Supabase Auth built-in |
| Compatibility | Mobile OS Support | Platform versions | Android 10+, iOS 14+ | Expo compatibility matrix |
| Reliability | Crash Rate | App crashes | <1% sessions | Sentry crash reports |
| Usability | Task Completion Time | First order placement | <3 min (90th percentile) | User analytics tracking |

---

**Related Documents:**
- [01 - Project Overview](./01-project-overview.md)
- [03 - Architecture](./03-architecture.md)
- [04 - Edge Cases](./04-edge-cases.md)
- [05 - Testing Strategy](./05-testing-strategy.md)
