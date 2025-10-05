# Content Validation and Review Procedures

## Overview

This document defines the operational procedures for validating documentation content across the Encaptio/Encapsify documentation suite. These procedures implement the standards defined in the formatting rules, structure validation, cross-reference system, and completeness checklist documents.

## Validation Workflow

### Phase 1: Author Self-Validation

**When:** Before submitting document for review

**Responsibilities:** Document author

**Process:**
1. Run formatting validation checks
2. Verify document structure compliance
3. Test all cross-references and links
4. Complete domain-specific completeness checklist
5. Address all identified issues
6. Mark document as "Ready for Review"

**Tools:**
- [Formatting Rules Checklist](formatting-rules.md)
- [Structure Validation Guide](structure-validation.md)
- [Cross-Reference Validation](cross-reference-system.md)
- [Completeness Checklist](completeness-checklist.md)

### Phase 2: Automated Validation

**When:** Upon document submission or update

**Responsibilities:** Automated validation system

**Checks Performed:**
1. Markdown syntax validation
2. Link integrity verification
3. Heading hierarchy validation
4. Required section presence check
5. Formatting consistency check
6. Placeholder text detection

**Output:** Validation report with errors, warnings, and suggestions

### Phase 3: Peer Review

**When:** After automated validation passes

**Responsibilities:** Assigned reviewer(s)

**Process:**
1. Review validation report
2. Verify content accuracy and completeness
3. Check domain-specific requirements
4. Validate cross-references and relationships
5. Assess content quality and clarity
6. Provide feedback or approve

**Tools:**
- [Review Assignment Process](../review-workflows/review-assignment.md)
- [Feedback Procedures](../review-workflows/feedback-procedures.md)

### Phase 4: Final Approval

**When:** After peer review approval

**Responsibilities:** Document owner or designated approver

**Process:**
1. Review all feedback and revisions
2. Verify all issues resolved
3. Confirm document meets all standards
4. Grant final approval
5. Update document status

**Tools:**
- [Approval Process](../review-workflows/approval-process.md)

## Validation Procedures by Type

### 1. Formatting Validation Procedure

**Objective:** Ensure consistent formatting across all documentation

**Steps:**

1. **Check Heading Structure**
   ```
   - Verify single H1 at document start
   - Confirm no skipped heading levels
   - Validate heading case consistency
   - Check heading hierarchy depth (max H4 recommended)
   ```

2. **Validate List Formatting**
   ```
   - Verify consistent bullet style (-)
   - Check proper indentation (2 spaces)
   - Validate ordered list numbering
   - Ensure parallel list structure
   ```

3. **Check Code Block Formatting**
   ```
   - Verify language identifiers present
   - Check inline code usage for technical terms
   - Validate code block syntax
   - Ensure proper formatting of file paths
   ```

4. **Validate Link Formatting**
   ```
   - Check relative path usage
   - Verify descriptive link text
   - Validate link syntax
   - Ensure no broken link formatting
   ```

5. **Check Whitespace and Line Breaks**
   ```
   - Verify single blank lines between sections
   - Check no trailing whitespace
   - Ensure file ends with newline
   - Validate consistent spacing
   ```

**Validation Checklist:**
- [ ] Single H1 heading present
- [ ] No skipped heading levels
- [ ] Consistent list formatting
- [ ] Code blocks have language identifiers
- [ ] Links properly formatted
- [ ] Proper whitespace usage
- [ ] No trailing whitespace
- [ ] File ends with newline

**Common Issues and Fixes:**
- Multiple H1 headings → Demote additional H1s to H2
- Skipped heading levels → Add intermediate heading levels
- Inconsistent bullets → Standardize to `-` character
- Missing code language → Add language identifier
- Trailing whitespace → Remove extra spaces

### 2. Structure Validation Procedure

**Objective:** Ensure documents follow required structural patterns

**Steps:**

1. **Identify Document Type**
   ```
   Determine domain and specific document type:
   - Features: Core domain, user profile, or cross-cutting
   - Business Plan: Strategic, playbook, or governance
   - Industry Use Cases: Use case or template
   ```

2. **Check Required Sections**
   ```
   For identified document type:
   - List all required sections
   - Verify each section is present
   - Check section naming matches standards
   - Validate section order
   ```

3. **Validate Content Organization**
   ```
   - Verify logical section flow
   - Check for orphaned content
   - Ensure proper nesting
   - Validate subsection structure
   ```

