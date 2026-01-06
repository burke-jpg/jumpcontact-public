# Contributing Guide

> How to add new clients to the Jump Contact ticket repository

## Table of Contents

1. [Overview](#overview)
2. [Repository Structure](#repository-structure)
3. [Adding a New Client](#adding-a-new-client)
4. [File Naming Conventions](#file-naming-conventions)
5. [Content Requirements](#content-requirements)
6. [Quality Standards](#quality-standards)
7. [Submission Process](#submission-process)

---

## Overview

This guide explains how to add new client tickets to the Jump Contact repository. All contributions should maintain the same quality, structure, and format as existing clients.

### Who Can Contribute

- Jump Contact team members
- Licensed white-label partners
- Approved consultants

### What to Contribute

- New client tickets (6-block HTML/CSS)
- Documentation improvements
- Bug fixes
- Template enhancements

---

## Repository Structure

```
jumpcontact-public/
├── clients/
│   ├── legal/                    # Law firms
│   ├── restoration/              # Restoration & disaster
│   ├── construction/             # Construction & trades
│   ├── service/                  # Home service businesses
│   └── professional-services/    # Professional services
│
├── docs/
│   ├── QUICKSTART.md
│   ├── DEPLOYMENT.md
│   └── ARCHITECTURE.md
│
├── templates/
│   └── 6-block-standard/
│
├── LICENSE
├── README.md
└── CONTRIBUTING.md (this file)
```

---

## Adding a New Client

### Step 1: Determine Industry Vertical

Place the client in the correct folder:

- **Legal** (`/clients/legal/`): Law firms, attorneys, legal services
- **Restoration** (`/clients/restoration/`): Water damage, fire restoration, disaster recovery
- **Construction** (`/clients/construction/`): General contractors, trades, builders
- **Service** (`/clients/service/`): Plumbing, HVAC, handyman, pools
- **Professional Services** (`/clients/professional-services/`): Consulting, accounting, architecture, etc.

### Step 2: Gather Client Information

Collect the following before starting:

#### Required Information
- [ ] Business legal name
- [ ] DBA (if different)
- [ ] Logo file (SVG, PNG) or URL
- [ ] Primary phone number
- [ ] Secondary/backup phone number (if applicable)
- [ ] Email address
- [ ] Website URL
- [ ] Physical address (if applicable)
- [ ] Business hours (with timezone)
- [ ] Emergency contact hierarchy
- [ ] GHL Form ID

#### Industry-Specific Information

**Legal Services:**
- [ ] Practice areas
- [ ] Bar association compliance requirements
- [ ] Conflict check protocols
- [ ] Retainer agreement process

**Restoration:**
- [ ] Types of damage handled (water, fire, mold, storm)
- [ ] Insurance coordination process
- [ ] Emergency response protocols
- [ ] 24/7 availability requirements

**Construction:**
- [ ] License numbers (if required)
- [ ] Types of projects
- [ ] Subcontractor coordination
- [ ] Permit requirements

**Home Services:**
- [ ] Service area (zip codes, cities)
- [ ] Pricing structure
- [ ] Scheduling availability
- [ ] Parts/materials process

### Step 3: Create the Client File

**File Name Format**: `[CLIENT_NAME]_ALL_6_BLOCKS.md`

**Examples**:
- `SMITH_LAW_ALL_6_BLOCKS.md`
- `ABC_RESTORATION_ALL_6_BLOCKS.md`
- `JOHNSON_CONSTRUCTION_ALL_6_BLOCKS.md`

### Step 4: Use the Standard Template

Copy the template from `/templates/6-block-standard/` and customize.

---

## File Naming Conventions

### Client Files
- **Format**: `[CLIENT_NAME]_ALL_6_BLOCKS.md`
- **Case**: UPPERCASE with underscores
- **Examples**:
  - ✅ `ACME_PLUMBING_ALL_6_BLOCKS.md`
  - ✅ `SMITH_AND_JONES_LAW_ALL_6_BLOCKS.md`
  - ❌ `acme-plumbing.md` (wrong case)
  - ❌ `Acme Plumbing All Blocks.md` (spaces, mixed case)

### Documentation Files
- **Format**: `TITLE.md`
- **Case**: UPPERCASE
- **Examples**: `QUICKSTART.md`, `DEPLOYMENT.md`

---

## Content Requirements

### Required Sections (All Clients)

Every client file MUST include:

#### 1. Special Notes Section
```markdown
# [CLIENT NAME] - All 6 Blocks

## Special Notes
- **Form ID**: [ghl-form-id]
- **Primary Contact**: (555) 123-4567
- **Emergency Contact**: (555) 987-6543
- **Business Hours**: Monday-Friday 9 AM - 5 PM EST
- **Language**: English / Bilingual (English & Spanish)
- **Industry**: [Legal/Restoration/Construction/Service/Professional]
```

#### 2. Block 1: Header
```html
<div class="ticket-header">
  <!-- Logo and branding -->
</div>
```

#### 3. Block 2: Status Bar
```html
<div class="status-bar">
  <!-- Time, weather, office status -->
</div>
```

#### 4. Block 3: Business Details
```html
<div class="business-details">
  <!-- Contact information -->
</div>
```

#### 5. Block 4: Call Script
```html
<div class="call-script">
  <!-- Agent scripts and call flow -->
</div>
```

#### 6. Block 5: Forms
```markdown
## BLOCK 5: Forms
[GHL Form will be inserted here - Form ID: abc123]
```

#### 7. Block 6: Warnings
```html
<div class="warnings">
  <!-- Critical protocols -->
</div>
```

### Optional Sections

#### Deployment Notes
```markdown
## Deployment Notes
- Date deployed: 2025-01-15
- GHL Sub-Account: client-subaccount-id
- Workflow Name: Main Inbound Calls
- Special configurations: [any unique setup]
```

#### Client-Specific Customizations
```markdown
## Customizations
- Custom color scheme: #1a73e8 (primary), #34a853 (success)
- Logo dimensions: 180px x 60px
- Timezone: America/New_York
- Weather location: New York, NY (40.7128, -74.0060)
```

---

## Quality Standards

### Code Quality

#### HTML
- ✅ Valid HTML5 syntax
- ✅ Semantic markup
- ✅ Proper indentation (2 spaces)
- ✅ Accessibility attributes (alt text, ARIA labels)
- ✅ No inline styles (use `<style>` blocks)

#### CSS
- ✅ Mobile-first responsive design
- ✅ Consistent class naming (BEM style preferred)
- ✅ CSS variables for colors/spacing
- ✅ Browser compatibility (modern browsers)

#### JavaScript
- ✅ Minimal usage (only for live data)
- ✅ Vanilla JS (no frameworks)
- ✅ Error handling (try/catch)
- ✅ Graceful degradation (fallbacks)

### Content Quality

#### Call Scripts
- ✅ Clear and concise language
- ✅ Professional tone
- ✅ Numbered steps
- ✅ Client-approved messaging
- ✅ Compliance-reviewed (if regulated industry)

#### Business Information
- ✅ Accurate contact information
- ✅ Current business hours
- ✅ Valid phone numbers (click-to-copy works)
- ✅ Accessible logo URLs
- ✅ Correct timezone

#### Warnings Section
- ✅ Critical protocols highlighted (red boxes)
- ✅ Required actions emphasized (green boxes)
- ✅ Emergency procedures clear
- ✅ Compliance warnings present

---

## Testing Checklist

Before submitting a new client, verify:

### Visual Testing
- [ ] All 6 blocks render correctly
- [ ] Logo displays properly
- [ ] Colors match brand guidelines
- [ ] Text is readable (no truncation)
- [ ] Mobile view works (responsive)
- [ ] No broken images or links

### Functional Testing
- [ ] Click-to-copy works on phone numbers
- [ ] Live clock displays correct time
- [ ] Weather shows correct location
- [ ] Office status calculates correctly
- [ ] Form ID is valid and exists in GHL

### Content Testing
- [ ] Business name is correct
- [ ] Phone numbers are accurate
- [ ] Email addresses are correct
- [ ] Business hours are accurate
- [ ] Emergency contacts are current
- [ ] Call scripts are client-approved

### Code Testing
- [ ] HTML validates (W3C validator)
- [ ] CSS has no syntax errors
- [ ] JavaScript has no console errors
- [ ] Works in Chrome, Firefox, Safari, Edge
- [ ] No accessibility violations

---

## Submission Process

### For Jump Contact Team Members

#### 1. Create Branch
```bash
git checkout -b client/[client-name]
```

#### 2. Add Client File
```bash
# Add file to correct industry folder
# Example: /clients/legal/SMITH_LAW_ALL_6_BLOCKS.md
```

#### 3. Test Locally
- Open file in browser
- Verify all blocks render
- Test all functionality
- Check mobile view

#### 4. Commit Changes
```bash
git add clients/[industry]/[CLIENT_NAME]_ALL_6_BLOCKS.md
git commit -m "Add [Client Name] - [Industry] vertical"
```

#### 5. Push to Repository
```bash
git push origin client/[client-name]
```

#### 6. Create Pull Request
- Title: `Add [Client Name] - [Industry]`
- Description: Include client details, deployment date, special notes
- Assign reviewer: Burke Campbell or designated team lead

#### 7. Address Review Feedback
- Make requested changes
- Update pull request
- Re-request review

#### 8. Merge to Main
- After approval, merge to main branch
- Delete feature branch
- Update production deployment tracker

### For External Contributors

#### 1. Fork Repository
- Fork this repository to your GitHub account

#### 2. Create Client File
- Add file to appropriate industry folder
- Follow all naming conventions and quality standards

#### 3. Submit Pull Request
- Create pull request from your fork
- Include detailed description
- Reference any related issues

#### 4. Review Process
- Jump Contact team will review
- May request changes
- Approval required before merge

---

## Common Mistakes to Avoid

### ❌ Don't Do This

**Wrong File Naming**:
```
clients/legal/smith-law.md          # Wrong: lowercase, hyphens
clients/legal/smith_law.html        # Wrong: .html extension
clients/legal/SMITH LAW.md          # Wrong: spaces
```

**Broken Phone Numbers**:
```html
<div>(555) 123-4567</div>           # Missing click-to-copy
<div onclick="">555-123-4567</div>  # Empty onclick
```

**Missing Special Notes**:
```markdown
# SMITH LAW - All 6 Blocks

[Starts with Block 1...]            # Wrong: No Special Notes section
```

**Hard-Coded Colors**:
```css
.header { background: #ff0000; }    # Wrong: Should use CSS variables
```

**Invalid HTML**:
```html
<div class="box">
  <p>Content
</div>                               # Wrong: Unclosed <p> tag
```

### ✅ Do This Instead

**Correct File Naming**:
```
clients/legal/SMITH_LAW_ALL_6_BLOCKS.md
```

**Proper Phone Numbers**:
```html
<div class="phone-number" onclick="navigator.clipboard.writeText('5551234567')">
  (555) 123-4567 📋
</div>
```

**Complete Special Notes**:
```markdown
# SMITH LAW - All 6 Blocks

## Special Notes
- **Form ID**: abc123xyz
- **Primary Contact**: (555) 123-4567
[etc...]
```

**CSS Variables**:
```css
:root {
  --primary-color: #1a73e8;
  --success-color: #34a853;
}
.header { background: var(--primary-color); }
```

**Valid HTML**:
```html
<div class="box">
  <p>Content</p>
</div>
```

---

## Style Guide

### Markdown Formatting

**Headers**:
```markdown
# H1 - Client Name
## H2 - Block Title
### H3 - Section Title
```

**Code Blocks**:
````markdown
```html
<div class="example">HTML code</div>
```

```css
.example { color: blue; }
```

```javascript
const example = 'JavaScript code';
```
````

**Lists**:
```markdown
- Unordered list item
- Another item
  - Nested item

1. Ordered list item
2. Another item
```

### HTML Formatting

**Indentation**: 2 spaces
```html
<div class="container">
  <div class="item">
    <p>Content</p>
  </div>
</div>
```

**Class Names**: BEM style preferred
```html
<div class="ticket-header">
  <div class="ticket-header__logo">
    <img class="ticket-header__logo-image" src="logo.svg">
  </div>
</div>
```

### CSS Formatting

**Declaration Order**:
1. Positioning
2. Box model
3. Typography
4. Visual
5. Misc

```css
.example {
  /* Positioning */
  position: relative;
  top: 0;
  
  /* Box model */
  display: flex;
  width: 100%;
  padding: 1rem;
  
  /* Typography */
  font-size: 1rem;
  line-height: 1.5;
  
  /* Visual */
  background: white;
  border: 1px solid #ddd;
  
  /* Misc */
  cursor: pointer;
}
```

---

## Questions?

- **Email**: burke@jumpcontact.com
- **GitHub Issues**: Open an issue for questions
- **Documentation**: Review existing clients as examples

---

## License

By contributing to this repository, you agree that your contributions will be licensed under the Apache 2.0 License.

See [LICENSE](LICENSE) for details.

---

**Thank you for contributing to Jump Contact! 🎉**
