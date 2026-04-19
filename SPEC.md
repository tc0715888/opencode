# Domain Matrix - Domain Management Console

## 1. Concept & Vision

A cyberpunk-inspired domain management dashboard that feels like a command center for tracking digital assets. The interface evokes the feeling of hacking into a futuristic network operations center - dark backgrounds, glowing data streams, and crisp monospace typography. Domain management shouldn't feel like accounting; it should feel like controlling critical infrastructure.

## 2. Design Language

**Aesthetic Direction:** Cyberpunk terminal / sci-fi command center - inspired by Blade Runner, The Matrix, and modern DevOps dashboards.

**Color Palette:**
- Background Primary: `#0a0e17` (deep space black)
- Background Secondary: `#111827` (dark slate)
- Background Card: `#1a2234` (elevated surface)
- Accent Primary: `#00f0ff` (cyan glow)
- Accent Secondary: `#7c3aed` (electric purple)
- Accent Warning: `#f59e0b` (amber alert)
- Accent Danger: `#ef4444` (red alert)
- Accent Success: `#10b981` (green confirmation)
- Text Primary: `#f1f5f9` (bright white)
- Text Secondary: `#94a3b8` (muted gray)
- Border: `#1e3a5f` (subtle blue border)

**Typography:**
- Headings: "Orbitron" (sci-fi geometric sans)
- Body/Data: "JetBrains Mono" (monospace for data)
- UI Elements: "Inter" (clean UI text)

**Spatial System:**
- Base unit: 8px
- Card padding: 24px
- Section gaps: 32px
- Border radius: 8px (subtle, not rounded)

**Motion Philosophy:**
- Scanline effects on hover (horizontal line sweep)
- Glow pulse on status indicators
- Smooth fade-in for data rows (staggered 50ms)
- Typing effect for loading states
- Subtle grid background animation

**Visual Assets:**
- Custom SVG icons with glow effects
- ASCII-style decorative elements
- Grid/matrix background pattern
- Data stream visual indicators

## 3. Layout & Structure

### Header
- Logo: "DOMAIN MATRIX" with glitch effect
- Status bar showing connection status and last sync time
- Import button (prominent)

### Main Content Area
- **Control Bar:** Search/filter, bulk actions, view toggle (table/grid)
- **Data Table:** Domain list with sortable columns
- **Detail Panel:** Slide-in panel showing full domain info

### Data Table Columns
1. Status indicator (color-coded dot)
2. Domain name (primary key, bold)
3. Registrar
4. Registration Date
5. Expiration Date
6. Days Until Expiry (with color coding)
7. Renewal Price
8. Auto-renew status
9. Actions (view details, whois lookup)

### Footer
- Statistics bar: total domains, expiring soon, expired count
- Version/info

## 4. Features & Interactions

### Excel Import
- Drag-and-drop zone or file picker
- Supports .xlsx, .xls, .csv formats
- Auto-detects domain column(s) from headers
- Preview before import with column mapping
- Progress indicator during WHOIS lookup

### Domain Data Display
- Domains sorted by expiration date (default)
- Color-coded expiry warnings:
  - Red: expired or < 30 days
  - Amber: 30-90 days
  - Green: > 90 days
- Hover reveals quick actions

### WHOIS Lookup
- Batch lookup with rate limiting (avoid API throttling)
- Cache results to reduce API calls
- Manual refresh button per domain
- Full WHOIS data in detail panel

### Search & Filter
- Real-time search across all fields
- Filter by: status, registrar, expiry range, price range
- Bulk select for batch operations

### Export
- Export current view to Excel
- Export WHOIS data for all domains

### Detail Panel
- Slides in from right
- Full WHOIS record display
- Timeline of key dates
- Registrar contact info (if available)
- Historical data if previously looked up

## 5. Component Inventory

### Status Indicator
- Pulsing dot with glow
- States: active (green), expiring (amber), expired (red), unknown (gray)

### Domain Row
- Default: subtle background
- Hover: glow border, scanline effect
- Selected: accent border left
- Loading: skeleton shimmer

### Import Zone
- Dashed border, becomes solid on drag-over
- Icon + instructional text
- Progress bar during processing

### Data Card (Grid View)
- Elevated surface with subtle glow
- Domain name prominent
- Expiry countdown as large number
- Status badge in corner

### Button Variants
- Primary: cyan glow, filled
- Secondary: outline with hover fill
- Danger: red accent
- Ghost: text only with underline on hover

### Input Fields
- Dark background with subtle border
- Cyan glow on focus
- Search icon prefix

## 6. Technical Approach

**Stack:** Single HTML file with embedded CSS/JS for portability

**Libraries:**
- SheetJS (xlsx.full.min.js) for Excel parsing
- Custom WHOIS lookup via public API (whoisxmlapi.com or similar)

**Data Flow:**
1. User imports Excel → SheetJS parses → domains extracted
2. For each domain, WHOIS lookup triggered (with batching)
3. Results cached in localStorage for persistence
4. UI updates reactively

**API Strategy:**
- Use whoisxmlapi.com free tier for WHOIS data
- Fallback to cached data if API fails
- Rate limiting: 1 request/second to avoid throttling

**Storage:**
- localStorage for cached WHOIS data
- Session state for current import/view

**Domain Column Detection:**
- Look for headers containing "domain", "domain name", "url", "site"
- Or prompt user to select column if ambiguous
