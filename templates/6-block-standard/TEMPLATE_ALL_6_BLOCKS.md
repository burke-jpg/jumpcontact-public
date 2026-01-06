# [BUSINESS_NAME] - All 6 Blocks

## Special Notes
- **Form ID**: [FORM_ID]
- **Primary Contact**: [PRIMARY_PHONE]
- **Secondary Contact**: [SECONDARY_PHONE]
- **Emergency Contact**: [EMERGENCY_PHONE]
- **Business Hours**: [BUSINESS_HOURS] (e.g., "Monday-Friday 9 AM - 5 PM EST")
- **Language**: [LANGUAGE] (English / Bilingual: English & Spanish)
- **Industry**: [INDUSTRY] (Legal / Restoration / Construction / Service / Professional Services)
- **Timezone**: [TIMEZONE] (e.g., 'America/New_York', 'America/Chicago', 'America/Los_Angeles')
- **Location**: [CITY], [STATE] ([LATITUDE], [LONGITUDE])

---

## BLOCK 1: Header

```html
<style>
  :root {
    --primary-color: #1a73e8;
    --secondary-color: #34a853;
    --success-color: #34a853;
    --warning-color: #fbbc04;
    --danger-color: #ea4335;
    --text-color: #202124;
    --background-color: #ffffff;
  }

  .ticket-header {
    display: flex;
    align-items: center;
    padding: 1rem;
    background: var(--primary-color);
    color: white;
    border-radius: 8px 8px 0 0;
  }

  .ticket-header__logo {
    height: 60px;
    margin-right: 1rem;
  }

  .ticket-header__title {
    font-size: 1.5rem;
    font-weight: bold;
    margin: 0;
  }
</style>

<div class="ticket-header">
  <!-- Replace [LOGO_URL] with actual logo URL (recommended: 180px x 60px) -->
  <img src="[LOGO_URL]" alt="[BUSINESS_NAME] Logo" class="ticket-header__logo">
  <h1 class="ticket-header__title">[BUSINESS_NAME]</h1>
</div>
```

---

## BLOCK 2: Status Bar

```html
<style>
  .status-bar {
    display: flex;
    justify-content: space-between;
    padding: 0.75rem 1rem;
    background: #f8f9fa;
    border-bottom: 2px solid #e0e0e0;
    font-size: 0.9rem;
  }

  .status-bar__item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .status-bar__office-open {
    color: var(--success-color);
    font-weight: bold;
  }

  .status-bar__office-closed {
    color: var(--danger-color);
    font-weight: bold;
  }
</style>

<div class="status-bar">
  <div class="status-bar__item">
    <span id="current-time">--:-- --</span>
  </div>
  <div class="status-bar__item">
    <span id="current-weather">-- °F</span>
  </div>
  <div class="status-bar__item">
    <span id="office-status">CHECKING...</span>
  </div>
</div>

<script>
  // Update time every second
  function updateTime() {
    const now = new Date();
    // Replace [TIMEZONE] with client's timezone
    const options = { 
      timeZone: '[TIMEZONE]',
      hour: 'numeric',
      minute: '2-digit',
      hour12: true
    };
    const timeString = now.toLocaleTimeString('en-US', options);
    document.getElementById('current-time').textContent = timeString;
  }
  
  // Fetch weather data
  function updateWeather() {
    // Replace [LATITUDE] and [LONGITUDE] with client's coordinates
    fetch('https://api.open-meteo.com/v1/forecast?latitude=[LATITUDE]&longitude=[LONGITUDE]&current_weather=true&temperature_unit=fahrenheit')
      .then(response => response.json())
      .then(data => {
        const temp = Math.round(data.current_weather.temperature);
        const weatherCode = data.current_weather.weathercode;
        const weatherIcon = weatherCode < 3 ? '☀️' : weatherCode < 50 ? '⛅' : '🌧️';
        document.getElementById('current-weather').textContent = `${temp}°F ${weatherIcon}`;
      })
      .catch(() => {
        document.getElementById('current-weather').textContent = '-- °F';
      });
  }
  
  // Check office status based on business hours
  function updateOfficeStatus() {
    const now = new Date();
    const options = { timeZone: '[TIMEZONE]', weekday: 'long', hour: 'numeric', hour12: false };
    const timeInfo = new Intl.DateTimeFormat('en-US', options).format(now);
    const day = timeInfo.split(',')[0];
    const hour = parseInt(timeInfo.split(',')[1].trim());
    
    // Customize business hours as needed
    const isWeekday = !['Saturday', 'Sunday'].includes(day);
    const isBusinessHours = hour >= 9 && hour < 17; // 9 AM - 5 PM
    
    const statusElement = document.getElementById('office-status');
    if (isWeekday && isBusinessHours) {
      statusElement.textContent = 'OFFICE OPEN ✅';
      statusElement.className = 'status-bar__office-open';
    } else {
      statusElement.textContent = 'OFFICE CLOSED ⏰';
      statusElement.className = 'status-bar__office-closed';
    }
  }
  
  // Initialize
  updateTime();
  updateWeather();
  updateOfficeStatus();
  
  // Update every minute
  setInterval(() => {
    updateTime();
    updateOfficeStatus();
  }, 60000);
  
  // Update weather every 10 minutes
  setInterval(updateWeather, 600000);
</script>
```

