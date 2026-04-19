# DOMAIN SELLING PLATFORM - domains.td

## 1. Concept & Vision

A sleek, cyberpunk-inspired domain marketplace for showcasing and selling premium domain names. The platform exudes exclusivity and tech-forward aesthetics, positioning each domain as a valuable digital asset. Access is restricted to the owner via password authentication, while visitors can freely browse the domain listings.

## 2. Design Language

**Aesthetic Direction:** Cyberpunk command center meets luxury showroom - dark, glowing, and premium.

**Color Palette:**
- Background Primary: `#0a0e17` (deep space black)
- Background Secondary: `#111827` (dark slate)
- Background Card: `#1a2234` (elevated surface)
- Accent Primary: `#00f0ff` (cyan glow)
- Accent Secondary: `#7c3aed` (electric purple)
- Accent Gold: `#fuda01` (premium/price highlight)
- Accent Green: `#10b981` (available/success)
- Accent Red: `#ef4444` (sold/unavailable)
- Text Primary: `#f1f5f9` (bright white)
- Text Secondary: `#94a3b8` (muted gray)

**Typography:**
- Headings: "Orbitron" (sci-fi geometric sans)
- Body/Data: "JetBrains Mono" (monospace for data)
- UI Elements: "Inter" (clean UI text)

**Motion Philosophy:**
- Subtle glow pulses on featured domains
- Smooth hover transitions with border glow
- Scan-line effect on interactive elements
- Staggered fade-in for domain cards

## 3. Layout & Structure

### Header
- Logo: "DOMAINS.TD" with glitch effect
- Tagline: "Premium Domain Marketplace"
- Owner access button (locked icon)

### Hero Section
- Brief intro text
- Total domains count
- Total portfolio value

### Domain Grid
- Card-based layout (3 columns on desktop, 1 on mobile)
- Each card shows: domain name, price, TLD category, quick actions

### Domain Card Contents
- Domain name (prominent, clickable)
- Price in USD (gold accent)
- TLD type badge (.com, .ai, .io, etc.)
- Status: Available / In Negotiation / Sold
- Inquiry button

### Admin Panel (Password Protected)
- Password input modal
- Excel import functionality
- Bulk domain management
- Price editing
- Sold status toggle
- Export current list

### Footer
- Contact information
- Last updated timestamp

## 4. Features & Interactions

### Public Features
- Browse all available domains
- Filter by TLD, price range, status
- Search domains
- View domain details
- Contact/inquiry button (mailto link)

### Admin Features (Password Protected)
- Password: user-defined, stored in browser session
- Import domains from Excel (.xlsx, .csv)
- Auto-detect domain column, add price column
- Edit individual domain price/status
- Mark domains as sold
- Remove domains
- Export full list to Excel

### Domain Status
- Available (green) - can be purchased
- In Negotiation (amber) - being discussed
- Sold (red) - no longer available

### Excel Import Format
| Column | Content | Required |
|--------|---------|----------|
| A | Domain Name | Yes |
| B | Price (USD) | Yes |
| C | Status | No (default: Available) |
| D | Notes | No |

## 5. Component Inventory

### Domain Card
- Default: dark card with subtle border
- Hover: cyan border glow, slight lift
- Featured: pulsing gold accent border

### Price Badge
- Large, gold-colored price
- "$" prefix with proper formatting

### Status Badge
- Available: green background, white text
- Negotiation: amber background, dark text
- Sold: red background, white text

### Lock Icon Button
- Unlocked state: cyan glow
- Locked state: gray, clicking shows password prompt

### Password Modal
- Dark modal with centered form
- Password input field
- Show/hide password toggle
- Submit and Cancel buttons

## 6. Technical Approach

**Stack:** Single HTML file with embedded CSS/JS

**Key Libraries:**
- SheetJS (xlsx) for Excel parsing and export

**Data Storage:**
- Browser localStorage for domain list
- Session storage for admin password verification

**Security:**
- Simple password check (client-side, for convenience not high security)
- Password stored in sessionStorage (cleared on browser close)
- No sensitive data exposed publicly

**Export:**
- Export current list to Excel with all fields
- Include: Domain, Price, Status, Notes, Last Updated

**Integration:**
- domains.td - point this domain to this HTML file
- Contact form uses mailto: links
