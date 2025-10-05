---
title: Embeddable Widget
version: 1.0
lastUpdated: 2025-01-04
author: Product Team
reviewers: []
status: draft
tags: [deployment, embedding, widget, integration]
relatedDocuments: [./link-generation.md, ../capsule-creation/brand-styling.md]
---

# Embeddable Widget

## Overview

Embeddable Widget enables creators to integrate AI capsules directly into their websites, landing pages, or applications using a simple embed code. This feature allows seamless capsule experiences without redirecting users to external pages.

## User Stories

### Story 1: Website Integration
**As a** business owner  
**I want** to embed my capsule on my website  
**So that** visitors can interact without leaving my site

### Story 2: Landing Page Enhancement
**As a** marketer  
**I want** to add an interactive capsule to my landing page  
**So that** I can increase engagement and conversions

### Story 3: Customizable Appearance
**As a** web developer  
**I want** to customize the embedded capsule's size and appearance  
**So that** it matches my website design

## Technical Requirements

### Functional Requirements
- Generate embed code (iframe or JavaScript widget)
- Support multiple embed formats (inline, popup, chat bubble)
- Allow size customization (width, height, responsive)
- Enable appearance customization (colors, position)
- Support lazy loading for performance
- Provide API for programmatic control
- Enable cross-domain communication
- Support mobile-responsive embedding
- Allow multiple capsules per page
- Provide embed preview before implementation

### Non-Functional Requirements
- Widget load time: < 1 second
- Minimal impact on host page performance (< 100KB)
- Cross-browser compatibility (Chrome, Firefox, Safari, Edge)
- Mobile-friendly and touch-optimized
- Secure iframe sandboxing
- GDPR-compliant tracking in embedded context

## Business Value

Embedded capsules reduce friction by keeping users on the creator's site, improving conversion rates and maintaining brand control throughout the user journey.

## Dependencies

- CDN for widget delivery
- Iframe security infrastructure
- Cross-domain messaging system
- Responsive design framework

## Acceptance Criteria

1. WHEN embed code is generated THEN it SHALL work on any website
2. WHEN a capsule is embedded THEN it SHALL load within 1 second
3. IF the host page is mobile THEN the widget SHALL adapt responsively
4. WHEN multiple capsules are embedded THEN they SHALL not conflict
5. WHERE appearance is customized THEN changes SHALL apply without code modification
6. WHEN a user interacts THEN analytics SHALL track the embedded context

## Implementation Notes

### Embed Formats

**Inline Embed:**
```html
<iframe src="https://encaptio.com/embed/[capsule-id]" 
        width="100%" 
        height="600px" 
        frameborder="0">
</iframe>
```

**JavaScript Widget:**
```html
<div id="encaptio-widget"></div>
<script src="https://cdn.encaptio.com/widget.js"></script>
<script>
  Encaptio.init({
    capsuleId: '[capsule-id]',
    container: '#encaptio-widget',
    mode: 'inline', // or 'popup', 'bubble'
    width: '100%',
    height: '600px'
  });
</script>
```

**Chat Bubble:**
```html
<script src="https://cdn.encaptio.com/bubble.js"></script>
<script>
  Encaptio.bubble({
    capsuleId: '[capsule-id]',
    position: 'bottom-right',
    color: '#0066cc'
  });
</script>
```

### Embed Modes

**Inline Mode:**
- Embedded directly in page content
- Fixed or responsive dimensions
- Scrollable content area
- Best for dedicated sections

**Popup Mode:**
- Triggered by button or link
- Modal overlay
- Centered on screen
- Dismissible by user
- Best for on-demand access

**Chat Bubble Mode:**
- Floating button in corner
- Expands to chat interface
- Minimizable
- Persistent across pages
- Best for ongoing support

### Customization Options

**Appearance:**
- Width and height (fixed or percentage)
- Border radius and shadow
- Primary color theme
- Font family override
- Custom CSS (Enterprise tier)

**Behavior:**
- Auto-open on page load
- Trigger on scroll depth
- Trigger on time delay
- Trigger on exit intent
- Remember minimized state

**Position (for bubble mode):**
- Bottom-right (default)
- Bottom-left
- Top-right
- Top-left
- Custom offset

### Embed Code Generator

**Configuration Interface:**
1. Select embed mode (inline, popup, bubble)
2. Customize appearance
3. Set behavior triggers
4. Preview embed
5. Copy generated code
6. View implementation instructions

**Generated Code Includes:**
- Embed script/iframe
- Configuration options
- Fallback content
- Analytics tracking
- Privacy compliance

### Performance Optimization

**Lazy Loading:**
- Load widget only when visible
- Defer non-critical resources
- Progressive enhancement

**Resource Optimization:**
- Minified JavaScript
- Compressed assets
- CDN delivery
- Browser caching
- Async loading

**Host Page Impact:**
- Minimal DOM manipulation
- No global namespace pollution
- Isolated CSS (shadow DOM or scoped)
- Efficient event handling

### Security Considerations

**Iframe Sandboxing:**
```html
<iframe sandbox="allow-scripts allow-same-origin allow-forms">
```

**Content Security Policy:**
- Restrict allowed origins
- Prevent clickjacking
- XSS protection

**Cross-Domain Communication:**
- PostMessage API for secure messaging
- Origin validation
- Message sanitization

### API for Programmatic Control

```javascript
// Initialize widget
const widget = Encaptio.init({ capsuleId: 'xxx' });

// Control methods
widget.open();
widget.close();
widget.minimize();
widget.maximize();

// Event listeners
widget.on('open', () => {});
widget.on('close', () => {});
widget.on('message', (data) => {});
widget.on('conversion', (data) => {});

// Update configuration
widget.setConfig({ color: '#ff0000' });
```

## Related Features

- [Smart Link Generation](./link-generation.md): Alternative distribution method
- [Brand Styling](../capsule-creation/brand-styling.md): Appearance customization
- [Engagement Metrics](../analytics-insights/engagement-metrics.md): Embedded analytics