---

## BLOCK 3: Business Details

```html
<style>
  .business-details {
    padding: 1rem;
    background: white;
  }

  .business-details__grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }

  .business-details__item {
    padding: 0.75rem;
    background: #f8f9fa;
    border-radius: 4px;
  }

  .business-details__label {
    font-size: 0.75rem;
    color: #5f6368;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 0.25rem;
  }

  .business-details__value {
    font-size: 1rem;
    color: var(--text-color);
    font-weight: 500;
  }

  .business-details__phone {
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }

  .business-details__phone:hover {
    color: var(--primary-color);
  }
</style>

<div class="business-details">
  <h2>Business Information</h2>
  
  <div class="business-details__grid">
    <div class="business-details__item">
      <div class="business-details__label">Primary Phone</div>
      <div class="business-details__value">
        <!-- Replace [PRIMARY_PHONE] with 10-digit phone number (no formatting) -->
        <span class="business-details__phone" onclick="navigator.clipboard.writeText('[PRIMARY_PHONE]')">
          [PRIMARY_PHONE_FORMATTED] 📋
        </span>
      </div>
    </div>
    
    <div class="business-details__item">
      <div class="business-details__label">Secondary Phone</div>
      <div class="business-details__value">
        <span class="business-details__phone" onclick="navigator.clipboard.writeText('[SECONDARY_PHONE]')">
          [SECONDARY_PHONE_FORMATTED] 📋
        </span>
      </div>
    </div>
    
    <div class="business-details__item">
      <div class="business-details__label">Email</div>
      <div class="business-details__value">[EMAIL]</div>
    </div>
    
    <div class="business-details__item">
      <div class="business-details__label">Website</div>
      <div class="business-details__value">
        <a href="[WEBSITE]" target="_blank">[WEBSITE]</a>
      </div>
    </div>
    
    <!-- Optional: Add if business has physical location -->
    <div class="business-details__item">
      <div class="business-details__label">Address</div>
      <div class="business-details__value">[ADDRESS]</div>
    </div>
    
    <div class="business-details__item">
      <div class="business-details__label">Service Area</div>
      <div class="business-details__value">[SERVICE_AREA]</div>
    </div>
  </div>
</div>
```

---

## BLOCK 4: Call Script

```html
<style>
  .call-script {
    padding: 1rem;
    background: white;
  }

  .call-script__section {
    margin-bottom: 1.5rem;
    padding: 1rem;
    background: #f8f9fa;
    border-radius: 4px;
  }

  .call-script__section h3 {
    margin-top: 0;
    color: var(--primary-color);
  }

  .call-script__required {
    background: #e8f5e9;
    border-left: 4px solid var(--success-color);
    padding: 0.75rem;
    margin: 0.5rem 0;
  }

  .call-script__optional {
    background: #fff3e0;
    border-left: 4px solid var(--warning-color);
    padding: 0.75rem;
    margin: 0.5rem 0;
  }

  .call-script__list {
    margin: 0.5rem 0;
    padding-left: 1.5rem;
  }
</style>

<div class="call-script">
  <h2>Call Flow</h2>
  
  <div class="call-script__section">
    <h3>1. Greeting</h3>
    <div class="call-script__required">
      <strong>REQUIRED:</strong> "Thank you for calling [BUSINESS_NAME]. This is [Agent Name]. How may I help you today?"
    </div>
  </div>
  
  <div class="call-script__section">
    <h3>2. Qualification Questions</h3>
    <ul class="call-script__list">
      <li>What type of service are you looking for?</li>
      <li>When do you need this service?</li>
      <li>What is your location/address?</li>
      <li>Have you worked with us before?</li>
    </ul>
  </div>
  
  <div class="call-script__section">
    <h3>3. Information Collection</h3>
    <p>Complete the form below with caller's information.</p>
    <div class="call-script__required">
      <strong>REQUIRED FIELDS:</strong>
      <ul class="call-script__list">
        <li>Full name</li>
        <li>Phone number (verify for callback)</li>
        <li>Email address</li>
        <li>Service type</li>
        <li>Brief description of need</li>
      </ul>
    </div>
  </div>
  
  <div class="call-script__section">
    <h3>4. Next Steps</h3>
    <div class="call-script__optional">
      <p><strong>Standard Response:</strong></p>
      <p>"Thank you for the information. [Next step based on service type]. You should expect [callback/visit/quote] within [timeframe]. Is there anything else I can help you with today?"</p>
    </div>
  </div>
  
  <div class="call-script__section">
    <h3>5. Closing</h3>
    <div class="call-script__required">
      <strong>REQUIRED:</strong> "Thank you for calling [BUSINESS_NAME]. Have a great day!"
    </div>
  </div>
</div>
```

