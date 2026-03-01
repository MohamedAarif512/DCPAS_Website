# DCPAS Website – Setup Guide

## Files Included
- `index.html` — Main homepage
- `about.html` — About page
- `contact.html` — Contact page
- `demo.html` — Demo request form (sends email to you)
- `logo.webp` — DCPAS navbar logo
- `favicon.png` — Browser tab favicon

## How to Deploy
Just put all files in the same folder on any web host (Netlify, GitHub Pages, Vercel, shared hosting).
Make sure `logo.webp` and `favicon.png` are in the same folder as the HTML files.

---

## Setting Up Email (so demo requests reach you)

### Option A: EmailJS (Recommended — Free, No Backend Needed)

1. Go to **https://www.emailjs.com/** and create a free account
2. Click **Add New Service** → choose Gmail → connect your Google account
3. Copy the **Service ID** (e.g. `service_abc123`)
4. Go to **Email Templates** → click **Create New Template**
5. Set the template body like this:

```
New DCPAS Demo Request

Name: {{from_name}}
Email: {{from_email}}
Phone: {{phone}}
Farm Size: {{farm_size}}
Location: {{location}}
Primary Crops: {{crops}}
Attack Frequency: {{frequency}}
Previous Methods Tried: {{previous_methods}}

Additional Information:
{{additional_info}}
```

6. Set **To Email** → `mohamedaarif.peer@gmail.com`
7. Save the template, copy the **Template ID** (e.g. `template_xyz789`)
8. Go to **Account → General** → copy your **Public Key**
9. Open `demo.html` and replace these 3 lines near the top of the `<script>`:

```javascript
const EMAILJS_SERVICE_ID  = 'service_abc123';    // ← your Service ID
const EMAILJS_TEMPLATE_ID = 'template_xyz789';   // ← your Template ID
const EMAILJS_PUBLIC_KEY  = 'abcDEFxyz123456';   // ← your Public Key
```

That's it! Every demo request will be emailed to `mohamedaarif.peer@gmail.com`.

---

### Option B: Formspree (Even Simpler — No JS needed)

1. Go to **https://formspree.io/** → create free account
2. Click **New Form** → set email to `mohamedaarif.peer@gmail.com`
3. Copy your Form ID (e.g. `xpwzqabc`)
4. In `contact.html`, find this line and replace `YOUR_FORM_ID`:
```javascript
fetch('https://formspree.io/f/YOUR_FORM_ID', {
```

Note: Formspree works for the contact page. For the full multi-step demo form, EmailJS gives a better experience.

---

## Fonts Used
- **League Spartan ExtraBold (800)** — all headings
- **K2D** — all body/small text

Both are loaded from Google Fonts — no installation needed.

---

## Customization
- Change colors in the `:root {}` CSS block at the top of each file
- `--green: #00e87a` is the accent color used throughout
- `--nav: #0e1010` is the navbar background color
