# 🌏 TheVietnamDMC — B2B Travel Website

> **Developer / AI Context README**
>
> This document explains the current implementation, page structure, user journey, styling system, integrations, known limitations, and safe development rules for **TheVietnamDMC** website.
>
> It is intentionally written so that an AI coding assistant such as Claude can understand the existing project before making changes.

---

## 1. Project Overview

**TheVietnamDMC** is a premium, hospitality-focused **B2B Vietnam Destination Management Company (DMC) website**.

The website is designed primarily for:

- Travel agents
- Tour operators
- Corporate travel clients
- B2B partners
- Group travel / MICE clients

The website's main purpose is currently **company presentation + service discovery + quote enquiry**.

It presents:

- Vietnam destinations
- DMC positioning
- Travel services
- Hotel partnerships
- Halong Bay cruises
- Ground transportation
- Expert guides
- Indian restaurant support
- Visa services
- B2B quote enquiry

The current implementation is intentionally lightweight and is built as a **static website** rather than a React/Vue/Next.js application.

---

# 2. Current Technology Stack

| Technology | Usage |
|---|---|
| HTML5 | Page structure and content |
| CSS3 | All visual design, responsive layout, animations |
| Vanilla JavaScript | Quote form validation and EmailJS submission |
| EmailJS | Sending quote enquiry emails from the browser |ek| Google Fonts | Typography |
| GitHub | Source-code repository |
| GitHub Pages | Static hosting/deployment |
| External image URLs | Destination/background/partner imagery |
| Inline SVG | Small interface icons |
| Emoji | Some service/feature visual elements |

### Important

There is currently:

- No React
- No Vue
- No Angular
- No Node.js application
- No backend server
- No database
- No REST API
- No local CSS file
- No local JavaScript file

Most CSS is embedded directly inside each HTML document.

---

# 3. Repository Structure

Current repository structure:

```text
check/
│
├── .github/
│   └── workflows/
│       └── ...
│
├── README.md
│
├── bg_logo.png
├── white_logo.jpg
│
├── index.htm
├── services.htm
└── get_quote.htm
```

### File responsibilities

| File | Responsibility |
|---|---|
| `index.htm` | Main landing/home page |
| `services.htm` | Detailed services page |
| `get_quote.htm` | B2B quote request form |
| `bg_logo.png` | Local favicon/logo-related image asset |
| `white_logo.jpg` | Local brand asset |
| `.github/workflows/` | GitHub automation/deployment configuration |
| `README.md` | Project documentation |

---

# 4. High-Level Architecture

The current architecture is simple:

```text
                    ┌─────────────────────┐
                    │     index.htm       │
                    │     Home Page       │
                    └─────────┬───────────┘
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
       services.htm     get_quote.htm     Page Sections
       Services Page    Quote Request     #about etc.
             │                │
             │                ▼
             │           Browser JS
             │                │
             │                ▼
             │             EmailJS
             │                │
             │                ▼
             │         Quote Email Service
             │
             ▼
      Additional planned/
      referenced pages
      (currently missing)
```

The website is therefore primarily a **presentation layer**.

The quote form is the main interactive workflow.

---

# 5. User Journey

## 5.1 Main website journey

A normal B2B visitor enters the website through:

```text
Home
 ↓
Understand TheVietnamDMC
 ↓
See company value proposition
 ↓
View destinations
 ↓
View services
 ↓
View partner/certification section
 ↓
Choose "Get Quote"
 ↓
Fill B2B enquiry form
 ↓
Client-side validation
 ↓
EmailJS submission
 ↓
Success message
```

The homepage positions the company as a B2B Vietnam travel partner.

The primary CTA is:

```text
Get Quote
```

which opens:

```text
get_quote.htm
```

---

# 6. `index.htm` — Home Page

## Purpose

`index.htm` is the main landing page and brand showcase.

It contains the largest amount of visual storytelling.

---

## 6.1 Head / Global setup

The page defines:

- UTF-8 character encoding
- Responsive viewport
- Favicon
- Page title
- Google Fonts

Fonts currently include:

- Cormorant Garamond
- DM Sans

The page uses inline CSS rather than a separate stylesheet.

---

## 6.2 Design tokens

The homepage defines CSS variables for the visual system.

Important variables include:

