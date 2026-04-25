# Personal Business Card Site - Design Spec

## Overview

Transform the existing Jekyll blog into a personal business card site focused on landing Ruby programming contracts. The site communicates expertise, experience, and contact information to potential clients.

## Design Style

- Modern/creative with subtle animations
- Dark gradient hero section for memorable first impression
- Clean card-based layout for information hierarchy
- English only

## Layout Structure

```
┌─────────────────────────────────────────────┐
│                  HERO                        │
│   Bartłomiej Weber                           │
│   Senior Ruby Developer | Building robust   │
│   web applications since 2015                │
│   [Let's Talk] [GitHub] [LinkedIn]          │
└─────────────────────────────────────────────┘
          ↓ scroll
┌─────────────────────────────────────────────┐
│  ┌─────────┐ ┌─────────┐ ┌─────────┐        │
│  │EXPERTISE│ │EXPERIENCE│ │CONTACT │        │
│  └─────────┘ └─────────┘ └─────────┘        │
└─────────────────────────────────────────────┘
```

## Sections

### 1. Hero Section

- **Background**: Dark gradient (#1a1a2e to #16213e)
- **Content**:
  - Name: "Bartłomiej Weber" (large, bold, white)
  - Tagline: "Senior Ruby Developer | Building robust web applications since 2015"
  - CTA button: "Let's Talk" → mailto link
  - Social icons: GitHub, LinkedIn (clickable)
- **Height**: Full viewport on desktop, auto on mobile
- **Animation**: Subtle fade-in on load

### 2. Expertise Card

- **Icon**: Code symbol
- **Title**: "What I Do"
- **Content**: Pill-style tags for skills
  - Ruby, Rails, PostgreSQL, Redis, Sidekiq, Docker, JavaScript, TypeScript, AWS
- **Layout**: Flex wrap, centered

### 3. Experience Card

- **Icon**: Briefcase
- **Title**: "Where I've Worked"
- **Content**: Condensed timeline
  - **Semrush** (2026–Present) - Senior Backend Developer
    - Media Database
  - **Prowly** (2023–2026) - Ruby Developer
    - PR reporting area, email message delivery
  - **GetResponse** (2015–2023) - Junior → Ruby Developer
    - Payment processing, affiliate programs
- **Project types**: Payment systems, APIs, DevOps, email delivery

### 4. Contact Card

- **Icon**: Mail
- **Title**: "Get In Touch"
- **Content**:
  - Email: bartlomiej.weber@bweber.dev (clickable mailto)
  - Subtext: "Open to contract work and consulting"
  - CTA button: "Email Me"

## Responsive Behavior

- Desktop: 3-column card grid
- Tablet: 2-column grid
- Mobile: Single column stack

## Implementation Notes

- Use minima theme as base, override layouts as needed
- Remove `_posts/` from navigation (archive, not primary focus)
- Keep about page as secondary reference
- Minimal animations (CSS only, no heavy JS)

## Success Criteria

1. Visitor immediately understands who you are and what you do
2. Contact information is one click away
3. Technical skills and experience are scannable in <10 seconds
4. Site works well on mobile during client meetings
