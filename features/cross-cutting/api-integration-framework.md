---
title: API & Integration Framework
version: 1.0
lastUpdated: 2025-01-04
author: Product Team
reviewers: []
status: draft
tags: [cross-cutting, api, integration, webhooks, sdk]
relatedDocuments: [./system-architecture.md, ./security-authentication.md]
---

# API & Integration Framework

## Overview

The API & Integration Framework provides comprehensive programmatic access to Encaptio/Encapsify platform capabilities. This cross-cutting feature enables third-party integrations, custom applications, automation, and extensibility through REST APIs, GraphQL, webhooks, and SDKs.

## User Stories

### Story 1: API Access
**As a** developer  
**I want** programmatic access to platform features  
**So that** I can build custom integrations

### Story 2: Webhook Notifications
**As a** business user  
**I want** real-time notifications of capsule events  
**So that** I can trigger automated workflows

### Story 3: SDK Usage
**As a** developer  
**I want** SDKs in my preferred language  
**So that** I can integrate quickly and easily

## Technical Requirements

### Functional Requirements

**REST API:**
- RESTful endpoints for all resources
- JSON request/response format
- Pagination support
- Filtering and sorting
- Batch operations
- Rate limiting

**GraphQL API:**
- Single endpoint
- Flexible queries
- Real-time subscriptions
- Type safety
- Introspection

**Webhooks:**
- Event-driven notifications
- Configurable endpoints
- Retry logic
- Signature verification
- Event filtering

**SDKs:**
- JavaScript/TypeScript
- Python
- Ruby
- PHP
- Go
- Java

### Non-Functional Requirements
- API response time: < 200ms (p95)
- API availability: 99.9%+
- Rate limits: Tiered by plan
- Documentation: Complete and current
- Versioning: Semantic versioning

## Business Value

Comprehensive APIs enable ecosystem growth, custom integrations, automation, and platform extensibility, increasing platform value and stickiness.

## Dependencies

- API gateway
- Authentication service
- Rate limiting service
- Webhook delivery system
- Documentation platform

## Acceptance Criteria

1. WHEN calling API THEN response SHALL be within 200ms
2. WHEN rate limit exceeded THEN appropriate error SHALL return
3. IF webhook configured THEN events SHALL be delivered
4. WHEN using SDK THEN it SHALL match API capabilities
5. WHERE authentication required THEN it SHALL be enforced
6. WHEN API changes THEN versioning SHALL be maintained

## Implementation Notes

### REST API Design

**Base URL:**
```
https://api.encaptio.com/v1
```

**Authentication:**
```http
Authorization: Bearer {api_key}
```

**Resource Endpoints:**
```
GET    /capsules              # List capsules
POST   /capsules              # Create capsule
GET    /capsules/{id}         # Get capsule
PATCH  /capsules/{id}         # Update capsule
DELETE /capsules/{id}         # Delete capsule

GET    /capsules/{id}/analytics    # Get analytics
POST   /capsules/{id}/publish      # Publish capsule
POST   /capsules/{id}/unpublish    # Unpublish capsule

GET    /content               # List content
POST   /content               # Upload content
GET    /content/{id}          # Get content
DELETE /content/{id}          # Delete content

GET    /interactions          # List interactions
GET    /interactions/{id}     # Get interaction

GET    /users                 # List team users
POST   /users                 # Invite user
GET    /users/{id}            # Get user
PATCH  /users/{id}            # Update user
DELETE /users/{id}            # Remove user
```

**Request/Response Format:**
```json
// Request
POST /capsules
{
  "title": "Product Demo",
  "description": "Interactive product demonstration",
  "settings": {
    "ai_personality": "professional",
    "voice_enabled": true
  }
}

// Response
{
  "id": "cap_1234567890",
  "title": "Product Demo",
  "description": "Interactive product demonstration",
  "status": "draft",
  "url": "https://encaptio.com/c/product-demo",
  "settings": {
    "ai_personality": "professional",
    "voice_enabled": true
  },
  "created_at": "2025-01-04T10:30:00Z",
  "updated_at": "2025-01-04T10:30:00Z"
}
```

**Error Responses:**
```json
{
  "error": {
    "code": "validation_error",
    "message": "Invalid request parameters",
    "details": [
      {
        "field": "title",
        "message": "Title is required"
      }
    ]
  }
}
```

**HTTP Status Codes:**
- 200: Success
- 201: Created
- 204: No Content
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 429: Too Many Requests
- 500: Internal Server Error

### GraphQL API

**Endpoint:**
```
https://api.encaptio.com/graphql
```

**Schema Example:**
```graphql
type Capsule {
  id: ID!
  title: String!
  description: String
  status: CapsuleStatus!
  url: String!
  settings: CapsuleSettings!
  content: [Content!]!
  analytics: Analytics
  createdAt: DateTime!
  updatedAt: DateTime!
}

type Query {
  capsule(id: ID!): Capsule
  capsules(
    first: Int
    after: String
    filter: CapsuleFilter
  ): CapsuleConnection!
  
  analytics(
    capsuleId: ID!
    dateRange: DateRange
  ): Analytics!
}

type Mutation {
  createCapsule(input: CreateCapsuleInput!): Capsule!
  updateCapsule(id: ID!, input: UpdateCapsuleInput!): Capsule!
  deleteCapsule(id: ID!): Boolean!
  publishCapsule(id: ID!): Capsule!
}

type Subscription {
  capsuleUpdated(id: ID!): Capsule!
  newInteraction(capsuleId: ID!): Interaction!
}
```

