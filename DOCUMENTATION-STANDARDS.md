# Documentation Standards and Guidelines

## Purpose

This document establishes the standards, conventions, and best practices for all documentation within the Encaptio/Encapsify project.

## Metadata Standards

All documentation files must include YAML frontmatter with the following fields:

```yaml
---
title: [Document Title]
version: [Semantic version: X.Y]
lastUpdated: [YYYY-MM-DD]
author: [Author Name]
reviewers: [Array of reviewer names]
status: [draft|review|approved|archived]
tags: [Array of relevant tags]
relatedDocuments: [Array of related document paths]
---
```

### Metadata Field Definitions

- **title**: Clear, descriptive title of the document
- **version**: Semantic versioning (major.minor)
- **lastUpdated**: ISO date format (YYYY-MM-DD)
- **author**: Primary author or document owner
- **reviewers**: List of people who have reviewed the document
- **status**: Current document lifecycle status
  - `draft`: Work in progress
  - `review`: Ready for stakeholder review
  - `approved`: Finalized and approved
  - `archived`: Historical version, no longer current
- **tags**: Keywords for categorization and search
- **relatedDocuments**: Relative paths to related documentation

### Industry-Specific Metadata

For use case documents, add:
```yaml
industry: [Industry Name]
```

## Formatting Guidelines

### Headings

- Use ATX-style headings (`#` syntax)
- One H1 (`#`) per document (the title)
- Maintain logical hierarchy (don't skip levels)
- Use sentence case for headings

### Lists

- Use `-` for unordered lists
- Use `1.` for ordered lists
- Indent nested lists with 2 spaces
- Keep list items concise and parallel in structure

### Tables

- Use markdown tables for structured data
- Include header row
- Align columns for readability in source
- Keep tables simple; break complex tables into multiple tables

Example:
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
```

### Code and Technical Content

- Use backticks for inline code: `code`
- Use fenced code blocks with language specification:
  ```language
  code block
  ```
- Include comments in code examples for clarity

### Links and References

- Use descriptive link text (not "click here")
- Use relative paths for internal documentation links
- Format: `[Link Text](path/to/document.md)`
- For cross-references, use format: `See [Document Name](../path/to/doc.md)`

### Emphasis

- Use **bold** for important terms or emphasis
- Use *italics* for subtle emphasis or technical terms
- Avoid excessive formatting

## Content Standards

### Writing Style

- **Clarity**: Use clear, concise language
- **Consistency**: Maintain consistent terminology throughout
- **Audience**: Write for the intended audience (technical vs. business)
- **Active Voice**: Prefer active voice over passive
- **Present Tense**: Use present tense for current features

### Document Structure

Each document type should follow its template structure:

1. **Metadata** (frontmatter)
2. **Title** (H1)
3. **Overview/Introduction**
4. **Main Content** (organized by H2 sections)
5. **Conclusion/Next Steps** (if applicable)
6. **Appendix/References** (if applicable)

### Requirements Format (EARS)

Use Easy Approach to Requirements Syntax:

- **WHEN** [trigger] **THEN** [system] **SHALL** [response]
- **IF** [precondition] **THEN** [system] **SHALL** [response]
- **WHERE** [feature] **THEN** [system] **SHALL** [response]
- **WHILE** [state] **THEN** [system] **SHALL** [response]

Example:
```
WHEN a user uploads a document THEN the system SHALL process it within 30 seconds
```

### User Stories Format

```
As a [user type]
I want [capability]
So that [benefit]
```

## File Naming Conventions

- Use lowercase with hyphens: `file-name.md`
- Be descriptive but concise
- Avoid special characters except hyphens
- Use `.md` extension for markdown files

## Directory Organization

Follow the established domain-driven structure:

```
project-root/
├── features/
│   ├── core-domains/
│   ├── user-profiles/
│   └── cross-cutting/
├── business-plan/
│   ├── strategic-documents/
│   ├── versions/
│   ├── governance/
│   └── execution-playbooks/
├── industry-use-cases/
│   └── [industry-name]/
└── templates/
```

## Version Control

### Document Versioning

- **Major version** (X.0): Significant changes, restructuring, or new sections
- **Minor version** (X.Y): Updates, clarifications, or minor additions
- Update `lastUpdated` field with each change
- Update `version` field according to change significance

### Change Tracking

- Document significant changes in commit messages
- For business plan versions, create new version folders
- Maintain `current/` symlink or copy for latest approved version

## Review and Approval Process

### Review Workflow

1. **Draft**: Author creates initial document
2. **Review**: Document shared with reviewers
3. **Revision**: Author incorporates feedback
4. **Approval**: Stakeholders approve final version
5. **Publication**: Document status set to "approved"

### Review Checklist

- [ ] Metadata complete and accurate
- [ ] Formatting follows standards
- [ ] Content is clear and complete
- [ ] Cross-references are valid
- [ ] Technical accuracy verified
- [ ] Grammar and spelling checked
- [ ] Appropriate for target audience

## Quality Assurance

### Content Quality

- **Accuracy**: All information must be factually correct
- **Completeness**: Cover all necessary aspects of the topic
- **Relevance**: Focus on information valuable to the audience
- **Currency**: Keep information up-to-date

### Technical Quality

- **Valid Links**: All internal and external links must work
- **Proper Formatting**: Follow markdown syntax correctly
- **Template Compliance**: Use appropriate templates
- **Metadata Accuracy**: Ensure all metadata fields are correct

## Cross-Referencing

### Linking Between Documents

Use relative paths and descriptive text:
```markdown
For more details, see [Feature Name](../features/core-domains/feature-name.md)
```

### Maintaining References

- Update `relatedDocuments` in metadata
- Check and update links when moving or renaming files
- Use search to find all references to a document before changes

## Templates Usage

### Available Templates

- `feature-template.md`: For feature documentation
- `business-document-template.md`: For strategic business documents
- `use-case-template.md`: For industry use cases
- `playbook-template.md`: For execution playbooks

### Using Templates

1. Copy appropriate template
2. Rename file following naming conventions
3. Fill in all metadata fields
4. Replace placeholder content
5. Remove unused sections (if appropriate)
6. Follow template structure

## Best Practices

### Do's

✓ Use templates for consistency
✓ Update metadata with every change
✓ Write for your audience
✓ Use clear, descriptive headings
✓ Include examples where helpful
✓ Cross-reference related documents
✓ Review before submitting
✓ Keep documents focused and concise

### Don'ts

✗ Skip metadata fields
✗ Use inconsistent terminology
✗ Create orphaned documents (no links to/from)
✗ Use vague or generic titles
✗ Include outdated information
✗ Ignore templates
✗ Use complex jargon without explanation
✗ Create overly long documents (consider splitting)

## Maintenance

### Regular Reviews

- Quarterly review of all documentation
- Update outdated information
- Archive obsolete documents
- Verify all links and references
- Update version numbers and dates

### Continuous Improvement

- Gather feedback from documentation users
- Refine templates based on usage
- Update standards as needed
- Share lessons learned

## Support and Questions

For questions about documentation standards or assistance with documentation:
- Review this standards document
- Check relevant templates
- Consult with documentation owner
- Refer to examples in existing documentation
