---
title: Internationalization (i18n)
version: 1.0
lastUpdated: 2025-01-04
author: Product Team
reviewers: []
status: draft
tags: [cross-cutting, i18n, localization, multilingual]
relatedDocuments: [./responsive-design.md, ./accessibility.md]
---

# Internationalization (i18n)

## Overview

Internationalization enables Encaptio/Encapsify to support multiple languages, regions, and cultures. This cross-cutting feature provides multilingual interfaces, localized content, cultural adaptations, and global accessibility.

## User Stories

### Story 1: Language Selection
**As an** international user  
**I want** to use the platform in my native language  
**So that** I can understand and use all features

### Story 2: Localized Content
**As a** global business  
**I want** to create capsules in multiple languages  
**So that** I can reach international audiences

### Story 3: Cultural Adaptation
**As a** user from a different culture  
**I want** dates, numbers, and formats to match my locale  
**So that** information is presented familiarly

## Technical Requirements

### Functional Requirements

**Language Support:**
- Multiple UI languages
- Content translation
- Language detection
- Language switching
- RTL (right-to-left) support
- Fallback languages

**Localization:**
- Date/time formatting
- Number formatting
- Currency formatting
- Address formats
- Name formats
- Measurement units

**Cultural Adaptation:**
- Cultural norms
- Color meanings
- Imagery appropriateness
- Idioms and expressions
- Legal requirements

### Non-Functional Requirements
- Language switch: < 1 second
- Translation coverage: 95%+
- RTL layout: Fully supported
- Character encoding: UTF-8
- Font support: All languages

## Business Value

Internationalization expands global market reach, improves user experience for non-English speakers, enables compliance with local regulations, and demonstrates cultural sensitivity.

## Dependencies

- Translation management system
- Localization libraries (i18next, react-intl)
- Translation services
- Font libraries
- Locale data (CLDR)

## Acceptance Criteria

1. WHEN selecting a language THEN UI SHALL display in that language
2. WHEN content is multilingual THEN appropriate version SHALL display
3. IF language is RTL THEN layout SHALL mirror correctly
4. WHEN formatting dates THEN locale format SHALL be used
5. WHERE translations missing THEN fallback SHALL display
6. WHEN detecting language THEN user preference SHALL be respected

## Implementation Notes

### Supported Languages

**Phase 1 (Launch):**
- English (en-US, en-GB)
- Spanish (es-ES, es-MX)
- French (fr-FR)
- German (de-DE)
- Portuguese (pt-BR)

**Phase 2 (Expansion):**
- Chinese (zh-CN, zh-TW)
- Japanese (ja-JP)
- Korean (ko-KR)
- Italian (it-IT)
- Dutch (nl-NL)

**Phase 3 (Global):**
- Arabic (ar-SA)
- Russian (ru-RU)
- Hindi (hi-IN)
- Turkish (tr-TR)
- Polish (pl-PL)
- And more...

### Translation Architecture

**Translation Keys:**
```json
{
  "common": {
    "save": "Save",
    "cancel": "Cancel",
    "delete": "Delete",
    "edit": "Edit"
  },
  "capsule": {
    "create": "Create Capsule",
    "title": "Capsule Title",
    "description": "Description"
  },
  "errors": {
    "required": "This field is required",
    "invalid_email": "Please enter a valid email"
  }
}
```

**Usage in Code:**
```javascript
import { useTranslation } from 'react-i18next';

function Component() {
  const { t } = useTranslation();
  
  return (
    <div>
      <h1>{t('capsule.create')}</h1>
      <button>{t('common.save')}</button>
    </div>
  );
}
```

**Pluralization:**
```json
{
  "items": {
    "zero": "No items",
    "one": "{{count}} item",
    "other": "{{count}} items"
  }
}
```

**Interpolation:**
```json
{
  "welcome": "Welcome, {{name}}!",
  "views": "{{count}} views in the last {{days}} days"
}
```

### Language Detection

**Detection Priority:**
1. User's saved preference
2. URL parameter (?lang=es)
3. Browser language setting
4. IP-based geolocation
5. Default language (English)

**Implementation:**
```javascript
function detectLanguage() {
  // 1. Check user preference
  const userLang = getUserPreference();
  if (userLang) return userLang;
  
  // 2. Check URL parameter
  const urlLang = new URLSearchParams(window.location.search).get('lang');
  if (urlLang && supportedLanguages.includes(urlLang)) return urlLang;
  
  // 3. Check browser language
  const browserLang = navigator.language || navigator.userLanguage;
  const matchedLang = findBestMatch(browserLang, supportedLanguages);
  if (matchedLang) return matchedLang;
  
  // 4. Check geolocation
  const geoLang = await getLanguageFromIP();
  if (geoLang) return geoLang;
  
  // 5. Default
  return 'en-US';
}
```

### RTL (Right-to-Left) Support

**RTL Languages:**
- Arabic (ar)
- Hebrew (he)
- Persian (fa)
- Urdu (ur)

