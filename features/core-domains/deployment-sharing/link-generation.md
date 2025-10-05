---
title: Smart Link Generation
version: 1.0
lastUpdated: 2025-01-04
author: Product Team
reviewers: []
status: draft
tags: [deployment, sharing, links, tracking]
relatedDocuments: [./embedding.md, ./qr-codes.md, ../analytics-insights/engagement-metrics.md]
---

# Smart Link Generation

## Overview

Smart Link Generation creates unique, trackable URLs for AI capsules with customization options for branding, access control, and analytics tracking. This feature enables creators to share capsules across channels while maintaining attribution and control.

## User Stories

### Story 1: Custom Branded Links
**As a** business user  
**I want** to create custom-branded capsule URLs  
**So that** links look professional and trustworthy

### Story 2: Campaign Tracking
**As a** marketing professional  
**I want** to create different links for different campaigns  
**So that** I can track which channels drive the most engagement

### Story 3: Access Control
**As a** enterprise user  
**I want** to create password-protected links  
**So that** I can control who accesses sensitive capsules

## Technical Requirements

### Functional Requirements
- Generate unique, short URLs for each capsule
- Support custom domains for branded links
- Enable URL customization (custom slugs)
- Provide link expiration options
- Support password protection
- Enable access limits (max views, max users)
- Track link performance (clicks, conversions)
- Support UTM parameters for campaign tracking
- Allow multiple links per capsule with different settings
- Provide link management dashboard

### Non-Functional Requirements
- Link generation time: < 1 second
- Link redirect latency: < 200ms
- Support 10,000+ active links per account
- 99.99% link availability
- Secure link generation (prevent guessing)

## Business Value

Professional, trackable links increase click-through rates and enable precise attribution, helping creators optimize distribution strategies and demonstrate ROI.

## Dependencies

- URL shortening service
- Custom domain management
- Access control system
- Analytics tracking infrastructure

## Acceptance Criteria

1. WHEN a capsule is published THEN the system SHALL generate a unique shareable link
2. WHEN a custom slug is requested THEN the system SHALL validate availability and create it
3. IF a link has expiration set THEN access SHALL be denied after expiration
4. WHEN a password is set THEN users SHALL be prompted before accessing the capsule
5. WHERE access limits are reached THEN the system SHALL block further access
6. WHEN viewing link analytics THEN the creator SHALL see clicks, views, and conversions

## Implementation Notes

### Link Structure

**Standard Link:**
```
https://encaptio.com/c/[unique-id]
```

**Custom Slug:**
```
https://encaptio.com/c/[custom-slug]
```

**Custom Domain:**
```
https://capsules.yourbrand.com/[slug]
```

### Link Configuration Options

**Branding:**
- Custom slug (e.g., /property-123-main-st)
- Custom domain (Enterprise tier)
- Branded preview cards (Open Graph tags)

**Access Control:**
- Public (anyone with link)
- Password-protected
- Email-gated (collect email before access)
- IP-restricted (Enterprise tier)
- Time-limited (expires after date/time)
- View-limited (max N views)

**Tracking:**
- UTM parameters (source, medium, campaign)
- Custom tracking parameters
- Referrer tracking
- Device and location tracking

**Behavior:**
- Direct to capsule (default)
- Show preview page first
- Redirect after conversation
- Custom welcome message per link

### Link Management Dashboard

**Link List:**
- All links for a capsule
- Link performance summary
- Status (active, expired, limit reached)
- Creation date and creator
- Quick actions (copy, edit, delete)

**Link Analytics:**
- Clicks vs. views (click-through rate)
- Geographic distribution
- Device breakdown
- Traffic sources
- Conversion rate per link

**Bulk Operations:**
- Create multiple links with templates
- Bulk expiration updates
- Export link list
- Archive old links

### Security Considerations

**Link Generation:**
- Use cryptographically secure random IDs
- Prevent enumeration attacks
- Rate limit link creation
- Validate custom slugs for abuse

**Access Control:**
- Secure password hashing
- Rate limit password attempts
- Session management for authenticated access
- Audit log for access attempts

### Custom Domain Setup

**Domain Configuration:**
1. User adds custom domain in settings
2. System provides DNS records (CNAME)
3. User configures DNS
4. System verifies domain ownership
5. SSL certificate provisioned automatically
6. Custom domain activated

**Domain Management:**
- Multiple domains per account (Enterprise)
- Default domain selection
- Domain-specific analytics
- SSL certificate renewal

## Related Features

- [Embeddable Widget](./embedding.md): Alternative distribution method
- [QR Code Export](./qr-codes.md): Physical link distribution
- [Engagement Metrics](../analytics-insights/engagement-metrics.md): Link performance tracking
