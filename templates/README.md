# Templates

> Standard templates for creating new Jump Contact client tickets

## Available Templates

### 6-Block Standard Template
**Location**: `/templates/6-block-standard/`

The standard template includes all 6 blocks with placeholder content that can be customized for any client:

1. **Header Block** - Business branding and logo
2. **Status Bar Block** - Live time, weather, and office status
3. **Business Details Block** - Contact information
4. **Call Script Block** - Agent call flow and scripts
5. **Forms Block** - GHL form integration placeholder
6. **Warnings Block** - Critical protocols and compliance

## How to Use Templates

### Step 1: Copy Template
```bash
cp templates/6-block-standard/TEMPLATE_ALL_6_BLOCKS.md \
   clients/[industry]/[CLIENT_NAME]_ALL_6_BLOCKS.md
```

### Step 2: Customize Variables
Replace all placeholder values marked with `[PLACEHOLDER]`:

- `[BUSINESS_NAME]` → Client's business name
- `[LOGO_URL]` → Client's logo URL
- `[PRIMARY_PHONE]` → Primary phone number
- `[EMAIL]` → Contact email
- `[TIMEZONE]` → Business timezone
- `[LATITUDE]` → Business location latitude
- `[LONGITUDE]` → Business location longitude
- `[FORM_ID]` → GHL form ID

### Step 3: Industry-Specific Customization
Add industry-specific sections based on vertical:

- **Legal**: Add practice areas, conflict check protocols
- **Restoration**: Add damage types, insurance coordination
- **Construction**: Add licensing, permit requirements
- **Service**: Add service areas, scheduling

### Step 4: Test
- Render in browser
- Verify all placeholders are replaced
- Test click-to-copy functionality
- Verify live data displays

### Step 5: Deploy
Follow the [Deployment Guide](../docs/DEPLOYMENT.md) to deploy to GoHighLevel.

## Template Variables Reference

### Required Variables (Must Replace)
```
[BUSINESS_NAME]     - Full legal business name
[LOGO_URL]          - URL to business logo (SVG or PNG)
[PRIMARY_PHONE]     - Primary phone number (format: 5551234567)
[SECONDARY_PHONE]   - Secondary/backup phone number
[EMAIL]             - Contact email address
[WEBSITE]           - Website URL
[TIMEZONE]          - IANA timezone (e.g., 'America/New_York')
[LATITUDE]          - Location latitude for weather
[LONGITUDE]         - Location longitude for weather
[FORM_ID]           - GoHighLevel form ID
```

### Optional Variables (Customize as Needed)
```
[ADDRESS]           - Physical address (if applicable)
[BUSINESS_HOURS]    - Operating hours (e.g., "9 AM - 5 PM EST")
[SERVICE_AREA]      - Service coverage area
[EMERGENCY_PHONE]   - Emergency contact number
[LANGUAGE]          - Language support (English/Bilingual)
```

### Color Variables (Brand Customization)
```
--primary-color     - Main brand color
--secondary-color   - Secondary brand color
--success-color     - Success/positive actions (default: green)
--warning-color     - Warnings (default: yellow)
--danger-color      - Prohibited actions (default: red)
--text-color        - Main text color
--background-color  - Background color
```

## Creating Custom Templates

### Industry-Specific Templates
To create a new industry-specific template:

1. Copy the 6-block standard template
2. Add industry-specific sections
3. Include industry-specific warnings
4. Add compliance requirements
5. Save as `[INDUSTRY]_TEMPLATE_ALL_6_BLOCKS.md`

### Example: Legal Template
```
templates/legal-template/
└── LEGAL_TEMPLATE_ALL_6_BLOCKS.md
    - Includes conflict check protocols
    - Attorney-client privilege warnings
    - Retainer agreement process
    - Bar association compliance
```

### Example: Restoration Template
```
templates/restoration-template/
└── RESTORATION_TEMPLATE_ALL_6_BLOCKS.md
    - Includes emergency response protocols
    - Insurance coordination steps
    - Damage type triage
    - 24/7 availability scripts
```

## Template Best Practices

### 1. Use Consistent Placeholders
- Always use `[UPPERCASE_UNDERSCORES]` for variables
- Make placeholder names descriptive
- Include default values in comments

### 2. Include Helpful Comments
```html
<!-- Replace [LOGO_URL] with actual logo URL -->
<!-- Recommended logo size: 180px x 60px -->
<img src="[LOGO_URL]" alt="[BUSINESS_NAME] Logo">
```

### 3. Provide Examples
```html
<!-- Example: 'America/New_York' or 'America/Chicago' -->
timeZone: '[TIMEZONE]'
```

### 4. Document Required vs. Optional
```markdown
## Special Notes
- **Form ID**: [FORM_ID] (REQUIRED)
- **Primary Contact**: [PRIMARY_PHONE] (REQUIRED)
- **Emergency Contact**: [EMERGENCY_PHONE] (OPTIONAL)
```

### 5. Include Validation Hints
```html
<!-- Phone format: 10 digits, no formatting: 5551234567 -->
onclick="navigator.clipboard.writeText('[PRIMARY_PHONE]')"
```

## Template Maintenance

### Updating Templates
When updating templates:
1. Update the standard template first
2. Test changes thoroughly
3. Apply updates to industry-specific templates
4. Document changes in commit message
5. Update template version number

### Version History
- **v1.0** (2025-01-05): Initial 6-block standard template
- **v1.1** (TBD): Industry-specific template variants
- **v2.0** (TBD): Variable substitution automation

## Future Enhancements

### Planned Features
- [ ] Automated variable substitution script
- [ ] Visual template builder
- [ ] Industry-specific template library
- [ ] Multi-language template support
- [ ] Theme/color scheme templates

### Contribution Ideas
See [CONTRIBUTING.md](../CONTRIBUTING.md) for how to contribute new templates.

## Questions?

- **Email**: burke@jumpcontact.com
- **Documentation**: See [docs/](../docs/) for guides
- **Examples**: See [clients/](../clients/) for production examples
