# Quick Validation Guide

## Overview

This quick reference guide provides a streamlined checklist for validating documentation before submission. Use this for rapid self-validation before formal review.

## 5-Minute Pre-Submission Check

### 1. Visual Scan (1 minute)
- [ ] Document has clear title at top
- [ ] Sections are properly organized with headings
- [ ] No obvious formatting issues
- [ ] No red flags (TODO, TBD, placeholder text)

### 2. Link Check (1 minute)
- [ ] Click all internal links - do they work?
- [ ] Links use relative paths (not absolute)
- [ ] Link text is descriptive (not "click here")

### 3. Structure Check (1 minute)
- [ ] Required sections present for document type
- [ ] Content under appropriate headings
- [ ] Related documentation section included

### 4. Content Check (1 minute)
- [ ] All sections have real content (not placeholders)
- [ ] Examples are specific and relevant
- [ ] Technical details are sufficient

### 5. Final Polish (1 minute)
- [ ] Spell check completed
- [ ] Grammar is correct
- [ ] Formatting is consistent
- [ ] File saved with final changes

## Document Type Quick Checks

### Feature Document
```
✓ Overview explains what the feature does
✓ Business value is clear
✓ User stories with acceptance criteria
✓ Technical requirements specified
✓ Dependencies identified (if any)
```

### Use Case Document
```
✓ Industry context provided
✓ User persona defined
✓ Scenario clearly described
✓ Solution approach explained
✓ Implementation steps included
✓ Success metrics defined
```

### Business Plan Document
```
✓ Executive summary present
✓ Analysis with supporting data
✓ Key takeaways summarized
✓ Next steps or recommendations
```

### Playbook Document
```
✓ Objectives clearly stated
✓ Step-by-step process documented
✓ Roles and responsibilities assigned
✓ Success criteria defined
```

## Common Issues Quick Fixes

### Issue: Broken Link
**Quick Fix:** Update path to correct location or remove if no longer relevant

### Issue: Missing Section
**Quick Fix:** Add section with at least 100-200 words of content

### Issue: Placeholder Text
**Quick Fix:** Replace with actual content or remove section if not needed

### Issue: Poor Formatting
**Quick Fix:** Use consistent bullets (-), add blank lines between sections

### Issue: No Cross-References
**Quick Fix:** Add "Related Documentation" section with 2-3 relevant links

## Validation Severity Guide

### 🔴 Critical (Must Fix Before Submission)
- Broken internal links
- Missing required sections
- Placeholder text in required sections
- Malformed markdown syntax
- No H1 heading

### 🟡 Warning (Should Fix Before Submission)
- Very short sections (<50 words)
- Missing code block language identifiers
- Non-descriptive link text
- Inconsistent formatting
- Missing optional recommended sections

### 🟢 Suggestion (Nice to Have)
- Additional examples
- More cross-references
- Enhanced formatting
- Deeper content in optional sections

## Self-Validation Checklist

### Before Starting Review
- [ ] I have read the document completely
- [ ] I understand the document's purpose
- [ ] I know which document type this is

### Formatting Validation
- [ ] Single H1 heading at start
- [ ] No skipped heading levels (H1→H2→H3)
- [ ] Lists use consistent bullets (-)
- [ ] Code blocks have language identifiers
- [ ] Links are properly formatted
- [ ] No trailing whitespace

### Structure Validation
- [ ] All required sections present
- [ ] Sections properly named
- [ ] Content logically organized
- [ ] No orphaned content
- [ ] Related documentation included

### Link Validation
- [ ] All internal links work
- [ ] Links use relative paths
- [ ] Link text is descriptive
- [ ] Section anchors are valid
- [ ] Bidirectional references present (where appropriate)

### Completeness Validation
- [ ] No placeholder text (TODO, TBD)
- [ ] All sections have substantive content
- [ ] Examples are specific and relevant
- [ ] Technical details are sufficient
- [ ] Domain-specific requirements met

### Final Check
- [ ] Spell check completed
- [ ] Grammar verified
- [ ] Consistency checked
- [ ] Ready for review

## Quick Validation Commands

### Manual Validation Steps
```
1. Open document in markdown editor
2. Preview rendered markdown
3. Click through all links
4. Review against checklist
5. Fix identified issues
6. Re-check after fixes
```

### Automated Validation (if available)
```bash
# Run full validation
validate-doc path/to/document.md

# Check specific aspects
validate-doc --formatting path/to/document.md
validate-doc --links path/to/document.md
validate-doc --structure path/to/document.md
```

