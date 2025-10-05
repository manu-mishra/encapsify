# Validation Script Template

## Overview

This document provides templates and pseudocode for implementing automated validation scripts. These templates can be adapted to various scripting languages (Python, JavaScript, Bash, etc.) to automate the validation procedures defined in the quality assurance system.

## Script Architecture

### Modular Design

```
validation-system/
├── validators/
│   ├── formatting_validator
│   ├── structure_validator
│   ├── link_validator
│   └── completeness_validator
├── utils/
│   ├── markdown_parser
│   ├── file_system_helper
│   └── report_generator
├── config/
│   ├── validation_rules.json
│   └── document_templates.json
└── main_validator
```

## Core Validation Functions

### 1. Formatting Validator

**Purpose:** Check markdown formatting compliance

**Pseudocode:**
```
function validateFormatting(documentPath):
    document = readFile(documentPath)
    errors = []
    warnings = []
    suggestions = []
    
    // Check heading structure
    headings = extractHeadings(document)
    
    // Verify single H1
    h1Count = countHeadingLevel(headings, 1)
    if h1Count == 0:
        errors.append("Missing H1 heading")
    else if h1Count > 1:
        errors.append("Multiple H1 headings found")
    
    // Check for skipped heading levels
    for i in range(1, len(headings)):
        currentLevel = headings[i].level
        previousLevel = headings[i-1].level
        if currentLevel > previousLevel + 1:
            errors.append("Skipped heading level at line " + headings[i].line)
    
    // Check list formatting
    lists = extractLists(document)
    for list in lists:
        if not isConsistentBulletStyle(list):
            warnings.append("Inconsistent bullet style at line " + list.line)
        if not isProperlyIndented(list):
            warnings.append("Improper list indentation at line " + list.line)
    
    // Check code blocks
    codeBlocks = extractCodeBlocks(document)
    for block in codeBlocks:
        if not hasLanguageIdentifier(block):
            warnings.append("Code block missing language identifier at line " + block.line)
    
    // Check links
    links = extractLinks(document)
    for link in links:
        if not isDescriptiveLinkText(link.text):
            warnings.append("Non-descriptive link text at line " + link.line)
        if not isRelativePath(link.url) and isInternalLink(link.url):
            errors.append("Absolute path used for internal link at line " + link.line)
    
    // Check whitespace
    if hasTrailingWhitespace(document):
        warnings.append("Trailing whitespace found")
    if not endsWithNewline(document):
        warnings.append("File does not end with newline")
    
    return {
        errors: errors,
        warnings: warnings,
        suggestions: suggestions
    }
```

**Implementation Notes:**
- Use regex patterns for markdown element extraction
- Maintain line number tracking for error reporting
- Consider using existing markdown parsing libraries
- Cache parsed document structure for efficiency

### 2. Structure Validator

**Purpose:** Verify document structure compliance

**Pseudocode:**
```
function validateStructure(documentPath, documentType):
    document = readFile(documentPath)
    template = loadTemplate(documentType)
    errors = []
    warnings = []
    
    // Extract document sections
    sections = extractSections(document)
    sectionTitles = sections.map(s => s.title)
    
    // Check required sections
    for requiredSection in template.requiredSections:
        if requiredSection not in sectionTitles:
            errors.append("Missing required section: " + requiredSection)
    
    // Check section order
    if template.enforceOrder:
        expectedOrder = template.sectionOrder
        actualOrder = getSectionOrder(sections, expectedOrder)
        if actualOrder != expectedOrder:
            warnings.append("Sections not in recommended order")
    
    // Check for orphaned content
    orphanedContent = findOrphanedContent(document)
    if orphanedContent.length > 0:
        for orphan in orphanedContent:
            warnings.append("Orphaned content at line " + orphan.line)
    
    // Validate section depth
    for section in sections:
        if section.level > 4:
            suggestions.append("Section nesting too deep at line " + section.line)
    
    // Check for empty required sections
    for section in sections:
        if section.title in template.requiredSections:
            if isEmpty(section.content):
                errors.append("Required section is empty: " + section.title)
    
    return {
        errors: errors,
        warnings: warnings,
        suggestions: suggestions
    }
```

**Implementation Notes:**
- Load document type templates from configuration
- Support flexible section matching (case-insensitive, fuzzy)
- Detect section boundaries accurately
- Handle nested sections properly

### 3. Link Validator

**Purpose:** Verify all internal links are functional