```css
--wine
--gold
--cream
--card
--maroon
```

The intended visual language is:

- Premium
- Luxury hospitality
- Wine/maroon tones
- Gold accents
- Cream/light backgrounds
- Large editorial typography
- Rounded cards
- Soft shadows

When extending the design, preserve this visual language unless a redesign is explicitly requested.

---

# 7. Homepage Navigation

The homepage has a fixed floating navigation bar.

Current navigation structure:

```text
Logo
Home
About
Destinations
Services
MICE
Contact
Get Quote
```

The `Services` link correctly points to:

```text
services.htm
```

The `Get Quote` CTA correctly points to:

```text
get_quote.htm
```

Some navigation items currently reference section IDs such as:

```text
#home
#about
#destinations
#mice
#contact
```

Before creating a new page or changing navigation, verify that the target actually exists.

Do not create dead navigation links.

---

# 8. Homepage Hero

The hero section communicates:

> Crafting Extraordinary Vietnam Journeys

and positions the company as a:

> Premium B2B destination management service.

It contains:

- Badge
- Main heading
- Supporting paragraph
- Get Quote button
- Explore Vietnam button
- Four statistics

Current displayed statistics include:

```text
1000+ Tours Operated
500+ Partner Hotels
98% Agent Satisfaction
24/7 Ground Support
```

### Important development note

These numbers are currently **hard-coded presentation content**.

They are not retrieved from a database or API.

If they are changed, update the HTML directly.

---

# 9. Homepage Background Slideshow

The homepage contains a fixed full-screen background slideshow.

Images are externally hosted.

Current imagery represents locations such as:

- Halong Bay
- Hanoi
- Ho Chi Minh City
- Vietnam landscapes
- Da Nang
- Sapa

The slideshow uses CSS animations.

Important implementation concept:

```text
.bg-slider
    ↓
multiple absolutely positioned images
    ↓
opacity + transform animation
    ↓
timed animation delays
    ↓
dark overlay
    ↓
content displayed above it
```

The overlay exists to maintain text readability.

Do not remove the overlay without checking hero text contrast.

---

# 10. Homepage "Why Choose Us"

The page presents four feature cards:

```text
Dedicated DMC Team
Luxury Hotel Contracts
Fast Quotations
24/7 Execution
```

These are purely presentational cards.

There is currently no JavaScript interaction associated with them.

---

# 11. Partner / Certification Section

The homepage contains:

> Trusted by Industry Leaders

and:

> Our Luxury Accommodation Partners & Certifications

Cards currently represent:

- Wyndham Grand
- Equatorial
- Melia Vinpearl
- Expert Team
- Google Verified
- B2B Certified

Some images are externally hosted.

Important:

The displayed card text and external imagery are static HTML content.

If real corporate branding is introduced, verify ownership/permission and replace placeholder or externally hosted assets with approved assets.

---

# 12. Destination Section

The homepage includes a "Hottest Selling Destinations" section.

Current destinations represented include:

- Halong Bay
- Danang
- Hanoi
- Ho Chi Minh City
- Phu Quoc
- Sapa
- Da Lat
- Nha Trang
- Ninh Binh
- Incense Stick Village

The destination cards are currently primarily visual/presentational.

### Important

Do not assume that each destination has a dedicated destination-detail page.

A destination appearing on the homepage does **not** currently mean that it has a functional booking/details workflow.

---

# 13. Luxury Services Section

Homepage service highlights include:

```text
Hotel Bookings
Airport Transfers
FIT & GIT Packages
Halong Cruises
```

These are presentation cards.

Detailed service information is handled on `services.htm`.

---

# 14. Homepage Statistics

The "Our Numbers" section displays:

```text
5000+ Guests Served
250+ Agent Partners
15+ Years Experience
9 Destinations
```

These are hard-coded values.

They should not be described as dynamically calculated unless a backend/data source is later added.

---

# 15. `services.htm` — Services Page

## Purpose

`services.htm` provides a much deeper explanation of the DMC's operational services.

The page is structured around:

```text
Hero
 ↓
Statistics
 ↓
Comprehensive Travel Solutions
 ↓
Visa Services
 ↓
Additional sections
 ↓
WhatsApp CTA
 ↓
Footer
```

---

# 16. Services Hero

The page introduces:

> Our Comprehensive Travel Services