**CSS Implementation:**
```css
/* Logical properties for RTL support */
.container {
  margin-inline-start: 1rem; /* margin-left in LTR, margin-right in RTL */
  padding-inline-end: 2rem;  /* padding-right in LTR, padding-left in RTL */
}

/* Direction-specific styles */
[dir="rtl"] .icon {
  transform: scaleX(-1); /* Mirror icons */
}

[dir="rtl"] .text-align-start {
  text-align: right;
}
```

**HTML Direction:**
```html
<html lang="ar" dir="rtl">
  <body>
    <!-- Content flows right to left -->
  </body>
</html>
```

### Localization Formats

**Date and Time:**
```javascript
// Using Intl API
const date = new Date();

// US English: 1/4/2025
new Intl.DateTimeFormat('en-US').format(date);

// British English: 04/01/2025
new Intl.DateTimeFormat('en-GB').format(date);

// German: 04.01.2025
new Intl.DateTimeFormat('de-DE').format(date);

// Japanese: 2025/1/4
new Intl.DateTimeFormat('ja-JP').format(date);

// Relative time
new Intl.RelativeTimeFormat('en', { numeric: 'auto' })
  .format(-1, 'day'); // "yesterday"
```

**Numbers:**
```javascript
const number = 1234567.89;

// US: 1,234,567.89
new Intl.NumberFormat('en-US').format(number);

// German: 1.234.567,89
new Intl.NumberFormat('de-DE').format(number);

// French: 1 234 567,89
new Intl.NumberFormat('fr-FR').format(number);
```

**Currency:**
```javascript
const amount = 1234.56;

// USD: $1,234.56
new Intl.NumberFormat('en-US', {
  style: 'currency',
  currency: 'USD'
}).format(amount);

// EUR: 1.234,56 €
new Intl.NumberFormat('de-DE', {
  style: 'currency',
  currency: 'EUR'
}).format(amount);

// JPY: ¥1,235
new Intl.NumberFormat('ja-JP', {
  style: 'currency',
  currency: 'JPY'
}).format(amount);
```

### Content Translation

**AI Content Translation:**
- Automatic translation of capsule content
- Maintain formatting and structure
- Preserve links and media
- Quality assurance
- Human review option (premium)

**Translation Workflow:**
1. Creator uploads content in source language
2. System detects language
3. AI translates to target languages
4. Translations stored separately
5. User selects language
6. Appropriate version displayed

**Translation Quality:**
- Machine translation (automatic)
- Professional translation (premium)
- Community translation (crowdsourced)
- Hybrid approach

### Cultural Considerations

**Colors:**
- Red: Danger (Western), Luck (Chinese), Purity (Indian)
- White: Purity (Western), Mourning (Eastern)
- Green: Nature (Western), Sacred (Islamic)

**Images:**
- Avoid culturally insensitive imagery
- Use diverse representation
- Consider religious sensitivities
- Respect cultural norms

**Text:**
- Avoid idioms that don't translate
- Be mindful of formality levels
- Consider reading direction
- Respect naming conventions

**Dates and Calendars:**
- Gregorian calendar (most common)
- Islamic calendar
- Hebrew calendar
- Chinese calendar
- Buddhist calendar

### Font Support

**Web Fonts:**
```css
/* Latin scripts */
@font-face {
  font-family: 'Inter';
  src: url('/fonts/inter.woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153;
}

/* Cyrillic */
@font-face {
  font-family: 'Inter';
  src: url('/fonts/inter-cyrillic.woff2');
  unicode-range: U+0400-045F, U+0490-0491;
}

/* Arabic */
@font-face {
  font-family: 'Noto Sans Arabic';
  src: url('/fonts/noto-arabic.woff2');
  unicode-range: U+0600-06FF;
}

/* CJK (Chinese, Japanese, Korean) */
@font-face {
  font-family: 'Noto Sans CJK';
  src: url('/fonts/noto-cjk.woff2');
  unicode-range: U+4E00-9FFF;
}
```

### Translation Management

**Translation Workflow:**
1. Developers add translation keys
2. Keys extracted to translation files
3. Translators translate strings
4. Translations reviewed
5. Translations deployed
6. Continuous updates

**Translation Tools:**
- Crowdin
- Lokalise
- Phrase
- POEditor
- Custom TMS

**Quality Assurance:**
- Context screenshots
- Character limits
- Placeholder validation
- Consistency checks
- Native speaker review

### Testing Strategy

**Localization Testing:**
- Visual testing in all languages
- RTL layout testing
- Date/time format testing
- Number format testing
- Currency display testing
- Text expansion testing (German, Finnish)
- Text contraction testing (Chinese, Japanese)

**Pseudo-localization:**
```
Original: "Save changes"
Pseudo: "[!!! Šàvé çhàñgéš !!!]"
```
- Tests text expansion
- Identifies hard-coded strings
- Reveals layout issues
- Validates character encoding

## Related Features

- [Responsive Design](./responsive-design.md): Responsive multilingual layouts
- [Accessibility](./accessibility.md): Accessible multilingual content
- [AI Interaction](../core-domains/ai-interaction/README.md): Multilingual AI responses
