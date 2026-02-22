# Deploy Emergency Landing Page to Vercel
## patriotportables.com/emergency → emergency.patriotportables.com

---

## What You're Deploying
A standalone high-converting landing page for emergency porta potty searches.
- URL: emergency.patriotportables.com (or any subdomain you choose)
- File: emergency-landing-page.html

---

## Step 1: Create a New GitHub Repo

1. Go to github.com and click **New repository**
2. Name it: `patriot-emergency-landing`
3. Set to **Private**
4. Click **Create repository**

---

## Step 2: Upload Your Files

In the new repo, click **Add file > Upload files** and upload:
- `emergency-landing-page.html`
- `vercel.json`

Commit directly to main.

---

## Step 3: Deploy on Vercel

1. Go to vercel.com and click **Add New > Project**
2. Import your `patriot-emergency-landing` GitHub repo
3. Leave all settings as default — Vercel will detect the config
4. Click **Deploy**

Your page will be live at a vercel.app URL within 60 seconds.

---

## Step 4: Add Your Custom Domain (emergency.patriotportables.com)

### In Vercel:
1. Go to your project > **Settings > Domains**
2. Type: `emergency.patriotportables.com`
3. Click **Add**
4. Vercel will show you a CNAME record to add

### In Your DNS (wherever patriotportables.com is registered):
Add a CNAME record:
- **Name/Host:** `emergency`
- **Value/Target:** `cname.vercel-dns.com`
- **TTL:** 3600

DNS usually propagates within 15–30 minutes.

---

## Step 5: Update Your Logo

In the HTML file, find this line:
```
<img src="https://www.patriotportables.com/logo.png" ...>
```

Replace the src with your actual logo URL from your Wix media library.
To find it: go to your Wix site > Media > right-click your logo > Copy URL.

---

## Step 6: Connect Your Form

The quote form currently submits to `/thank-you`. You have two options:

**Option A — Use Formspree (easiest, free):**
1. Go to formspree.io and create a free account
2. Create a new form — you'll get a URL like `https://formspree.io/f/xyzabc`
3. In the HTML, find `action="/thank-you"` and replace with your Formspree URL
4. Add `method="POST"` is already there — you're done
5. Formspree emails you every submission

**Option B — Connect to your existing CRM/form handler:**
Replace the form action URL with whatever endpoint your current Wix forms use.

---

## Step 7: Update Google Ads Final URLs

Once the page is live at emergency.patriotportables.com, update your Google Ads:

- Campaign 3 (Emergency): Change Final URL to `https://emergency.patriotportables.com`
- Any existing ads pointing to patriotportables.com/emergency: Update those too

---

## Step 8: Set Up Conversion Tracking

Once you have a /thank-you page (Formspree can redirect there):
1. Go to Google Ads > Tools > Conversions > New Conversion
2. Choose: Website
3. Track: Thank you page URL
4. Paste the Google tag snippet into your thank-you page's `<head>`

---

## Future Landing Pages

When you're ready to build the Construction and Events pages, the process is identical.
You can add them to the same repo as:
- `construction-landing-page.html`
- `events-landing-page.html`

And add routes in vercel.json:
```json
{
  "rewrites": [
    { "source": "/", "destination": "/emergency-landing-page.html" },
    { "source": "/construction", "destination": "/construction-landing-page.html" },
    { "source": "/events", "destination": "/events-landing-page.html" }
  ]
}
```

Then use subdomains:
- emergency.patriotportables.com
- construction.patriotportables.com  
- events.patriotportables.com