It positions the company around:

> Premium B2B Travel Solutions

The hero describes the company as handling details of a Vietnam journey for its B2B partners.

---

# 17. Services Statistics

The page displays:

```text
5000+ Guests Served
350+ Partner Hotels
50+ Halong Cruises
15+ Years Experience
```

Again, these are hard-coded values.

---

# 18. Core Services

The services page currently presents the following major service cards.

## M.I.C.E

Meaning:

```text
Meetings
Incentives
Conferences
Events
```

The card highlights:

- Premium venue sourcing
- Negotiation
- Dedicated MICE coordinator
- AV
- Logistics
- Food & beverage
- Team building
- Incentive programs

CTA:

```text
Enquire Now
```

Currently points to:

```text
get_quote.htm
```

This is an active route.

---

## FIT & GIT Holiday Packages

The page describes:

- FIT itineraries
- Group departures
- Private options
- Semi-private options

CTA currently references:

```text
view_packages.htm
```

### Current status

`view_packages.htm` is **not present in the current repository**.

Treat this as a missing/planned page unless it is added later.

---

## Hotel Accommodation

The page describes:

- 350+ contracted properties
- Luxury to budget options
- B2B negotiated rates

CTA currently references:

```text
browse_hotels.htm
```

### Current status

`browse_hotels.htm` is not currently present.

Do not tell users that hotel browsing is already implemented.

---

## Halong Bay Cruises

The page describes:

- 50+ cruise options
- Luxury overnight cruises
- Day trips
- Private charters

CTA:

```text
explore_cruises.htm
```

### Current status

`explore_cruises.htm` is not currently present.

---

## Transportation Services

The page describes:

- Own fleet
- Airport transfers
- Intercity transfers
- Different vehicle categories

CTA:

```text
check_availability.htm
```

### Current status

`check_availability.htm` is not currently present.

This is a referenced future route, not an implemented page.

---

## Expert Guides

The page describes:

- English-speaking guides
- Multilingual support
- 24/7 ground support
- Local expertise

CTA currently uses:

```html
href="#"
```

This means it is effectively a placeholder.

---

## Contracted Indian Restaurants

The page describes:

- Pure vegetarian options
- Jain menus
- Gujarati menus
- South Indian options
- Group buffets
- Advance booking
- Coverage in Hanoi
- Danang
- Ho Chi Minh City

The CTA currently uses:

```html
href="#"
```

This is also a placeholder.

---

# 19. Visa Services

The services page contains a dedicated dark visa section.

It currently includes service concepts such as:

- Tourist Visa Support
- Invitation Letters
- Express Processing
- Group Visa Handling

The page describes the visa offering as support for Indian travelers and B2B groups.

Important:

The page is currently informational.

There is no visible visa-processing API or database integration in this repository.

---

# 20. Scroll-Reveal Animation

`services.htm` includes a CSS-based reveal system.

The pattern is:

```css
.reveal {
    opacity: 0;
    transform: translateY(28px);
}

.reveal.visible {
    opacity: 1;
    transform: none;
}
```

### Important implementation observation

The CSS defines the `.visible` state, but the current repository does not contain a separate JavaScript scroll observer that clearly applies `.visible`.

Therefore, do not assume the reveal system is fully functional simply because the CSS exists.

If scroll reveal is required, implement it carefully using `IntersectionObserver`.

---

# 21. Responsive Design

Both major content pages contain responsive CSS.

The design adapts for:

```text
Desktop
Tablet
Mobile
```

Typical breakpoints include:

```text
1200px
900px
768px
640px
```

Examples:

- Desktop grids become fewer columns
- Navigation links disappear on smaller screens
- Hero typography reduces
- Wide service cards become single-column
- Statistics become 2-column layouts
- WhatsApp floating button moves inward on mobile

When changing layout, test at least:

```text
1920px+
1440px
1024px
768px
480px
375px
```

---

# 22. WhatsApp Floating Button

The services page contains a floating WhatsApp-style CTA.

It is implemented with CSS and SVG.

Features include:

- Fixed positioning
- Circular button
- Hover scaling
- Tooltip
- Pulse animation

Before modifying it, verify the actual WhatsApp destination/link in the current HTML.

Do not assume that a visual WhatsApp button automatically means the site has a working WhatsApp conversation link.

