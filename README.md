# Dental CAM Solution — Website

## Files
- `index.html` — Full website
- `vercel.json` — Vercel deployment config

---

## Deploy to Vercel (10 minutes)

1. Create a free account at vercel.com
2. Install Vercel CLI or use the web dashboard
3. Drag this folder into vercel.com/new (drag & drop deploy)
4. Set your custom domain: dentalcamsolution.com
   - In Vercel dashboard → your project → Settings → Domains
   - Add www.dentalcamsolution.com
   - Point your domain DNS to Vercel (they give you the records)

---

## Wire up Stripe Payment Links (for DS CAM licensing)

### Step 1 — Create a Stripe account
Go to stripe.com → sign up → complete business verification

### Step 2 — Create Payment Links for each product
In Stripe dashboard:
- Products → Add Product → "DS CAM V5 Single License"
- Set price in CAD
- Click "Create Payment Link"
- Stripe gives you a URL like: https://buy.stripe.com/xxxxx

### Step 3 — Paste the links into index.html
Search for these comments in index.html and replace the href:

  <!-- REPLACE href WITH YOUR STRIPE PAYMENT LINK -->
  <a class="btn-primary" href="#contact" id="buy-single">Get Pricing</a>

Change to:
  <a class="btn-primary" href="https://buy.stripe.com/YOUR_LINK_HERE" target="_blank">Buy Now — $XXX CAD</a>

Do the same for the Free Demo and Multi-Seat cards.

---

## Wire up the Contact Form (so emails actually send)

Currently the form uses a mailto: fallback. For a proper form:

### Option A — Formspree (free, easiest)
1. Go to formspree.io → create account → new form
2. Get your form endpoint: https://formspree.io/f/xxxxxxx
3. In index.html, replace the submitForm() function with:

   fetch('https://formspree.io/f/YOUR_ID', {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({ name, email, message })
   })

### Option B — Netlify Forms (if you switch to Netlify hosting)
Add `netlify` attribute to your form tag — zero config required.

---

## Update pricing/content
All text is in index.html — search for the section you want and edit directly.
Pricing cards are in the section with class="pricing-grid".