4. **Check Optional Sections**
   ```
   - Identify recommended optional sections
   - Assess if optional sections would improve document
   - Verify optional sections follow standards
   ```

5. **Validate Cross-References**
   ```
   - Check "Related Documentation" section present
   - Verify appropriate cross-domain links
   - Validate dependency documentation
   ```

**Validation Checklist:**
- [ ] Document type correctly identified
- [ ] All required sections present
- [ ] Sections properly named
- [ ] Logical content organization
- [ ] No orphaned content
- [ ] Appropriate optional sections included
- [ ] Cross-references present

**Common Issues and Fixes:**
- Missing required section → Add section with appropriate content
- Incorrect section name → Rename to match standard
- Orphaned content → Move under appropriate heading
- Missing cross-references → Add "Related Documentation" section

### 3. Cross-Reference Validation Procedure

**Objective:** Ensure all internal links are functional and appropriate

**Steps:**

1. **Extract All Links**
   ```
   - Identify all markdown links in document
   - Categorize by type (internal, section, external)
   - Create link inventory
   ```

2. **Validate Link Syntax**
   ```
   For each link:
   - Check markdown syntax correctness
   - Verify relative path usage
   - Validate file extension present
   - Check case sensitivity
   ```

3. **Test Link Functionality**
   ```
   For each internal link:
   - Resolve relative path
   - Verify target file exists
   - For section links, confirm heading exists
   - Check link accessibility
   ```

4. **Validate Link Relationships**
   ```
   - Check bidirectional references
   - Verify dependency links
   - Validate cross-domain relationships
   - Ensure appropriate context
   ```

5. **Check for Orphaned Documents**
   ```
   - Identify documents with no incoming links
   - Assess if document should be linked
   - Recommend integration points
   ```

**Validation Checklist:**
- [ ] All links use relative paths
- [ ] Link syntax is correct
- [ ] All linked files exist
- [ ] Section anchors are valid
- [ ] Link text is descriptive
- [ ] Bidirectional references present
- [ ] No orphaned documents

**Common Issues and Fixes:**
- Broken link → Update path to correct location
- Absolute path → Convert to relative path
- Missing file extension → Add .md extension
- Invalid section anchor → Update to match heading
- Missing bidirectional link → Add reciprocal reference

### 4. Completeness Validation Procedure

**Objective:** Ensure documents contain all necessary content

**Steps:**

1. **Check Basic Elements**
   ```
   - Verify title (H1) present
   - Check overview/introduction exists
   - Ensure main content is substantive
   - Validate related documentation links
   ```

2. **Validate Content Depth**
   ```
   - Check section length meets minimums
   - Verify no placeholder text
   - Ensure examples are specific
   - Validate technical detail sufficiency
   ```

3. **Domain-Specific Validation**
   ```
   Apply appropriate domain checklist:
   - Features: User stories, technical requirements, business value
   - Business Plan: Executive summary, analysis, recommendations
   - Use Cases: Persona, scenario, solution, implementation
   ```

4. **Quality Assessment**
   ```
   - Check content accuracy
   - Verify clarity and readability
   - Validate consistency
   - Ensure actionability
   ```

5. **Completeness Scoring**
   ```
   Calculate completeness percentage:
   - 100%: All criteria met, ready for review
   - 75-99%: Minor gaps, mostly complete
   - 50-74%: Significant gaps, needs work
   - <50%: Incomplete, not ready
   ```

**Validation Checklist:**
- [ ] All required sections have content
- [ ] No placeholder text (TODO, TBD)
- [ ] Content depth meets minimums
- [ ] Domain-specific criteria met
- [ ] Examples are specific and relevant
- [ ] Technical accuracy verified
- [ ] Completeness score ≥75%

**Common Issues and Fixes:**
- Placeholder text → Replace with actual content
- Insufficient detail → Expand sections with specifics
- Missing required section → Add section with content
- Generic examples → Replace with specific examples
- Low completeness score → Address gaps systematically

## Automated Quality Checks

### Automated Check Categories

#### Level 1: Critical Errors (Must Fix)
These prevent document approval:
- Missing H1 heading
- Broken internal links
- Skipped heading levels
- Malformed markdown syntax
- Missing required sections
- Placeholder text in required sections

#### Level 2: Warnings (Should Fix)
These should be addressed before approval:
- Inconsistent list formatting
- Missing code block language identifiers
- Non-descriptive link text
- Very short sections (<50 words)
- Missing optional recommended sections
- No cross-references