**Pseudocode:**
```
function validateLinks(documentPath, repositoryRoot):
    document = readFile(documentPath)
    documentDir = getDirectory(documentPath)
    errors = []
    warnings = []
    
    // Extract all links
    links = extractLinks(document)
    
    for link in links:
        // Skip external links
        if isExternalLink(link.url):
            continue
        
        // Validate link syntax
        if not isValidMarkdownLink(link):
            errors.append("Malformed link at line " + link.line)
            continue
        
        // Check relative path
        if not isRelativePath(link.url):
            errors.append("Non-relative path at line " + link.line)
            continue
        
        // Resolve path
        targetPath = resolvePath(documentDir, link.url)
        
        // Check if target exists
        if not fileExists(targetPath):
            errors.append("Broken link at line " + link.line + ": " + link.url)
            continue
        
        // For section links, verify section exists
        if hasSectionAnchor(link.url):
            anchor = extractAnchor(link.url)
            targetDocument = readFile(targetPath)
            if not sectionExists(targetDocument, anchor):
                errors.append("Invalid section anchor at line " + link.line + ": " + anchor)
    
    // Check for bidirectional references
    relatedDocs = findRelatedDocuments(documentPath)
    for relatedDoc in relatedDocs:
        if not hasBackReference(relatedDoc, documentPath):
            warnings.append("Missing bidirectional reference to: " + relatedDoc)
    
    // Check for orphaned documents
    if not hasIncomingLinks(documentPath, repositoryRoot):
        warnings.append("Document has no incoming links (orphaned)")
    
    return {
        errors: errors,
        warnings: warnings,
        suggestions: suggestions
    }
```

**Implementation Notes:**
- Handle both file and section links
- Properly resolve relative paths
- Consider case sensitivity of file systems
- Build link graph for bidirectional checking

### 4. Completeness Validator

**Purpose:** Ensure documents have sufficient content

**Pseudocode:**
```
function validateCompleteness(documentPath, documentType):
    document = readFile(documentPath)
    template = loadTemplate(documentType)
    errors = []
    warnings = []
    
    // Check for placeholder text
    placeholders = ["TODO", "TBD", "[TODO]", "[TBD]", "Coming Soon"]
    for placeholder in placeholders:
        if contains(document, placeholder):
            errors.append("Placeholder text found: " + placeholder)
    
    // Check section content depth
    sections = extractSections(document)
    for section in sections:
        wordCount = countWords(section.content)
        
        if section.title in template.requiredSections:
            minWords = template.minimumWords.required
            if wordCount < minWords:
                errors.append("Section too short: " + section.title + 
                            " (" + wordCount + " words, minimum " + minWords + ")")
        else:
            minWords = template.minimumWords.optional
            if wordCount > 0 and wordCount < minWords:
                warnings.append("Section could use more detail: " + section.title)
    
    // Check for examples
    if template.requiresExamples:
        if not hasCodeBlocks(document) and not hasExampleSections(document):
            warnings.append("Document should include examples")
    
    // Domain-specific checks
    if documentType == "feature":
        if not hasUserStories(document):
            errors.append("Feature document missing user stories")
        if not hasTechnicalRequirements(document):
            errors.append("Feature document missing technical requirements")
    
    else if documentType == "use-case":
        if not hasPersona(document):
            errors.append("Use case missing user persona")
        if not hasScenario(document):
            errors.append("Use case missing scenario description")
    
    else if documentType == "playbook":
        if not hasStepByStepProcess(document):
            errors.append("Playbook missing step-by-step process")
    
    // Calculate completeness score
    totalChecks = errors.length + warnings.length + suggestions.length
    passedChecks = totalChecks - errors.length
    completenessScore = (passedChecks / totalChecks) * 100
    
    return {
        errors: errors,
        warnings: warnings,
        suggestions: suggestions,
        completenessScore: completenessScore
    }
```

**Implementation Notes:**
- Define minimum word counts per document type
- Use pattern matching for domain-specific elements
- Calculate meaningful completeness metrics
- Provide actionable feedback

## Utility Functions

### Markdown Parser Utilities