---

# 23. `get_quote.htm` — Quote Request Workflow

This is the most important interactive page.

It is a B2B quote enquiry form.

---

# 24. Quote Form Fields

The form currently collects:

### Required

```text
Agent Name
Company Name
Email Address
WhatsApp / Phone
Itinerary & Requirements
```

### Optional

```text
Number of Pax
Hotel Category
```

Hotel category options include:

```text
3 Star
4 Star
5 Star
Resort / Boutique
Self Booked
```

The itinerary field asks the agent to provide:

- Travel dates
- Destinations
- Itinerary outline
- Special requests
- Inclusions

---

# 25. Quote Form Validation

The form uses client-side JavaScript.

The following IDs are treated as required:

```javascript
[
  "name",
  "company",
  "email",
  "phone",
  "message"
]
```

The validation logic checks whether each required field contains text.

If a required field is empty:

```text
Border becomes red
↓
Focus/error styling is shown
↓
Submission stops
```

Once the user starts editing the invalid field, the error styling is reset.

---

# 26. EmailJS Integration

The quote form uses EmailJS.

External library:

```text
https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js
```

The page initializes EmailJS in the browser.

The submission flow is:

```text
User clicks Send Quote Request
            ↓
preventDefault()
            ↓
Required-field validation
            ↓
If invalid → stop
            ↓
Disable button
            ↓
Button changes to "Sending…"
            ↓
EmailJS send()
            ↓
Success
      ↙             ↘
Hide form          Show success state
```

If the EmailJS request fails:

```text
Console error
↓
Button re-enabled
↓
Button text restored
↓
Alert displayed
```

---

# 27. Quote Email Payload

The current EmailJS payload maps form fields to:

```javascript
{
    from_name,
    company_name,
    from_email,
    phone,
    pax,
    hotel_cat,
    message
}
```

This mapping is important.

If the EmailJS template is changed, make sure the template variable names remain compatible with these keys.

---

# 28. Quote Success State

The success state is hidden initially.

After successful EmailJS submission:

```javascript
formSec.style.display = "none";
sucSec.style.display = "block";
```

The visitor then sees:

```text
Quote Request Sent
```

with a response-time message.

There is currently no server-side confirmation ID.

There is also no CRM record being created by this repository.

---

# 29. Current Data Architecture

There is currently **no application database**.

The project works primarily like this:

```text
Static HTML
    +
Inline CSS
    +
Small amount of JavaScript
    +
External assets
    +
EmailJS
```

There is no internal data layer such as:

```text
MongoDB
MySQL
PostgreSQL
Firebase
Supabase
```

unless one is introduced later.

---

# 30. External Dependencies

The website currently depends on external resources including:

### Google Fonts

Fonts are loaded from:

```text
fonts.googleapis.com
```

### EmailJS

The quote form uses:

```text
cdn.jsdelivr.net
```

for the EmailJS browser SDK.

### External images

Some hero, destination, logo, and partner images are loaded from external domains such as:

```text
images.unsplash.com
media.tacdn.com
media.istockphoto.com
sembark.com
customer-assets.emergentagent.com
other image/CDN sources
```

### Development consideration

External assets can disappear, change, become rate-limited, or change URLs.

For production stability, important brand assets should eventually be downloaded, optimized, licensed appropriately, and stored locally in the repository or a controlled CDN.

---

# 31. Important Security Note

The current quote page contains a client-side EmailJS public initialization key.

This is normal for EmailJS browser usage, but the project should still be treated as a public frontend.

Never put:

```text
database passwords
private API keys
server credentials
SMTP passwords
admin tokens
```

inside these HTML files.

If a future backend is introduced, secrets must live server-side/environment variables.

---

# 32. Important Current Limitations

Claude/developers should know these limitations before modifying the project.

## 32.1 Missing referenced pages

`services.htm` references pages that do not currently exist:

```text
view_packages.htm
browse_hotels.htm
explore_cruises.htm
check_availability.htm
```

These should be considered **planned/missing routes**.

---

## 32.2 Placeholder links

Some CTAs use:

```html
href="#"
```

These are placeholders.

Do not mistake them for working functionality.

---

## 32.3 Static statistics

Numbers such as:

```text
5000+
350+
50+
15+
98%
```

are hard-coded.

