# Business Plan Version Management

This directory contains version control for business plan iterations, enabling tracking of changes, comparisons between versions, and maintenance of historical records.

## Version Structure

Each version is stored in its own subdirectory with the following structure:

```
versions/
├── v1.0/
│   ├── business-plan-v1.0.md
│   ├── changelog.md
│   └── approval-record.md
├── v2.0/
│   ├── business-plan-v2.0.md
│   ├── changelog.md
│   └── approval-record.md
└── current/
    └── [symlink to latest approved version]
```

## Version Numbering

**Major Version (X.0)**: Significant strategic changes, new business model, major pivots
- Example: v1.0 → v2.0 (new market focus, revised financial model)

**Minor Version (X.Y)**: Updates to projections, market analysis, or strategy refinements
- Example: v1.0 → v1.1 (updated financial projections, new competitive analysis)

**Patch Version (X.Y.Z)**: Minor corrections, clarifications, or formatting updates
- Example: v1.1 → v1.1.1 (typo fixes, updated contact information)

## Version Lifecycle

### Draft
- Work in progress
- Not yet reviewed or approved
- Subject to significant changes

### Review
- Submitted for stakeholder review
- Feedback being collected
- Revisions in progress

### Approved
- Formally approved by CEO and Board
- Official version for use
- Archived for historical record

### Archived
- Superseded by newer version
- Maintained for historical reference
- No longer active

## Version Comparison Process

When creating a new version:

1. Copy previous version to new directory
2. Make necessary updates and changes
3. Document all changes in changelog.md
4. Create comparison document highlighting key differences
5. Submit for review and approval
6. Upon approval, update current/ symlink

## Approval Workflow

1. **Draft Creation**: Author creates new version draft
2. **Internal Review**: Executive team reviews and provides feedback
3. **Revision**: Author incorporates feedback
4. **Board Review**: Board of Directors reviews
5. **Approval**: CEO and Board Chair sign approval record
6. **Publication**: Version marked as current and distributed

## Change Tracking

All changes between versions must be documented in the changelog.md file, including:
- Date of change
- Author of change
- Description of change
- Rationale for change
- Impact assessment

## Access Control

- **Draft Versions**: Limited to executive team
- **Review Versions**: Executive team and board
- **Approved Versions**: All stakeholders
- **Archived Versions**: Available for reference

## Retention Policy

- All approved versions retained indefinitely
- Draft versions retained for 1 year after superseded
- Review versions retained for 2 years after superseded

## Current Version

The `current/` directory always contains a reference to the latest approved version of the business plan. This ensures stakeholders always have access to the most up-to-date, official version.

## Version History

| Version | Date | Status | Key Changes |
|---------|------|--------|-------------|
| v1.0 | Jan 2025 | Draft | Initial business plan |

## Related Documents

- Strategic Documents (../strategic-documents/)
- Governance Documents (../governance/)
- Execution Playbooks (../execution-playbooks/)