```
function extractHeadings(document):
    // Parse markdown and extract all headings with levels and line numbers
    headings = []
    lines = document.split("\n")
    for i, line in enumerate(lines):
        if matches(line, /^(#{1,6})\s+(.+)$/):
            level = countHashMarks(line)
            text = extractHeadingText(line)
            headings.append({
                level: level,
                text: text,
                line: i + 1
            })
    return headings

function extractLinks(document):
    // Extract all markdown links with text and URLs
    links = []
    pattern = /\[([^\]]+)\]\(([^\)]+)\)/g
    matches = findAllMatches(document, pattern)
    for match in matches:
        links.append({
            text: match.group(1),
            url: match.group(2),
            line: getLineNumber(document, match.start)
        })
    return links

function extractSections(document):
    // Parse document into sections based on headings
    sections = []
    headings = extractHeadings(document)
    lines = document.split("\n")
    
    for i in range(len(headings)):
        startLine = headings[i].line
        endLine = headings[i+1].line if i+1 < len(headings) else len(lines)
        content = lines[startLine:endLine].join("\n")
        
        sections.append({
            title: headings[i].text,
            level: headings[i].level,
            line: startLine,
            content: content
        })
    
    return sections

function extractCodeBlocks(document):
    // Find all code blocks with language identifiers
    codeBlocks = []
    pattern = /```(\w*)\n([\s\S]*?)```/g
    matches = findAllMatches(document, pattern)
    for match in matches:
        codeBlocks.append({
            language: match.group(1),
            code: match.group(2),
            line: getLineNumber(document, match.start)
        })
    return codeBlocks
```

### File System Utilities

```
function resolvePath(basePath, relativePath):
    // Resolve relative path from base path
    if isAbsolutePath(relativePath):
        return relativePath
    
    // Handle ../ and ./ in path
    parts = relativePath.split("/")
    baseParts = basePath.split("/")
    
    for part in parts:
        if part == "..":
            baseParts.pop()
        else if part != ".":
            baseParts.append(part)
    
    return baseParts.join("/")

function findRelatedDocuments(documentPath):
    // Find documents that should reference this document
    // Based on domain relationships and dependencies
    relatedDocs = []
    
    // Check for feature-to-use-case relationships
    if isFeatureDocument(documentPath):
        useCases = findUseCasesForFeature(documentPath)
        relatedDocs.extend(useCases)
    
    // Check for dependency relationships
    dependencies = extractDependencies(documentPath)
    relatedDocs.extend(dependencies)
    
    return relatedDocs

function hasIncomingLinks(documentPath, repositoryRoot):
    // Check if any other documents link to this one
    allDocuments = findAllMarkdownFiles(repositoryRoot)
    
    for doc in allDocuments:
        if doc == documentPath:
            continue
        
        links = extractLinks(readFile(doc))
        for link in links:
            targetPath = resolvePath(getDirectory(doc), link.url)
            if targetPath == documentPath:
                return true
    
    return false
```

### Report Generator

```
function generateValidationReport(results, documentPath):
    report = "# Validation Report\n\n"
    report += "**Document:** " + documentPath + "\n"
    report += "**Date:** " + getCurrentDate() + "\n"
    report += "**Validator:** Automated\n\n"
    
    // Summary
    report += "## Summary\n"
    totalChecks = results.errors.length + results.warnings.length + results.suggestions.length
    report += "- Total Checks: " + totalChecks + "\n"
    report += "- Critical Errors: " + results.errors.length + "\n"
    report += "- Warnings: " + results.warnings.length + "\n"
    report += "- Suggestions: " + results.suggestions.length + "\n"
    
    if results.completenessScore:
        report += "- Completeness Score: " + results.completenessScore + "%\n"
    
    report += "\n"
    
    // Errors
    report += "## Critical Errors\n"
    if results.errors.length == 0:
        report += "None\n"
    else:
        for i, error in enumerate(results.errors):
            report += (i+1) + ". " + error + "\n"
    report += "\n"
    
    // Warnings
    report += "## Warnings\n"
    if results.warnings.length == 0:
        report += "None\n"
    else:
        for i, warning in enumerate(results.warnings):
            report += (i+1) + ". " + warning + "\n"
    report += "\n"
    
    // Suggestions
    report += "## Suggestions\n"
    if results.suggestions.length == 0:
        report += "None\n"
    else:
        for i, suggestion in enumerate(results.suggestions):
            report += (i+1) + ". " + suggestion + "\n"
    report += "\n"
    
    // Status
    report += "## Validation Status\n"
    if results.errors.length == 0:
        report += "- [x] Ready for Review\n"
        report += "- [ ] Needs Revision\n"
    else:
        report += "- [ ] Ready for Review\n"
        report += "- [x] Needs Revision\n"
    
    return report
```

## Main Validation Script

