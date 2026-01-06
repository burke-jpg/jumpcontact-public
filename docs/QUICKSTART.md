# Quick Start Guide - 15-Minute Deployment

> Deploy your first Jump Contact ticket in GoHighLevel in under 15 minutes

## Prerequisites

- GoHighLevel account with admin access
- Access to the client's sub-account
- Client's ALL_BLOCKS.md file from this repository

---

## Step 1: Choose Your Client (2 minutes)

1. Navigate to the appropriate client folder:
   - **Legal**: `/clients/legal/`
   - **Restoration**: `/clients/restoration/`
   - **Construction**: `/clients/construction/`
   - **Service**: `/clients/service/`
   - **Professional Services**: `/clients/professional-services/`

2. Open the client's `*_ALL_6_BLOCKS.md` file
3. Review the **Special Notes** section at the top for:
   - Form ID requirements
   - Emergency contact hierarchies
   - Language requirements (English-only vs. bilingual)
   - Client-specific protocols

---

## Step 2: Create Custom HTML Blocks in GHL (5 minutes)

### Navigate to Workflow Builder
1. Log into GoHighLevel
2. Go to **Settings** → **Phone System** → **Call Flow**
3. Find your target workflow
4. Click **Edit Workflow**

### Add Custom HTML Blocks
1. Click **Add Element** → **Custom HTML**
2. You'll create **6 Custom HTML blocks** (one for each block)

### Add Block 1: Header
1. Copy everything under `## BLOCK 1: Header` from the markdown file
2. Paste into the Custom HTML block
3. Name the block: "Header"
4. Save

### Add Block 2: Status Bar
1. Copy everything under `## BLOCK 2: Status Bar`
2. Paste into new Custom HTML block
3. Name the block: "Status Bar"
4. Save

### Add Blocks 3-6: Repeat Process
- **Block 3**: Business Details
- **Block 4**: Call Script
- **Block 5**: Forms (placeholder - actual form added separately)
- **Block 6**: Warnings

---

## Step 3: Add the GHL Form (3 minutes)

### Locate Form ID
1. In the `*_ALL_6_BLOCKS.md` file, find the **Special Notes** section
2. Look for: `Form ID: [form-id-here]`
3. Copy the Form ID

### Add Form to Workflow
1. In the GHL workflow, click **Add Element** → **Form**
2. Select the form using the Form ID from Special Notes
3. Position it between Block 4 (Call Script) and Block 6 (Warnings)
4. Save

**Note**: If no form exists yet, create one in GHL Forms with required fields listed in Special Notes.

---

## Step 4: Configure Call Routing (2 minutes)

### Set Up Contact Routing
From the **Special Notes** section, configure:

1. **Emergency Contacts**:
   - Set primary contact number
   - Set backup contact number (if applicable)
   - Configure emergency escalation rules

2. **Business Hours**:
   - Set office hours (usually 9 AM - 5 PM local time)
   - Configure after-hours routing
   - Set timezone

3. **Language Routing** (if bilingual):
   - Configure Spanish language detection
   - Set bilingual agent requirements

---

## Step 5: Test the Ticket (2 minutes)

### Visual Check
1. Preview the workflow in GHL
2. Verify all 6 blocks display correctly
3. Check:
   - ✅ Header shows business logo and name
   - ✅ Status bar shows live time and office status
   - ✅ Business details are accurate
   - ✅ Call script is clear and formatted
   - ✅ Form displays properly
   - ✅ Warnings are visible and color-coded

### Functional Check
1. Make a test call to the workflow
2. Verify:
   - ✅ Ticket loads on agent screen
   - ✅ Click-to-copy works on phone numbers
   - ✅ Form submits successfully
   - ✅ Live data displays (time, weather, status)
   - ✅ Mobile view works (if agents use mobile)

---

## Step 6: Deploy to Production (1 minute)

1. Activate the workflow in GHL
2. Assign agents to the workflow
3. Notify team the ticket is live
4. Monitor first few calls for any issues

---

## Verification Checklist

Before declaring deployment complete:

- [ ] All 6 HTML blocks are present and visible
- [ ] Form is embedded and functional
- [ ] Emergency contacts are correct
- [ ] Business hours are configured
- [ ] Language settings match requirements
- [ ] Test call completed successfully
- [ ] Agents have been trained/notified
- [ ] Mobile view tested (if applicable)

---

## Common Issues & Quick Fixes

### Issue: "Form not displaying"
**Fix**: Verify Form ID in Special Notes matches the form in GHL

### Issue: "Time showing wrong timezone"
**Fix**: Check office timezone in Business Details block (Block 3)

### Issue: "Logo not appearing"
**Fix**: Verify logo URL in Header block is accessible

### Issue: "Weather showing wrong location"
**Fix**: Verify latitude/longitude coordinates in Status Bar block

### Issue: "Click-to-copy not working"
**Fix**: This is CSS-only, works in modern browsers. Check browser compatibility.

---

## Next Steps

**After successful deployment:**

1. **Monitor Performance**: Track first 24 hours of calls
2. **Gather Feedback**: Get agent input on usability
3. **Optimize**: Make adjustments based on real usage
4. **Document Changes**: Update Special Notes if protocols change

**Need help?**
- Review [Full Deployment Guide](DEPLOYMENT.md) for advanced configuration
- Check [Architecture Documentation](ARCHITECTURE.md) to understand the system
- Email: burke@jumpcontact.com

---

## Time Breakdown

- **Step 1**: Choose Client - 2 min
- **Step 2**: Add HTML Blocks - 5 min
- **Step 3**: Add Form - 3 min
- **Step 4**: Configure Routing - 2 min
- **Step 5**: Test - 2 min
- **Step 6**: Deploy - 1 min

**Total**: 15 minutes ⏱️

---

**🎉 Congratulations! Your ticket is now live and operational.**
