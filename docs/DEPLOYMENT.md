# Complete Deployment Guide

> Comprehensive instructions for deploying Jump Contact tickets in GoHighLevel

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Pre-Deployment Planning](#pre-deployment-planning)
3. [GHL Environment Setup](#ghl-environment-setup)
4. [HTML Block Deployment](#html-block-deployment)
5. [Form Configuration](#form-configuration)
6. [Call Routing Setup](#call-routing-setup)
7. [Testing & Quality Assurance](#testing--quality-assurance)
8. [Production Deployment](#production-deployment)
9. [Post-Deployment Monitoring](#post-deployment-monitoring)
10. [Troubleshooting](#troubleshooting)

---

## Prerequisites

### Required Access
- ✅ GoHighLevel account with admin privileges
- ✅ Access to client's sub-account
- ✅ Permission to modify workflows and forms
- ✅ Access to client assets (logo, contact info)

### Required Information
- ✅ Client's business hours and timezone
- ✅ Emergency contact hierarchy
- ✅ Service area coverage (for weather/location)
- ✅ Language requirements (English-only vs. bilingual)
- ✅ Industry-specific compliance requirements

### Technical Requirements
- ✅ Modern web browser (Chrome, Firefox, Safari, Edge)
- ✅ Stable internet connection
- ✅ Test phone for call testing

---

## Pre-Deployment Planning

### 1. Client Discovery (30-60 minutes)

Gather the following information from the client:

#### Business Information
- Legal business name
- DBA (Doing Business As) name
- Logo file (SVG, PNG, or URL)
- Primary phone number
- Secondary/backup phone number
- Email address
- Website URL
- Physical address (if applicable)

#### Operational Details
- Business hours (with timezone)
- After-hours protocol (voicemail, emergency line, etc.)
- Emergency contact hierarchy
- Peak call times
- Average call duration
- Expected call volume

#### Service Requirements
- Primary services offered
- Service area (zip codes, cities, states)
- Language requirements
- Industry-specific regulations
- Compliance requirements (HIPAA, etc.)

### 2. Vertical-Specific Requirements

#### Legal Services
- Bar association compliance
- Conflict of interest checks
- Intake form requirements
- Retainer agreement protocols

#### Restoration/Disaster
- Emergency response protocols
- Insurance coordination
- 24/7 availability requirements
- Mitigation vs. restoration triage

#### Construction/Trades
- Licensing verification
- Permit requirements
- Subcontractor coordination
- Payment/deposit protocols

#### Home Services
- Service area boundaries
- Pricing transparency
- Scheduling availability
- Parts/materials coordination

---

## GHL Environment Setup

### 1. Create Sub-Account (If New Client)

1. Navigate to **Agency Dashboard**
2. Click **Add Location**
3. Enter client information:
   - Business name
   - Contact email
   - Phone number
   - Timezone
4. Configure sub-account settings
5. Enable required features

### 2. Set Up Phone Number

1. Navigate to **Settings** → **Phone Numbers**
2. Purchase or port client phone number
3. Configure number settings:
   - Call forwarding
   - Voicemail
   - Call recording (if required)
   - SMS capabilities

### 3. Create Custom Fields

Navigate to **Settings** → **Custom Fields** and create:

#### Required Custom Fields
- `lead_source` (dropdown)
- `service_type` (dropdown)
- `urgency_level` (dropdown: Normal, Urgent, Emergency)
- `preferred_contact_method` (dropdown: Phone, Email, SMS)
- `best_time_to_call` (text)

#### Industry-Specific Custom Fields

**Legal:**
- `case_type`
- `opposing_party`
- `statute_of_limitations_date`

**Restoration:**
- `damage_type`
- `insurance_carrier`
- `claim_number`

**Construction:**
- `project_type`
- `project_timeline`
- `budget_range`

**Home Services:**
- `service_address`
- `property_type`
- `access_instructions`

---

## HTML Block Deployment

### Block-by-Block Deployment Process

#### Block 1: Header
**Purpose**: Displays business logo, name, and branding

1. Open client's `*_ALL_6_BLOCKS.md` file
2. Locate `## BLOCK 1: Header`
3. Copy entire HTML content (from `<div class="ticket-header">` to closing `</div>`)
4. In GHL workflow, add **Custom HTML** element
5. Paste content
6. Name element: "Header"
7. **Customization points**:
   - Replace logo URL if needed
   - Verify business name is correct
   - Check brand color hex codes

#### Block 2: Status Bar
**Purpose**: Shows live time, weather, and office status

1. Locate `## BLOCK 2: Status Bar`
2. Copy entire HTML content
3. Add **Custom HTML** element in GHL
4. Name element: "Status Bar"
5. **Critical settings**:
   - Verify timezone (line ~15: `timeZone: 'America/Chicago'`)
   - Verify coordinates for weather (line ~45: `lat=XX.XX&lon=YY.YY`)
   - Verify business hours (line ~60)
6. **Weather API**: Uses Open-Meteo (free, no API key needed)

#### Block 3: Business Details
**Purpose**: Contact information and quick-copy functionality

1. Locate `## BLOCK 3: Business Details`
2. Copy entire HTML content
3. Add **Custom HTML** element
4. Name element: "Business Details"
5. **Verify accuracy**:
   - Phone numbers (click-to-copy functionality)
   - Email address
   - Physical address (if applicable)
   - Website URL
   - Service area

#### Block 4: Call Script
**Purpose**: Agent call flow and scripting

1. Locate `## BLOCK 4: Call Script`
2. Copy entire HTML content
3. Add **Custom HTML** element
4. Name element: "Call Script"
5. **Customization**:
   - Review greeting script for brand voice
   - Verify call flow logic matches client process
   - Check for industry-specific compliance language
   - Confirm objection handling scripts

#### Block 5: Forms (Placeholder)
**Purpose**: Marks where GHL form will be inserted

1. Locate `## BLOCK 5: Forms`
2. Copy placeholder HTML (if present)
3. **Note**: Actual GHL form added separately (see Form Configuration section)

#### Block 6: Warnings
**Purpose**: Critical protocols and compliance warnings

1. Locate `## BLOCK 6: Warnings`
2. Copy entire HTML content
3. Add **Custom HTML** element
4. Name element: "Warnings"
5. **Critical review**:
   - Red warnings (prohibited actions)
   - Green highlights (required actions)
   - Emergency protocols
   - Compliance requirements

---

## Form Configuration

### 1. Locate Required Form ID

In the client's `*_ALL_6_BLOCKS.md` file, find **Special Notes** section:
```
Form ID: [alphanumeric-id]
```

### 2. Verify Form Exists in GHL

1. Navigate to **Marketing** → **Forms**
2. Search for Form ID
3. If form exists, verify fields match requirements
4. If form doesn't exist, create new form (see below)

### 3. Create Form (If Needed)

#### Standard Form Fields (All Clients)
- First Name (required)
- Last Name (required)
- Phone Number (required)
- Email Address (required)
- Service Type (dropdown, required)
- Message/Description (textarea)

#### Legal Services Additional Fields
- Case Type (dropdown)
- Incident Date
- Opposing Party Name
- Preferred Attorney

#### Restoration Additional Fields
- Type of Damage (dropdown: Water, Fire, Mold, Storm)
- Insurance Carrier
- Claim Number
- Emergency? (Yes/No)

#### Construction Additional Fields
- Project Type (dropdown)
- Timeline
- Budget Range
- Property Address

#### Home Services Additional Fields
- Service Address
- Preferred Date/Time
- Property Type
- Access Instructions

### 4. Configure Form Settings

1. **Form Appearance**:
   - Match brand colors
   - Mobile-responsive layout
   - Clear field labels

2. **Form Validation**:
   - Required field enforcement
   - Phone number formatting
   - Email validation

3. **Form Actions**:
   - Create contact
   - Create opportunity
   - Assign to pipeline
   - Send notification
   - Trigger workflow

### 5. Embed Form in Workflow

1. In GHL workflow, add **Form** element
2. Select form by ID
3. Position between Block 4 (Call Script) and Block 6 (Warnings)
4. Configure form submission actions

---

## Call Routing Setup

### 1. Configure Business Hours

1. Navigate to **Settings** → **Business Hours**
2. Set operational hours by day
3. Configure timezone
4. Set holiday schedule

### 2. Emergency Contact Hierarchy

From client's Special Notes, set up contact forwarding:

**Example Hierarchy**:
1. Primary: Main office line
2. Secondary: Manager cell phone
3. Tertiary: After-hours service
4. Emergency: Owner direct line

### 3. Call Flow Logic

#### During Business Hours
```
Incoming Call → GHL Workflow → Agent Ticket Displays → Agent Answers
```

#### After Business Hours
```
Incoming Call → Check Emergency Flag → Route Accordingly
- Emergency: Forward to emergency contact
- Non-Emergency: Voicemail with callback promise
```

### 4. Voicemail Configuration

1. Record professional greeting
2. Set voicemail transcription (if available)
3. Configure voicemail notifications
4. Set callback workflow

---

## Testing & Quality Assurance

### Pre-Production Testing Checklist

#### Visual Testing
- [ ] All 6 blocks display correctly
- [ ] Logo appears and is properly sized
- [ ] Colors match brand guidelines
- [ ] Text is readable and properly formatted
- [ ] No broken images or missing content
- [ ] Mobile view displays correctly
- [ ] Click-to-copy buttons work
- [ ] Live data displays (time, weather, status)

#### Functional Testing
- [ ] Form submits successfully
- [ ] Form data creates contact in GHL
- [ ] Contact routing works correctly
- [ ] Emergency escalation functions
- [ ] After-hours routing works
- [ ] Voicemail records properly
- [ ] Notifications send correctly
- [ ] Call recording works (if enabled)

#### Content Accuracy Testing
- [ ] Business name is correct
- [ ] Phone numbers are accurate
- [ ] Email addresses are correct
- [ ] Address is accurate
- [ ] Business hours match reality
- [ ] Emergency contacts are current
- [ ] Call scripts match brand voice
- [ ] Compliance warnings are present

#### Call Flow Testing
1. Make test call during business hours
2. Verify ticket displays on agent screen
3. Test form submission
4. Verify data accuracy in GHL
5. Make test call after hours
6. Verify voicemail/routing
7. Test emergency call scenario
8. Verify escalation works

---

## Production Deployment

### Deployment Day Checklist

#### Morning of Deployment (T-4 hours)
- [ ] Final review of all content
- [ ] Backup current workflow (if replacing existing)
- [ ] Notify agents of deployment time
- [ ] Prepare rollback plan
- [ ] Verify test calls successful

#### Deployment Window (T-0)
- [ ] Activate new workflow in GHL
- [ ] Verify phone routing to new workflow
- [ ] Assign agents to workflow
- [ ] Monitor first 3 calls closely
- [ ] Check for any errors

#### Post-Deployment (T+1 hour)
- [ ] Verify 5+ successful calls
- [ ] Check agent feedback
- [ ] Review any errors or issues
- [ ] Make quick fixes if needed
- [ ] Document any changes

### Agent Training

#### Pre-Deployment Training (1 hour)
1. **Ticket Walkthrough** (15 min)
   - Show all 6 blocks
   - Explain each section
   - Demonstrate click-to-copy
   - Show form submission

2. **Call Flow Practice** (30 min)
   - Role-play scenarios
   - Practice using scripts
   - Test emergency protocols
   - Review warnings section

3. **Q&A and Troubleshooting** (15 min)
   - Answer agent questions
   - Address concerns
   - Clarify protocols
   - Distribute quick reference

#### Quick Reference Card
Create one-page guide with:
- Emergency contact numbers
- Common call scenarios
- Key warnings/protocols
- Troubleshooting tips

---

## Post-Deployment Monitoring

### First 24 Hours

**Metrics to track**:
- Total calls received
- Successful call completions
- Form submission rate
- Average call duration
- Agent feedback score
- Technical issues reported

**Monitoring checklist**:
- [ ] Review first 10 calls
- [ ] Check for any errors
- [ ] Gather agent feedback
- [ ] Verify data accuracy
- [ ] Monitor client satisfaction

### First Week

**Weekly review meeting**:
1. Review metrics
2. Identify any issues
3. Gather agent suggestions
4. Make necessary adjustments
5. Document improvements

### Ongoing Optimization

**Monthly review**:
- Call volume trends
- Conversion rates
- Agent efficiency
- Client satisfaction
- System updates needed

---

## Troubleshooting

### Common Issues and Solutions

#### Issue: "Ticket not displaying"
**Symptoms**: Blank screen when call comes in  
**Causes**: Workflow not activated, agent not assigned  
**Fix**:
1. Verify workflow is active in GHL
2. Check agent assignment
3. Verify phone number routing
4. Clear browser cache

#### Issue: "Form not submitting"
**Symptoms**: Form button doesn't work  
**Causes**: Form ID mismatch, validation errors  
**Fix**:
1. Verify Form ID matches Special Notes
2. Check required fields are filled
3. Verify form actions configured
4. Test in different browser

#### Issue: "Weather not displaying"
**Symptoms**: Weather section shows error  
**Causes**: Invalid coordinates, API timeout  
**Fix**:
1. Verify latitude/longitude in Block 2
2. Check internet connection
3. Test Open-Meteo API directly
4. Use fallback static weather

#### Issue: "Time showing wrong timezone"
**Symptoms**: Clock shows incorrect time  
**Causes**: Wrong timezone setting in Block 2  
**Fix**:
1. Find timezone setting (line ~15 in Block 2)
2. Update to correct timezone (e.g., 'America/New_York')
3. Save and refresh
4. Verify time is correct

#### Issue: "Click-to-copy not working"
**Symptoms**: Can't copy phone numbers  
**Causes**: Browser incompatibility, old browser  
**Fix**:
1. Update browser to latest version
2. Enable clipboard permissions
3. Test in Chrome/Firefox
4. Manual copy if needed

#### Issue: "Logo not appearing"
**Symptoms**: Broken image in header  
**Causes**: Invalid logo URL, CORS issue  
**Fix**:
1. Verify logo URL is accessible
2. Check logo file format (PNG, SVG, JPG)
3. Upload logo to GHL media library
4. Update URL in Block 1

---

## Support and Resources

### Documentation
- [Quick Start Guide](QUICKSTART.md) - 15-minute deployment
- [Architecture Documentation](ARCHITECTURE.md) - System design
- [Contributing Guide](../CONTRIBUTING.md) - How to add clients

### Contact
- **Email**: burke@jumpcontact.com
- **Repository**: https://github.com/burke-jpg/jumpcontact-public
- **Issues**: Report bugs via GitHub Issues

### External Resources
- [GoHighLevel Documentation](https://help.gohighlevel.com/)
- [Open-Meteo API Docs](https://open-meteo.com/en/docs)
- [HTML/CSS Reference](https://developer.mozilla.org/en-US/docs/Web)

---

## Deployment Timeline Summary

| Phase | Duration | Key Activities |
|-------|----------|---------------|
| **Planning** | 2-4 hours | Client discovery, requirements gathering |
| **Setup** | 1-2 hours | GHL environment, custom fields, forms |
| **Deployment** | 30-45 min | HTML blocks, form integration, routing |
| **Testing** | 1-2 hours | Visual, functional, call flow testing |
| **Training** | 1 hour | Agent walkthrough and practice |
| **Go-Live** | 15 min | Activate workflow, monitor calls |
| **Monitoring** | Ongoing | First 24 hours intensive, then weekly |

**Total Time to Production**: 6-10 hours (including planning and training)

---

**🎉 You now have everything needed for a successful deployment!**