## Validation Decision Tree

```
Start
  ↓
Is this a new document?
  ├─ Yes → Use full validation checklist
  └─ No → Is this a minor update?
      ├─ Yes → Use quick 5-minute check
      └─ No → Use full validation checklist
        ↓
Run validation
  ↓
Any critical errors?
  ├─ Yes → Fix errors and re-validate
  └─ No → Any warnings?
      ├─ Yes → Fix warnings (recommended)
      └─ No → Ready for submission
        ↓
Submit for review
```

## Time Estimates

### Quick Validation (Minor Updates)
- 5-minute check: ~5 minutes
- Fix minor issues: ~5-10 minutes
- **Total: 10-15 minutes**

### Full Validation (New Documents)
- Complete all checklists: ~15-20 minutes
- Fix identified issues: ~20-30 minutes
- Re-validation: ~5-10 minutes
- **Total: 40-60 minutes**

### Automated Validation (if available)
- Run automated checks: ~1-2 minutes
- Review report: ~5 minutes
- Fix issues: ~10-30 minutes
- **Total: 15-35 minutes**

## Validation Tips

### Efficiency Tips
1. **Use templates** - Start with correct structure
2. **Validate as you write** - Don't wait until the end
3. **Fix issues immediately** - Easier than batch fixing
4. **Use automation** - Let tools catch simple errors
5. **Learn common mistakes** - Avoid repeating them

### Quality Tips
1. **Read aloud** - Catches awkward phrasing
2. **Take breaks** - Fresh eyes catch more issues
3. **Get peer review** - Others see what you miss
4. **Check examples** - Ensure they're accurate
5. **Verify links** - Don't assume they work

### Time-Saving Tips
1. **Use checklist** - Don't rely on memory
2. **Batch similar tasks** - Check all links at once
3. **Use search** - Find all instances of issues
4. **Keep notes** - Document common fixes
5. **Create shortcuts** - For frequent validations

## When to Seek Help

### Ask for Review Help When:
- Unsure about document structure
- Complex cross-domain relationships
- Technical accuracy questions
- Unclear requirements
- Multiple validation failures

### Ask for Standards Clarification When:
- Conflicting guidance in standards
- New document type not covered
- Edge cases not addressed
- Standards seem outdated
- Validation results unclear

## Validation Resources

### Quick Reference Documents
- [Formatting Rules](formatting-rules.md) - Detailed formatting standards
- [Structure Validation](structure-validation.md) - Structure requirements
- [Cross-Reference System](cross-reference-system.md) - Link validation
- [Completeness Checklist](completeness-checklist.md) - Content requirements

### Detailed Procedures
- [Validation Procedures](validation-procedures.md) - Complete validation process
- [Validation Script Template](validation-script-template.md) - Automation guide

### Review Workflows
- [Review Assignment](../review-workflows/review-assignment.md) - How reviews work
- [Feedback Procedures](../review-workflows/feedback-procedures.md) - Handling feedback
- [Approval Process](../review-workflows/approval-process.md) - Final approval

### Templates
- [Feature Template](../../templates/feature-template.md)
- [Use Case Template](../../templates/use-case-template.md)
- [Business Document Template](../../templates/business-document-template.md)
- [Playbook Template](../../templates/playbook-template.md)

## Validation Status Indicators

### Document Status Labels

**🔴 Not Ready**
- Critical errors present
- Missing required sections
- Placeholder text remains
- Broken links

**🟡 Needs Work**
- Warnings present
- Content could be deeper
- Minor formatting issues
- Missing optional sections

**🟢 Ready for Review**
- No critical errors
- All required sections complete
- Formatting correct
- Links functional

**✅ Approved**
- Passed peer review
- All feedback addressed
- Final approval granted
- Ready for publication

## Quick Validation Workflow

```
1. Write/Update Document
   ↓
2. Self-Validation (5-min or full)
   ↓
3. Fix Issues
   ↓
4. Re-validate
   ↓
5. Submit for Review
   ↓
6. Address Feedback
   ↓
7. Final Validation
   ↓
8. Approval
```

## Related Documentation

- [Validation Procedures](validation-procedures.md) - Detailed validation process
- [Formatting Rules](formatting-rules.md) - Formatting standards
- [Structure Validation](structure-validation.md) - Structure requirements
- [Cross-Reference System](cross-reference-system.md) - Link validation
- [Completeness Checklist](completeness-checklist.md) - Content verification
- [Documentation Standards](../../DOCUMENTATION-STANDARDS.md) - Overall standards
