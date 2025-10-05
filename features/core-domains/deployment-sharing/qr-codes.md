---
title: QR Code Export
version: 1.0
lastUpdated: 2025-01-04
author: Product Team
reviewers: []
status: draft
tags: [deployment, qr-code, physical, offline]
relatedDocuments: [./link-generation.md, ../analytics-insights/engagement-metrics.md]
---

# QR Code Export

## Overview

QR Code Export enables creators to generate scannable QR codes that link to their AI capsules, facilitating offline-to-online transitions. This feature supports print materials, physical locations, and in-person events.

## User Stories

### Story 1: Print Marketing
**As a** real estate agent  
**I want** to generate QR codes for property flyers  
**So that** prospects can instantly access property capsules

### Story 2: Event Distribution
**As a** sales professional  
**I want** QR codes for my booth at trade shows  
**So that** attendees can easily access my product capsule

### Story 3: Branded QR Codes
**As a** business user  
**I want** to customize QR code appearance with my logo  
**So that** codes match my brand identity

## Technical Requirements

### Functional Requirements
- Generate standard QR codes for capsule links
- Support custom QR code branding (logo, colors)
- Provide multiple size options for different use cases
- Enable download in various formats (PNG, SVG, PDF)
- Support high-resolution output for print
- Track scans and conversions from QR codes
- Allow multiple QR codes per capsule with different tracking
- Provide QR code templates for common use cases
- Support dynamic QR codes (update destination without reprinting)

### Non-Functional Requirements
- QR code generation time: < 2 seconds
- Support QR codes up to 4000x4000 pixels
- Scannable from 6 inches to 10 feet distance
- Compatible with all major QR code readers
- Error correction level: Medium to High

## Business Value

QR codes bridge physical and digital experiences, enabling omnichannel marketing strategies and expanding capsule reach beyond digital channels.

## Dependencies

- QR code generation library
- Image processing service
- Link tracking infrastructure
- File export service

## Acceptance Criteria

1. WHEN a QR code is generated THEN it SHALL link to the correct capsule
2. WHEN scanned THEN the QR code SHALL open the capsule within 2 seconds
3. IF branding is applied THEN the QR code SHALL remain scannable
4. WHEN downloaded THEN the file SHALL be in the requested format and resolution
5. WHERE tracking is enabled THEN scans SHALL be recorded in analytics
6. WHEN using dynamic QR codes THEN destination updates SHALL not require reprinting

## Implementation Notes

### QR Code Generation

**Standard QR Code:**
- Black and white
- Square format
- Error correction level M (15% recovery)
- Optimal for maximum scannability

**Branded QR Code:**
- Custom colors (foreground and background)
- Logo in center (up to 30% of code area)
- Rounded corners or custom shapes
- Error correction level H (30% recovery) for logo space

### Size Options

**Print Sizes:**
- Business card (1" x 1")
- Flyer (2" x 2")
- Poster (4" x 4")
- Banner (8" x 8")
- Custom dimensions

**Digital Sizes:**
- Social media (1080x1080px)
- Email signature (200x200px)
- Website (400x400px)
- Custom resolution

### File Formats

**Raster Formats:**
- PNG (transparent background option)
- JPG (for print)
- High-resolution (300 DPI for print)

**Vector Formats:**
- SVG (scalable, best for design tools)
- PDF (print-ready)
- EPS (professional printing)

### QR Code Customization

**Visual Customization:**
- Foreground color
- Background color (or transparent)
- Logo upload (center placement)
- Corner style (square, rounded, dots)
- Pattern style (squares, circles, custom)

**Functional Customization:**
- Error correction level (L, M, Q, H)
- Quiet zone size
- Module size
- Data encoding optimization

### Dynamic QR Codes

**Benefits:**
- Update destination URL without reprinting
- A/B test different capsules
- Redirect to different content based on time/location
- Disable QR codes if needed

**Implementation:**
- QR code points to redirect service
- Redirect service looks up current destination
- Creator can update destination in dashboard
- Tracking maintained through redirect

### QR Code Templates

**Use Case Templates:**
- Property listing (real estate)
- Vehicle showcase (automotive)
- Product demo (sales)
- Event registration
- Contact card
- Menu/catalog

**Template Features:**
- Pre-designed layout with QR code
- Customizable text and images
- Brand color application
- Print-ready output

### Tracking & Analytics

**Scan Metrics:**
- Total scans
- Unique scans
- Scan location (if available)
- Scan time and date
- Device type
- Conversion rate

**Attribution:**
- Track which QR code drove the scan
- Campaign association
- Physical location tracking
- ROI calculation

### QR Code Generator Interface

**Configuration Steps:**
1. Select capsule to link
2. Choose QR code style (standard or branded)
3. Customize appearance
4. Select size and format
5. Preview QR code
6. Test scan with phone
7. Download file

**Bulk Generation:**
- Create multiple QR codes at once
- Different tracking parameters per code
- Batch download
- CSV import for campaign codes

### Best Practices Guide

**Scannability:**
- Minimum size: 1" x 1" for close viewing
- Contrast ratio: 3:1 minimum
- Quiet zone: 4 modules minimum
- Test scan before printing

**Placement:**
- Eye level when possible
- Good lighting
- Flat surface (avoid curves)
- Clear call-to-action ("Scan to learn more")

**Design:**
- Keep branding subtle (logo < 30%)
- High contrast colors
- Avoid gradients in QR area
- Test with multiple devices

## Related Features

- [Smart Link Generation](./link-generation.md): Provides URLs for QR codes
- [Engagement Metrics](../analytics-insights/engagement-metrics.md): Tracks QR code scans
- [Brand Styling](../capsule-creation/brand-styling.md): Branding for QR codes
