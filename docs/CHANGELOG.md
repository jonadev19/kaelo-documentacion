# CHANGELOG - Kaelo Documentación

Todos los cambios notables a este proyecto serán documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/),
y este proyecto adhiere a [Semantic Versioning](https://semver.org/lang/es/).

## [Unreleased]

### Planned
- Implementación completa de sistema modular
- Migración a Git para control de versiones

---

## [1.2] - 2026-02-15 (EJEMPLO - No implementado aún)

### Added
- Edge Case #4: Merchant offline scenarios during order placement
- Payment retry strategy (exponential backoff con 3 intentos)
- Webhook endpoint para Stripe payment confirmations
- Database índice en `orders.created_at` para mejorar queries

### Changed
- API latency target: <500ms → <300ms (P95)
- Database connection pool: 20 → 25 connections
- Mapbox tile cache duration: 7 days → 14 days
- Order timeout period: 30 min → 45 min

### Fixed
- Typo en RF-006 acceptance criteria ("payment" → "payment processing")
- Broken link en 03-architecture.md referencing deployment
- Incorrect SQL syntax en `reserve_stock_atomic` function

### Deprecated
- Wearable integration moved from Phase 1 to Phase 2
- Review/Rating system postponed to post-launch

### Removed
- N/A

### Security
- Added rate limiting to authentication endpoints (5 attempts/hour)

---

## [1.1] - 2026-01-27

### Added
- **Detailed edge cases analysis** (Sección 11)
  - Network partition durante order placement
  - Concurrent stock updates (race condition)
  - Offline-first sync conflicts
- **Enhanced testing strategy** (Sección 14)
  - Test pyramid con coverage targets
  - Unit test examples
  - Integration test examples
- **Security considerations** (Sección 17)
  - Security checklist completo
  - RLS policy examples
  - GDPR compliance guidelines
- **Budget breakdown** (Sección 18)
  - Monthly infrastructure costs
  - One-time costs
  - Break-even analysis

### Changed
- Reorganized document structure para mejor navegación
- Updated technical stack con versiones específicas
- Expanded competitive analysis con feature comparison matrix

### Fixed
- N/A

---

## [1.0] - 2026-01-20

### Added
- **Initial Release** - Full project specification
- Project identification y problem statement
- SMART objectives framework
- Functional requirements (User, Merchant, Admin modules)
- Non-functional requirements con monitoring strategy
- System architecture diagrams
- Data model con PostgreSQL/PostGIS schemas
- Stakeholder analysis
- Competitive analysis
- Market research (TAM/SAM/SOM)
- Risk management matrix
- Gantt chart (6-month timeline)
- Legal & compliance section

---

## Formato de Entradas

Usa este formato para nuevos cambios:

```markdown
## [X.Y] - YYYY-MM-DD

### Added
- Nueva funcionalidad o sección agregada

### Changed
- Cambios en funcionalidad existente
- Actualizaciones de valores/métricas

### Deprecated
- Funcionalidades marcadas para remover en futuras versiones

### Removed
- Funcionalidades removidas

### Fixed
- Correcciones de bugs o errores

### Security
- Cambios relacionados con seguridad
```

---

## Tipos de Cambios

- **Added**: para nuevas funcionalidades
- **Changed**: para cambios en funcionalidad existente
- **Deprecated**: para funcionalidades que pronto serán removidas
- **Removed**: para funcionalidades removidas
- **Fixed**: para correcciones de bugs
- **Security**: en caso de vulnerabilidades

---

## Versionado Semántico

- **MAJOR (X.0.0)**: Cambios incompatibles en la API o arquitectura fundamental
- **MINOR (1.X.0)**: Nuevas funcionalidades compatibles con versión anterior
- **PATCH (1.0.X)**: Correcciones de bugs compatibles con versión anterior

**Ejemplo:**
- `1.0.0` → `1.1.0`: Agregar nueva sección (edge cases)
- `1.1.0` → `1.1.1`: Corregir typo en requirement
- `1.1.0` → `2.0.0`: Cambiar stack tecnológico completamente