There is no live statistics system.

---

## 32.4 No CMS

Content must currently be edited directly in HTML.

Adding a new destination means modifying the HTML.

---

## 32.5 No database

There is no database-backed:

- Hotel catalogue
- Destination catalogue
- Cruise inventory
- Transport availability
- Agent account system
- Booking system

---

## 32.6 No authentication

There is currently no:

- Agent login
- Admin login
- Partner dashboard
- User account

---

## 32.7 No booking engine

The website currently presents services and collects enquiries.

It is not a complete online booking engine.

---

# 33. Recommended Future Architecture

If the website is expanded significantly, avoid continuously adding everything into one HTML file.

A sensible evolution would be:

```text
Frontend
    ↓
Reusable components
    ↓
API/backend
    ↓
Database
    ↓
Admin/content management
```

Potential future architecture:

```text
React / Next.js
        ↓
REST API / Server Actions
        ↓
Node.js / Supabase / Firebase
        ↓
Database
```

But **do not migrate to a framework merely for the sake of using one**.

For a small brochure-style website, static HTML can remain appropriate.

---

# 34. Suggested Future Data Models

If the project evolves into a real B2B travel platform, likely entities include:

## Destination

```text
id
name
slug
region
description
hero_image
gallery
best_season
highlights
```

## Hotel

```text
id
name
city
category
description
images
amenities
b2b_rate
contact
```

## Cruise

```text
id
name
route
duration
category
starting_price
description
images
```

## Vehicle

```text
id
type
capacity
city
availability
price
```

## Quote Request

```text
id
agent_name
company
email
phone
pax
hotel_category
itinerary
created_at
status
```

---

# 35. Recommended Quote System Evolution

Current:

```text
HTML Form
   ↓
EmailJS
   ↓
Email
```

Possible future:

```text
HTML/React Form
       ↓
Backend API
       ↓
Validation
       ↓
Database
       ↓
CRM
       ↓
Email notification
       ↓
Agent confirmation
```

Eventually the quote system could support:

```text
Quote ID
Agent account
Quote status
Draft quote
Supplier costing
Sales assignment
Operations assignment
Revision history
PDF quotation
Email tracking
CRM integration
```

---

# 36. AI Development Rules

This section is specifically for Claude or another coding assistant.

## Rule 1 — Understand before modifying

Before making changes:

1. Read the relevant HTML file.
2. Identify its existing sections.
3. Identify inline CSS.
4. Identify existing JavaScript.
5. Check links to other pages.
6. Check whether referenced files actually exist.

Do not assume a referenced page exists.

---

## Rule 2 — Do not rewrite the entire website unnecessarily

If asked to change:

```text
one card
one section
one button
one color
one form field
```

make the smallest safe change possible.

Avoid replacing entire files unless requested.

---

## Rule 3 — Preserve existing design language

The design uses:

```text
Luxury hospitality
Wine / maroon
Gold
Cream
Rounded cards
Large editorial headings
Soft shadows
Premium spacing
```

New components should visually belong to this system.

---

## Rule 4 — Preserve existing workflows

Do not break:

```text
index.htm → services.htm
index.htm → get_quote.htm
services.htm → get_quote.htm
quote form → EmailJS
```

when changing navigation or page structure.

---

## Rule 5 — Verify routes

Before creating links such as:

```text
hotel page
cruise page
package page
transport page
```

check whether the target file exists.

If it does not exist, either:

1. create it, or
2. clearly mark the feature as planned.

Never silently create a dead link.

---

## Rule 6 — Preserve EmailJS field names

Unless the EmailJS template is deliberately changed, preserve:

```text
from_name
company_name
from_email
phone
pax
hotel_cat
message
```

Changing these can break the quote email template.

---

## Rule 7 — Avoid unnecessary dependencies

This project currently has almost no dependency overhead.

Do not introduce:

```text
npm
React
Webpack
Vite
large UI libraries
```

unless there is a clear architectural reason.

---

## Rule 8 — Keep mobile compatibility

Every UI change should be checked on:

```text
Desktop
Tablet
Mobile
```

A visually perfect desktop layout that breaks on a phone is not considered complete.

---

# 37. Safe Development Workflow

Use this workflow for future development:

