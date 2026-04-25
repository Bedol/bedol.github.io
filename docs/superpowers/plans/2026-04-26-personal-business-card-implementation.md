# Personal Business Card Site - Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transform Jekyll blog into personal business card site for Ruby contractor acquisition.

**Architecture:** Single-page layout with full-viewport hero section followed by 3-column card grid. Override minima theme's default home layout and styles.

**Tech Stack:** Jekyll 4.4.1, minima 2.5 theme, native CSS (no additional frameworks)

---

## File Structure

```
├── _layouts/
│   └── home.html          # Override minima home layout
├── assets/
│   └── main.scss          # Custom styles (imported by minima)
├── index.markdown         # Modify: update front matter
├── _config.yml            # Modify: update site description
├── _includes/
│   └── custom/
│       ├── header.html    # Create: minimal header (no nav)
│       └── social.html   # Create: social icons component
└── docs/superpowers/plans/YYYY-MM-DD-*.md
```

---

## Task 1: Create Custom Header Include

**Files:**
- Create: `_includes/custom/header.html`

- [ ] **Step 1: Create directory**

```bash
mkdir -p _includes/custom
```

- [ ] **Step 2: Create header.html**

```html
<header class="site-header">
  <div class="wrapper">
    <a class="site-title" href="{{ "/" | relative_url }}">{{ site.title | escape }}</a>
  </div>
</header>
```

- [ ] **Step 3: Commit**

```bash
git add _includes/custom/header.html
git commit -m "feat: add minimal header include"
```

---

## Task 2: Create Social Icons Include

**Files:**
- Create: `_includes/custom/social.html`

- [ ] **Step 1: Create social.html with SVG icons**

```html
{% if site.github_username %}
<a href="https://github.com/{{ site.github_username }}" class="social-link" aria-label="GitHub">
  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
  </svg>
</a>
{% endif %}
{% if site.linkedin_username %}
<a href="https://linkedin.com/in/{{ site.linkedin_username }}" class="social-link" aria-label="LinkedIn">
  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
    <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
  </svg>
</a>
{% endif %}
```

- [ ] **Step 2: Commit**

```bash
git add _includes/custom/social.html
git commit -m "feat: add social icons include with SVG"
```

---

## Task 3: Create Custom Home Layout

**Files:**
- Create: `_layouts/home.html`

- [ ] **Step 1: Create home.html layout**

```html
<!DOCTYPE html>
<html>
{% include head.html %}
<body>
  {% include custom/header.html %}
  
  <main id="main" role="main">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <h1 class="hero-name">{{ site.title | escape }}</h1>
        <p class="hero-tagline">Senior Ruby Developer | Building robust web applications since 2015</p>
        <div class="hero-actions">
          <a href="mailto:{{ site.email }}" class="btn btn-primary">Let's Talk</a>
          {% include custom/social.html %}
        </div>
      </div>
    </section>

    <!-- Cards Section -->
    <section class="cards-section">
      <div class="cards-grid">
        <!-- Expertise Card -->
        <div class="card">
          <div class="card-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="16 18 22 12 16 6"></polyline>
              <polyline points="8 6 2 12 8 18"></polyline>
            </svg>
          </div>
          <h2 class="card-title">What I Do</h2>
          <div class="skill-tags">
            <span class="skill-tag">Ruby</span>
            <span class="skill-tag">Rails</span>
            <span class="skill-tag">PostgreSQL</span>
            <span class="skill-tag">Redis</span>
            <span class="skill-tag">Sidekiq</span>
            <span class="skill-tag">Docker</span>
            <span class="skill-tag">JavaScript</span>
            <span class="skill-tag">TypeScript</span>
            <span class="skill-tag">AWS</span>
          </div>
        </div>

        <!-- Experience Card -->
        <div class="card">
          <div class="card-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect>
              <path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path>
            </svg>
          </div>
          <h2 class="card-title">Where I've Worked</h2>
          <div class="timeline">
            <div class="timeline-item">
              <span class="timeline-company">Semrush</span>
              <span class="timeline-role">Senior Backend Developer</span>
              <span class="timeline-dates">2026 – Present</span>
              <span class="timeline-desc">Media Database</span>
            </div>
            <div class="timeline-item">
              <span class="timeline-company">Prowly</span>
              <span class="timeline-role">Ruby Developer</span>
              <span class="timeline-dates">2023 – 2026</span>
              <span class="timeline-desc">PR reporting, email delivery</span>
            </div>
            <div class="timeline-item">
              <span class="timeline-company">GetResponse</span>
              <span class="timeline-role">Junior → Ruby Developer</span>
              <span class="timeline-dates">2015 – 2023</span>
              <span class="timeline-desc">Payment processing, affiliate programs</span>
            </div>
          </div>
        </div>

        <!-- Contact Card -->
        <div class="card">
          <div class="card-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
              <polyline points="22,6 12,13 2,6"></polyline>
            </svg>
          </div>
          <h2 class="card-title">Get In Touch</h2>
          <p class="contact-email">
            <a href="mailto:{{ site.email }}">{{ site.email }}</a>
          </p>
          <p class="contact-subtext">Open to contract work and consulting</p>
          <a href="mailto:{{ site.email }}" class="btn btn-secondary">Email Me</a>
        </div>
      </div>
    </section>
  </main>

  {% include footer.html %}
</body>
</html>
```