#### Level 3: Suggestions (Consider)
These are recommendations for improvement:
- Heading case consistency
- Parallel list structure
- Table formatting improvements
- Additional examples
- Enhanced cross-references

### Validation Report Format

```markdown
# Validation Report

**Document:** [path/to/document.md]
**Date:** [YYYY-MM-DD]
**Validator:** [Automated/Manual]

## Summary
- Total Checks: [number]
- Passed: [number]
- Critical Errors: [number]
- Warnings: [number]
- Suggestions: [number]

## Critical Errors
[If none, state "None"]

1. **[Error Type]**
   - Location: Line [number] or Section "[name]"
   - Issue: [Description]
   - Fix: [Required action]

## Warnings
[If none, state "None"]

1. **[Warning Type]**
   - Location: Line [number] or Section "[name]"
   - Issue: [Description]
   - Recommendation: [Suggested action]

## Suggestions
[If none, state "None"]

1. **[Suggestion Type]**
   - Location: Line [number] or Section "[name]"
   - Suggestion: [Improvement idea]

## Validation Status
- [ ] Ready for Review (No critical errors)
- [ ] Needs Revision (Critical errors present)

## Next Steps
[Recommended actions based on validation results]
```

### Running Automated Validation

**Manual Validation Process:**
1. Open document in markdown editor
2. Review against formatting rules checklist
3. Test all links manually
4. Check structure against templates
5. Complete domain-specific checklist
6. Document findings in validation report

**Automated Validation (if tools available):**
1. Run markdown linter for syntax
2. Execute link checker for broken links
3. Run structure validator for required sections
4. Check for placeholder text patterns
5. Generate automated validation report
6. Review and address findings

## Validation Frequency

### Continuous Validation
- On document creation
- On document update
- Before submitting for review

### Periodic Validation
- Weekly: New and recently updated documents
- Monthly: All active documents
- Quarterly: Complete documentation suite audit

### Triggered Validation
- After file reorganization
- After template updates
- After standards changes
- Before major releases

## Validation Metrics

### Key Performance Indicators

**Quality Metrics:**
- Percentage of documents passing validation
- Average number of critical errors per document
- Average time to fix validation issues
- Percentage of documents with no warnings

**Process Metrics:**
- Average validation time per document
- Percentage of documents requiring revision
- Number of validation cycles before approval
- Time from submission to approval

**Trend Metrics:**
- Improvement in validation pass rate over time
- Reduction in common error types
- Decrease in validation cycle time
- Increase in first-pass approval rate

### Tracking and Reporting

**Weekly Reports:**
- Documents validated
- Critical errors found and fixed
- Common issues identified
- Validation pass rate

**Monthly Reports:**
- Validation trends
- Quality improvements
- Process efficiency metrics
- Recommendations for standards updates

**Quarterly Reports:**
- Comprehensive quality assessment
- Standards effectiveness review
- Process optimization opportunities
- Training needs identification

## Continuous Improvement

### Feedback Loop

1. **Collect Validation Data**
   - Track common errors
   - Identify recurring issues
   - Monitor validation metrics

2. **Analyze Patterns**
   - Identify root causes
   - Assess standards effectiveness
   - Evaluate process efficiency

3. **Implement Improvements**
   - Update standards and templates
   - Enhance validation procedures
   - Provide targeted training
   - Optimize automation

4. **Measure Impact**
   - Track improvement metrics
   - Assess effectiveness of changes
   - Gather stakeholder feedback
   - Iterate on improvements

### Standards Evolution

**When to Update Standards:**
- Recurring validation issues indicate unclear standards
- New document types require new standards
- Technology or tool changes enable better practices
- Stakeholder feedback suggests improvements

**Update Process:**
1. Identify need for standards update
2. Draft proposed changes
3. Review with stakeholders
4. Update standards documentation
5. Communicate changes
6. Update validation procedures
7. Provide training if needed

## Related Documentation

- [Formatting Rules](formatting-rules.md)
- [Structure Validation](structure-validation.md)
- [Cross-Reference System](cross-reference-system.md)
- [Completeness Checklist](completeness-checklist.md)
- [Review Assignment](../review-workflows/review-assignment.md)
- [Feedback Procedures](../review-workflows/feedback-procedures.md)
- [Approval Process](../review-workflows/approval-process.md)
- [Quality Metrics](../metrics/quality-metrics.md)