**Query Example:**
```graphql
query GetCapsule($id: ID!) {
  capsule(id: $id) {
    id
    title
    status
    analytics {
      views
      interactions
      conversions
    }
    content {
      id
      type
      title
    }
  }
}
```

**Mutation Example:**
```graphql
mutation CreateCapsule($input: CreateCapsuleInput!) {
  createCapsule(input: $input) {
    id
    title
    url
  }
}
```

### Webhooks

**Configuration:**
```json
{
  "url": "https://your-app.com/webhooks/encaptio",
  "events": [
    "capsule.published",
    "capsule.viewed",
    "interaction.created",
    "conversion.completed"
  ],
  "secret": "whsec_..."
}
```

**Webhook Payload:**
```json
{
  "id": "evt_1234567890",
  "type": "interaction.created",
  "created": 1704362400,
  "data": {
    "object": {
      "id": "int_1234567890",
      "capsule_id": "cap_1234567890",
      "user": {
        "name": "John Doe",
        "email": "john@example.com"
      },
      "duration": 180,
      "questions": 5,
      "engagement_score": 85
    }
  }
}
```

**Signature Verification:**
```javascript
const crypto = require('crypto');

function verifyWebhook(payload, signature, secret) {
  const hmac = crypto.createHmac('sha256', secret);
  const digest = hmac.update(payload).digest('hex');
  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(digest)
  );
}
```

**Retry Logic:**
- Retry failed webhooks up to 3 times
- Exponential backoff (1s, 5s, 25s)
- Mark as failed after 3 attempts
- Manual retry option in dashboard

### SDKs

**JavaScript/TypeScript SDK:**
```typescript
import { Encaptio } from '@encaptio/sdk';

const client = new Encaptio({
  apiKey: 'your_api_key'
});

// Create capsule
const capsule = await client.capsules.create({
  title: 'Product Demo',
  description: 'Interactive demo'
});

// Get analytics
const analytics = await client.analytics.get(capsule.id, {
  dateRange: 'last_30_days'
});

// List interactions
const interactions = await client.interactions.list({
  capsuleId: capsule.id,
  limit: 10
});
```

**Python SDK:**
```python
from encaptio import Encaptio

client = Encaptio(api_key='your_api_key')

# Create capsule
capsule = client.capsules.create(
    title='Product Demo',
    description='Interactive demo'
)

# Get analytics
analytics = client.analytics.get(
    capsule.id,
    date_range='last_30_days'
)

# List interactions
interactions = client.interactions.list(
    capsule_id=capsule.id,
    limit=10
)
```

### Rate Limiting

**Rate Limits by Tier:**
```
Free:        100 requests/hour
Pro:         1,000 requests/hour
Business:    10,000 requests/hour
Enterprise:  Custom limits
```

**Rate Limit Headers:**
```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1704366000
```

**Rate Limit Response:**
```json
{
  "error": {
    "code": "rate_limit_exceeded",
    "message": "Rate limit exceeded. Try again in 60 seconds."
  }
}
```

### API Versioning

**Version Strategy:**
- Major version in URL: `/v1`, `/v2`
- Backward compatible changes in minor versions
- Breaking changes require new major version
- Deprecation notices 6 months in advance
- Support previous version for 12 months

**Version Header:**
```http
API-Version: 2025-01-04
```

### API Documentation

**Documentation Platform:**
- OpenAPI/Swagger specification
- Interactive API explorer
- Code examples in multiple languages
- Authentication guide
- Rate limiting details
- Webhook documentation
- SDK documentation

**Example Documentation:**
```yaml
openapi: 3.0.0
info:
  title: Encaptio API
  version: 1.0.0
  description: Encaptio platform API

paths:
  /capsules:
    get:
      summary: List capsules
      parameters:
        - name: limit
          in: query
          schema:
            type: integer
            default: 10
      responses:
        '200':
          description: Success
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/CapsuleList'
```

### Integration Patterns

**Polling:**
```javascript
// Poll for new interactions
setInterval(async () => {
  const interactions = await client.interactions.list({
    since: lastCheck
  });
  processInteractions(interactions);
  lastCheck = Date.now();
}, 60000); // Every minute
```

**Webhooks:**
```javascript
// Receive real-time events
app.post('/webhooks/encaptio', (req, res) => {
  const event = req.body;
  
  if (event.type === 'interaction.created') {
    processInteraction(event.data.object);
  }
  
  res.sendStatus(200);
});
```

**Streaming:**
```javascript
// GraphQL subscription
const subscription = client.subscribe({
  query: `
    subscription {
      newInteraction(capsuleId: "cap_123") {
        id
        user { name email }
        engagementScore
      }
    }
  `
});

subscription.on('data', (data) => {
  processInteraction(data.newInteraction);
});
```

## Related Features

- [System Architecture](./system-architecture.md): API architecture
- [Security & Authentication](./security-authentication.md): API security
- [Integrations](../core-domains/integrations/README.md): Pre-built integrations
