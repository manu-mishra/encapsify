# Formatting Rules and Standards

## Overview

This document defines the formatting standards and automated validation rules for all documentation in the Encaptio/Encapsify documentation suite. Consistent formatting ensures readability, maintainability, and professional presentation.

## Markdown Formatting Standards

### Heading Hierarchy

**Rules:**
- Documents MUST start with a single H1 heading (`#`)
- Heading levels MUST NOT skip levels (e.g., H1 → H3 is invalid)
- Each document SHOULD have a clear heading structure that reflects content organization
- Headings MUST use sentence case (capitalize first word and proper nouns only)

**Validation Checks:**
```
✓ Single H1 at document start
✓ No skipped heading levels
✓ Consistent heading case style
✗ Multiple H1 headings
✗ H1 → H3 without H2
```

### Lists and Bullets

**Rules:**
- Use `-` for unordered lists (not `*` or `+`)
- Use `1.` for ordered lists with proper numbering
- Nested lists MUST be indented with 2 spaces
- List items SHOULD be parallel in structure
- Complex list items MAY use sub-bullets for clarity

**Example:**
```markdown
- First item
  - Nested item
  - Another nested item
- Second item
```

### Code Blocks

**Rules:**
- Code blocks MUST specify language for syntax highlighting
- Inline code MUST use single backticks
- Multi-line code MUST use triple backticks with language identifier
- File paths and commands SHOULD use inline code formatting

**Example:**
```markdown
Use `npm install` to install dependencies.

\`\`\`javascript
const example = "code block";
\`\`\`
```

### Links and References

**Rules:**
- Internal links MUST use relative paths
- External links SHOULD include descriptive text
- Link text MUST be meaningful (avoid "click here")
- Broken links are NOT permitted

**Example:**
```markdown
See [Feature Documentation](../features/README.md) for details.
Visit [AWS Documentation](https://docs.aws.amazon.com) for more information.
```

## Document Structure Standards

### Required Sections

All documentation MUST include:
1. **Title (H1)**: Clear, descriptive document title
2. **Overview**: Brief introduction to document purpose
3. **Main Content**: Organized with appropriate headings
4. **Related Documentation** (if applicable): Links to related content

### Optional Sections

Documents MAY include:
- **Prerequisites**: Required knowledge or setup
- **Examples**: Practical demonstrations
- **Troubleshooting**: Common issues and solutions
- **References**: External resources

## Content Formatting Standards

### Text Formatting

**Rules:**
- Use **bold** for emphasis and important terms
- Use *italics* for subtle emphasis or technical terms
- Use `code formatting` for technical elements, file names, and commands
- Avoid excessive formatting that reduces readability

### Tables

**Rules:**
- Tables MUST have header rows
- Columns MUST be aligned consistently
- Complex data SHOULD use tables for clarity
- Tables SHOULD include a caption or context

**Example:**
```markdown
| Feature | Status | Priority |
|---------|--------|----------|
| Auth    | Done   | High     |
| API     | In Progress | Medium |
```

### Whitespace and Line Breaks

**Rules:**
- Use single blank line between paragraphs
- Use single blank line before and after headings
- Use single blank line before and after code blocks
- No trailing whitespace at end of lines
- Files MUST end with a single newline

## Automated Validation Checks

### Level 1: Critical Errors
These MUST be fixed before document approval:
- Missing H1 heading
- Broken internal links
- Skipped heading levels
- Malformed markdown syntax
- Missing required sections

### Level 2: Warnings
These SHOULD be addressed:
- Inconsistent list formatting
- Missing language identifiers in code blocks
- Non-descriptive link text
- Excessive heading depth (>H4)
- Very long paragraphs (>500 words)

### Level 3: Style Suggestions
These are recommendations:
- Heading case consistency
- Parallel list structure
- Table formatting improvements
- Whitespace optimization

## Validation Process

### Manual Validation
1. Review document against formatting rules
2. Check heading hierarchy and structure
3. Verify all links are functional
4. Ensure consistent formatting throughout
5. Validate code blocks have language identifiers

### Automated Validation
Automated tools check for:
- Markdown syntax errors
- Broken links (internal and external)
- Heading hierarchy violations
- Missing required sections
- Formatting inconsistencies

## Domain-Specific Formatting

### Features Domain
- Feature documents MUST include user stories
- Technical requirements MUST use consistent formatting
- Acceptance criteria SHOULD use numbered lists

### Business Plan Domain
- Strategic documents MUST follow executive summary format
- Financial data SHOULD use tables
- Timelines MUST use consistent date formatting

### Industry Use Cases Domain
- Use cases MUST include scenario descriptions
- Benefits SHOULD use bullet lists
- Implementation steps MUST be numbered

## Compliance Checklist

Before submitting a document for review:
- [ ] Single H1 heading at document start
- [ ] No skipped heading levels
- [ ] All lists use consistent formatting
- [ ] Code blocks include language identifiers
- [ ] All links are functional and properly formatted
- [ ] Required sections are present
- [ ] No markdown syntax errors
- [ ] Consistent whitespace usage
- [ ] File ends with single newline
- [ ] Domain-specific requirements met

## Related Documentation

- [Structure Validation](structure-validation.md)
- [Completeness Checklist](completeness-checklist.md)
- [Documentation Standards](../../DOCUMENTATION-STANDARDS.md)