```text
1. Identify requested feature
        ↓
2. Find affected page/file
        ↓
3. Inspect existing HTML/CSS/JS
        ↓
4. Check related links/dependencies
        ↓
5. Make smallest required change
        ↓
6. Test desktop layout
        ↓
7. Test mobile layout
        ↓
8. Test navigation
        ↓
9. Test forms/integrations if affected
        ↓
10. Check console for errors
        ↓
11. Review external assets
        ↓
12. Commit with a clear message
```

---

# 38. Testing Checklist

Before considering a change complete:

## Navigation

- [ ] Home link works
- [ ] Services link works
- [ ] Get Quote link works
- [ ] No new broken links
- [ ] Existing navigation preserved

## Responsive

- [ ] Desktop works
- [ ] Tablet works
- [ ] Mobile works
- [ ] No horizontal overflow
- [ ] Images remain correctly cropped
- [ ] Text does not overlap

## Forms

- [ ] Required validation works
- [ ] Invalid fields show feedback
- [ ] Valid submission reaches EmailJS
- [ ] Loading state works
- [ ] Success state works
- [ ] Failure state restores the button

## Visual

- [ ] Fonts load
- [ ] Images load
- [ ] Cards align correctly
- [ ] Hover states work
- [ ] Buttons are readable
- [ ] Background overlay preserves text contrast

## Code

- [ ] No accidental duplicate elements
- [ ] No missing closing tags
- [ ] No broken IDs
- [ ] No console errors
- [ ] No unnecessary dependencies
- [ ] No secrets added

---

# 39. Current Product Positioning

The website should currently be understood as:

> **A premium B2B DMC marketing and enquiry website for Vietnam travel services.**

It is **not yet**:

- A complete OTA
- A hotel booking engine
- A package booking platform
- A live inventory platform
- A CRM
- A complete travel-management system

This distinction is important when planning future development.

---

# 40. Potential Product Roadmap

A logical roadmap could be:

### Phase 1 — Website Foundation

- Clean existing HTML
- Extract shared CSS
- Extract shared navigation/footer
- Fix broken links
- Optimize images
- Improve accessibility
- Improve SEO

### Phase 2 — Content Architecture

- Destination pages
- Hotel pages
- Cruise pages
- Package pages
- Restaurant pages
- Transport pages
- Visa information pages

### Phase 3 — Quote System

- Backend quote storage
- Quote IDs
- Agent records
- Quote status
- Admin dashboard
- PDF quotation generation

### Phase 4 — B2B Portal

- Agent login
- Saved quotations
- Booking history
- Documents
- Commission information
- Agent-specific rates

### Phase 5 — Operations

- Supplier management
- Hotel availability
- Transport assignment
- Guide assignment
- Booking status
- Operations dashboard

### Phase 6 — Integrations

Possible integrations:

```text
CRM
Email
WhatsApp
Payment gateway
Hotel supplier APIs
Flight APIs
Maps
Analytics
```

Only introduce these when there is a real business requirement.

---

# 41. SEO Considerations

The current pages should eventually receive:

- Unique meta descriptions
- Open Graph tags
- Canonical URLs
- Structured data
- Better semantic headings
- Descriptive image alt text
- Descriptive page titles
- Sitemap
- Robots configuration

Destination pages could target search terms around:

```text
Vietnam DMC
Vietnam B2B DMC
Vietnam tour operator
Vietnam ground handling
Vietnam MICE
Vietnam travel agent services
Vietnam hotel contracting
Vietnam visa assistance
```

SEO copy should remain natural and should not be stuffed with keywords.

---

# 42. Accessibility Improvements

Future development should consider:

- Proper heading hierarchy
- Keyboard navigation
- Visible focus states
- Accessible form labels
- Better color contrast
- Alt text for meaningful images
- Reduced-motion support
- Semantic buttons/links
- ARIA only where genuinely necessary

Do not replace semantic HTML with unnecessary ARIA.

---

# 43. Performance Improvements

The current website relies heavily on external images.

Potential improvements:

```text
Download important images
↓
Compress images
↓
Use WebP/AVIF where appropriate
↓
Add width/height attributes
↓
Lazy-load below-fold images
↓
Reduce oversized images
↓
Minimize repeated CSS
```

The background slideshow should be treated carefully because multiple large full-screen images can be expensive on mobile connections.

---

# 44. Code Quality Improvements