```
function validateDocument(documentPath, options):
    // Determine document type
    documentType = detectDocumentType(documentPath)
    
    // Initialize results
    allResults = {
        errors: [],
        warnings: [],
        suggestions: [],
        completenessScore: 0
    }
    
    // Run formatting validation
    if options.checkFormatting:
        formattingResults = validateFormatting(documentPath)
        allResults.errors.extend(formattingResults.errors)
        allResults.warnings.extend(formattingResults.warnings)
        allResults.suggestions.extend(formattingResults.suggestions)
    
    // Run structure validation
    if options.checkStructure:
        structureResults = validateStructure(documentPath, documentType)
        allResults.errors.extend(structureResults.errors)
        allResults.warnings.extend(structureResults.warnings)
        allResults.suggestions.extend(structureResults.suggestions)
    
    // Run link validation
    if options.checkLinks:
        linkResults = validateLinks(documentPath, options.repositoryRoot)
        allResults.errors.extend(linkResults.errors)
        allResults.warnings.extend(linkResults.warnings)
        allResults.suggestions.extend(linkResults.suggestions)
    
    // Run completeness validation
    if options.checkCompleteness:
        completenessResults = validateCompleteness(documentPath, documentType)
        allResults.errors.extend(completenessResults.errors)
        allResults.warnings.extend(completenessResults.warnings)
        allResults.suggestions.extend(completenessResults.suggestions)
        allResults.completenessScore = completenessResults.completenessScore
    
    // Generate report
    report = generateValidationReport(allResults, documentPath)
    
    // Save or display report
    if options.outputFile:
        writeFile(options.outputFile, report)
    else:
        print(report)
    
    // Return results for programmatic use
    return allResults

// Command-line interface
function main(args):
    options = parseArguments(args)
    
    if options.help:
        printUsage()
        return
    
    if not options.documentPath:
        print("Error: Document path required")
        return
    
    // Validate single document or directory
    if isDirectory(options.documentPath):
        documents = findAllMarkdownFiles(options.documentPath)
        for doc in documents:
            validateDocument(doc, options)
    else:
        validateDocument(options.documentPath, options)
```

## Configuration Files

### validation_rules.json

```json
{
  "formatting": {
    "maxHeadingDepth": 4,
    "bulletStyle": "-",
    "indentSpaces": 2,
    "requireCodeLanguage": true,
    "requireDescriptiveLinks": true
  },
  "structure": {
    "enforceOrder": false,
    "maxSectionDepth": 4,
    "requireRelatedDocs": true
  },
  "completeness": {
    "minimumWords": {
      "overview": 100,
      "requiredSection": 200,
      "optionalSection": 100
    },
    "requireExamples": true,
    "forbiddenPlaceholders": ["TODO", "TBD", "[TODO]", "[TBD]"]
  },
  "links": {
    "checkBidirectional": true,
    "checkOrphans": true,
    "allowAbsolutePaths": false
  }
}
```

### document_templates.json

```json
{
  "feature": {
    "requiredSections": [
      "Overview",
      "Business Value",
      "User Stories",
      "Technical Requirements"
    ],
    "optionalSections": [
      "Dependencies",
      "Implementation Considerations",
      "Examples"
    ],
    "requiresExamples": false,
    "minimumWords": {
      "required": 200,
      "optional": 100
    }
  },
  "use-case": {
    "requiredSections": [
      "Overview",
      "Industry Context",
      "User Persona",
      "Scenario Description",
      "Solution Overview",
      "Implementation Approach"
    ],
    "optionalSections": [
      "Benefits and ROI",
      "Success Metrics",
      "Example Workflow"
    ],
    "requiresExamples": true,
    "minimumWords": {
      "required": 200,
      "optional": 150
    }
  },
  "playbook": {
    "requiredSections": [
      "Overview",
      "Objectives",
      "Step-by-Step Process",
      "Roles and Responsibilities"
    ],
    "optionalSections": [
      "Prerequisites",
      "Timeline and Milestones",
      "Troubleshooting"
    ],
    "requiresExamples": false,
    "minimumWords": {
      "required": 200,
      "optional": 100
    }
  }
}
```

## Usage Examples

### Validate Single Document

```bash
# Basic validation
validate-doc features/core-domains/ai-interaction/README.md

# Full validation with all checks
validate-doc --all features/core-domains/ai-interaction/README.md

# Specific checks only
validate-doc --formatting --links features/core-domains/ai-interaction/README.md

# Output to file
validate-doc --output report.md features/core-domains/ai-interaction/README.md
```

### Validate Directory

```bash
# Validate all documents in directory
validate-doc --recursive features/

# Validate with summary report
validate-doc --recursive --summary features/

# Validate and fix auto-fixable issues
validate-doc --recursive --auto-fix features/
```

### Integration with CI/CD

```bash
# Run validation in CI pipeline
validate-doc --ci --fail-on-error features/

# Generate JSON report for processing
validate-doc --format json --output validation-results.json features/
```

## Related Documentation

- [Validation Procedures](validation-procedures.md)
- [Formatting Rules](formatting-rules.md)
- [Structure Validation](structure-validation.md)
- [Cross-Reference System](cross-reference-system.md)
- [Completeness Checklist](completeness-checklist.md)