- [ ] **Step 2: Commit**

```bash
git add _layouts/home.html
git commit -m "feat: create custom home layout with hero and cards"
```

---

## Task 4: Create Custom SCSS Styles

**Files:**
- Create: `assets/main.scss`

- [ ] **Step 1: Create main.scss**

```scss
---
---

@import "minima/skins/classic";

.site-header {
  padding: 1rem 0;
  position: absolute;
  width: 100%;
  z-index: 10;
}

.site-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: #fff;
  text-decoration: none;
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  color: #fff;
  text-align: center;
  padding: 2rem;
  animation: fadeIn 1s ease-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.hero-content {
  max-width: 800px;
}

.hero-name {
  font-size: clamp(2.5rem, 8vw, 4.5rem);
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: -0.02em;
}

.hero-tagline {
  font-size: clamp(1.1rem, 3vw, 1.5rem);
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 2rem;
}

.hero-actions {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.btn {
  display: inline-block;
  padding: 0.875rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: transform 0.2s, box-shadow 0.2s;
}

.btn-primary {
  background: #e94560;
  color: #fff;
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 20px rgba(233, 69, 96, 0.4);
  }
}

.btn-secondary {
  background: transparent;
  color: #e94560;
  border: 2px solid #e94560;
  &:hover {
    background: #e94560;
    color: #fff;
  }
}

.social-link {
  color: rgba(255, 255, 255, 0.7);
  transition: color 0.2s, transform 0.2s;
  display: inline-block;
  &:hover {
    color: #fff;
    transform: scale(1.1);
  }
  svg {
    width: 28px;
    height: 28px;
  }
}

.cards-section {
  padding: 4rem 2rem;
  background: #f8f9fa;
}

.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.card {
  background: #fff;
  border-radius: 16px;
  padding: 2rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s, box-shadow 0.3s;
  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1);
  }
}

.card-icon {
  color: #e94560;
  margin-bottom: 1rem;
}

.card-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: #1a1a2e;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.skill-tag {
  background: #f1f3f5;
  color: #495057;
  padding: 0.5rem 1rem;
  border-radius: 50px;
  font-size: 0.9rem;
  font-weight: 500;
  transition: background 0.2s, color 0.2s;
  &:hover {
    background: #e94560;
    color: #fff;
  }
}

.timeline {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.timeline-item {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.timeline-company {
  font-weight: 700;
  color: #1a1a2e;
  font-size: 1.1rem;
}

.timeline-role {
  color: #495057;
  font-size: 0.95rem;
}

.timeline-dates {
  color: #868e96;
  font-size: 0.85rem;
}

.timeline-desc {
  color: #adb5bd;
  font-size: 0.85rem;
  font-style: italic;
}

.contact-email {
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
  a {
    color: #e94560;
    text-decoration: none;
    &:hover { text-decoration: underline; }
  }
}

.contact-subtext {
  color: #868e96;
  margin-bottom: 1.5rem;
}

@media (max-width: 768px) {
  .hero {
    min-height: auto;
    padding: 6rem 1.5rem 4rem;
  }
  
  .cards-section {
    padding: 2rem 1rem;
  }
  
  .cards-grid {
    grid-template-columns: 1fr;
  }
}
```

- [ ] **Step 2: Commit**

```bash
git add assets/main.scss
git commit -m "feat: add custom styles for business card layout"
```

---

## Task 5: Update index.markdown

**Files:**
- Modify: `index.markdown`

- [ ] **Step 1: Update index.markdown**

```markdown
---
layout: home
---
```

- [ ] **Step 2: Commit**

```bash
git add index.markdown
git commit -m "chore: update index to use home layout"
```

---

## Task 6: Update _config.yml

**Files:**
- Modify: `_config.yml`

- [ ] **Step 1: Update site description and add linkedin_username**

Replace the description in _config.yml with:

```yaml
description: >-
  Senior Ruby Developer specializing in building robust web applications.
  Open to contract work and consulting.
linkedin_username: bweber-dev
github_username: bedol
```

- [ ] **Step 2: Commit**

```bash
git add _config.yml
git commit -m "chore: update site description and add social usernames"
```

---

## Task 7: Remove Blog Navigation (Optional)

**Files:**
- Modify: `_config.yml`

If minima shows blog/posts in header, we may need to add header navigation override. For now, the custom header in Task 1 is minimal (no nav links).

---

## Verification

- [ ] Run `bundle exec jekyll serve` and verify site loads
- [ ] Check hero section displays correctly with name, tagline, CTA
- [ ] Verify 3 cards render in grid layout
- [ ] Test social icons link to correct profiles
- [ ] Test email links open mailto composer
- [ ] Verify responsive layout on mobile (cards stack)
- [ ] Check animations (fade-in on hero, hover on cards/tags)

---

## Success Criteria Checklist

- [ ] Visitor immediately understands who you are and what you do
- [ ] Contact information is one click away
- [ ] Technical skills and experience are scannable in <10 seconds
- [ ] Site works well on mobile during client meetings