The current site was built rapidly and contains some duplicated/repeated CSS patterns.

Examples include repeated definitions for:

```text
nav
.partner-card
.partner-logo
animation rules
```

Future refactoring should:

1. Consolidate duplicate CSS.
2. Move shared styles into `style.css`.
3. Move JavaScript into `script.js`.
4. Create reusable components if the project becomes larger.
5. Remove dead CSS.
6. Remove placeholder sections that are no longer needed.

Refactoring should be incremental.

Do not combine a visual redesign, framework migration, backend migration, and content rewrite into one uncontrolled change.

---

# 45. Important "Do Not Assume" List

Claude should **not assume** that the following are currently implemented:

```text
❌ Hotel booking
❌ Live hotel availability
❌ Cruise booking
❌ Transport availability
❌ Package browsing
❌ Agent login
❌ CRM
❌ Database
❌ Payment gateway
❌ Admin dashboard
❌ User accounts
❌ Live statistics
❌ Real-time inventory
❌ Automated quotation generation
❌ WhatsApp conversation workflow
❌ Destination detail system
```

These can be future features.

---

# 46. Current Functional Features

The current repository does provide:

```text
✅ Responsive homepage
✅ Premium visual presentation
✅ Vietnam destination showcase
✅ Services showcase
✅ B2B positioning
✅ Partner/certification showcase
✅ Responsive services page
✅ Quote request form
✅ Client-side required-field validation
✅ EmailJS quote submission
✅ Quote success state
✅ CSS animations
✅ Responsive navigation
✅ GitHub-based deployment
```

---

# 47. AI Context Summary

If an AI coding assistant reads only one section, use this one:

```text
PROJECT:
TheVietnamDMC

TYPE:
Static B2B Vietnam DMC marketing + quote enquiry website.

STACK:
HTML5 + CSS3 + Vanilla JavaScript + EmailJS.

MAIN FILES:
index.htm
services.htm
get_quote.htm

ARCHITECTURE:
Static multi-page frontend.
No backend.
No database.

PRIMARY USER:
Travel agents / tour operators / corporate B2B clients.

PRIMARY CTA:
Get Quote.

QUOTE WORKFLOW:
get_quote.htm
→ browser validation
→ EmailJS
→ success state.

DESIGN:
Premium hospitality aesthetic.
Wine/maroon + gold + cream.
Cormorant Garamond + DM Sans.
Rounded cards.
Large editorial headings.
Responsive layouts.

IMPORTANT:
Do not assume referenced pages exist.
Several service CTAs currently point to planned/missing pages.

IMPORTANT FORM KEYS:
from_name
company_name
from_email
phone
pax
hotel_cat
message

DO NOT:
Break EmailJS integration.
Create dead links.
Add unnecessary frameworks.
Expose secrets.
Destroy existing responsive behavior.
Rewrite entire files for small changes.

FUTURE DIRECTION:
The website can evolve into a full B2B DMC platform with destinations, hotels, cruises, transport, quotations, agent accounts, CRM, operations and supplier integrations.
```

---

# 48. Recommended First Improvements

If continuing development, the safest order is:

```text
1. Fix broken/missing service links
2. Extract shared CSS
3. Extract shared navigation/footer
4. Improve mobile navigation
5. Optimize external images
6. Add proper SEO metadata
7. Improve accessibility
8. Build destination detail pages
9. Build hotel catalogue
10. Improve quote management
11. Add backend/database only when required
```

---

# 49. Final Developer Principle

The project should be treated as an evolving B2B travel product rather than just a collection of HTML pages.

Every new feature should answer:

```text
What does the B2B user need?
        ↓
Which page should provide it?
        ↓
What data is required?
        ↓
Is that data static or dynamic?
        ↓
Does the current architecture support it?
        ↓
What existing workflow could be affected?
        ↓
How will the feature work on mobile?
        ↓
How will it be tested?
```

The most important goal is to **extend the existing product without accidentally breaking the current user journey or quote workflow**.

---

## Repository

GitHub:
https://github.com/HELOSIS09/check

Live site:
https://helosis09.github.io/check/

---

## Documentation Status

This README describes the repository based on the current code structure and implementation.

When major architectural changes are made, update this document so that it remains an accurate source of context for future developers and AI coding assistants.