---

## BLOCK 5: Forms

**Note**: This is a placeholder. The actual GHL form will be inserted here during deployment.

```markdown
## FORM INTEGRATION POINT

**Form ID**: [FORM_ID]

The GHL form should be positioned here with the following fields:
- First Name (required)
- Last Name (required)
- Phone Number (required)
- Email Address (required)
- Service Type (dropdown, required)
- Message/Description (textarea)

Add industry-specific fields as needed.
```

---

## BLOCK 6: Warnings

```html
<style>
  .warnings {
    padding: 1rem;
    background: white;
  }

  .warning-box {
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 4px;
    border-left: 4px solid;
  }

  .warning-box--danger {
    background: #fce4ec;
    border-left-color: var(--danger-color);
  }

  .warning-box--success {
    background: #e8f5e9;
    border-left-color: var(--success-color);
  }

  .warning-box--warning {
    background: #fff3e0;
    border-left-color: var(--warning-color);
  }

  .warning-box h4 {
    margin-top: 0;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .warning-box ul {
    margin: 0.5rem 0;
    padding-left: 1.5rem;
  }
</style>

<div class="warnings">
  <h2>Critical Protocols & Warnings</h2>
  
  <div class="warning-box warning-box--danger">
    <h4>❌ NEVER DO THIS:</h4>
    <ul>
      <li>[Add prohibited action #1]</li>
      <li>[Add prohibited action #2]</li>
      <li>[Add prohibited action #3]</li>
    </ul>
  </div>
  
  <div class="warning-box warning-box--success">
    <h4>✅ ALWAYS DO THIS:</h4>
    <ul>
      <li>[Add required action #1]</li>
      <li>[Add required action #2]</li>
      <li>[Add required action #3]</li>
    </ul>
  </div>
  
  <div class="warning-box warning-box--warning">
    <h4>⚠️ EMERGENCY PROTOCOLS:</h4>
    <ul>
      <li><strong>Level 1 (Urgent):</strong> [Emergency contact procedure]</li>
      <li><strong>Level 2 (Standard):</strong> [Standard escalation procedure]</li>
      <li><strong>After Hours:</strong> [After-hours contact procedure]</li>
    </ul>
  </div>
  
  <!-- Add industry-specific warnings as needed -->
  <div class="warning-box warning-box--warning">
    <h4>ℹ️ INDUSTRY-SPECIFIC NOTES:</h4>
    <ul>
      <li>[Add industry requirement #1]</li>
      <li>[Add compliance note #1]</li>
      <li>[Add special handling note #1]</li>
    </ul>
  </div>
</div>
```

---

## Customization Checklist

Before deploying, ensure all placeholders are replaced:

### Required Replacements
- [ ] `[BUSINESS_NAME]` - Full business name
- [ ] `[LOGO_URL]` - Logo image URL
- [ ] `[PRIMARY_PHONE]` - 10 digits, no formatting (e.g., 5551234567)
- [ ] `[PRIMARY_PHONE_FORMATTED]` - Formatted display (e.g., (555) 123-4567)
- [ ] `[SECONDARY_PHONE]` - Secondary phone number
- [ ] `[SECONDARY_PHONE_FORMATTED]` - Formatted display
- [ ] `[EMAIL]` - Contact email
- [ ] `[WEBSITE]` - Website URL
- [ ] `[TIMEZONE]` - IANA timezone identifier
- [ ] `[LATITUDE]` - Location latitude for weather
- [ ] `[LONGITUDE]` - Location longitude for weather
- [ ] `[FORM_ID]` - GoHighLevel form ID

### Optional Customizations
- [ ] `[ADDRESS]` - Physical address (if applicable)
- [ ] `[SERVICE_AREA]` - Service coverage area
- [ ] `[BUSINESS_HOURS]` - Operating hours description
- [ ] `[EMERGENCY_PHONE]` - Emergency contact number
- [ ] Brand colors in CSS variables
- [ ] Call script customization
- [ ] Warning/protocol customization

### Testing
- [ ] All placeholders replaced
- [ ] Logo displays correctly
- [ ] Phone click-to-copy works
- [ ] Weather displays for correct location
- [ ] Time shows correct timezone
- [ ] Office status calculates correctly
- [ ] Form ID is valid in GHL
- [ ] Mobile view works properly

---

## Deployment Notes

See [DEPLOYMENT.md](../../docs/DEPLOYMENT.md) for complete deployment instructions.

**Quick Deploy Steps**:
1. Copy each block's HTML into GHL Custom HTML elements
2. Add GHL form between Block 4 and Block 6
3. Configure call routing and business hours
4. Test with sample call
5. Train agents
6. Go live

---

**Questions?** Contact burke@jumpcontact.com
