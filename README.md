# 🔥 Ember & Spice — Premium Restaurant Website

> A luxury single-page restaurant website for a multi-cuisine dining brand offering Desi BBQ, Fast Food, and Continental cuisine.

---

## 📋 Project Overview

**Ember & Spice** is a fully self-contained, single-file (`restaurant.html`) premium restaurant website built with pure HTML, CSS, and vanilla JavaScript — no frameworks, no dependencies, no build tools required. It is designed to maximize online orders, simplify the user experience, and establish a high-end brand presence.

---

## 🚀 Quick Start

1. Download `restaurant.html`
2. Open it in any modern web browser — that's it.

No installation, no npm, no server required. The file runs entirely client-side.

---

## 🗂️ Project Structure

```
restaurant.html          # The entire application (HTML + CSS + JS)
README.md                # This file
```

Everything — styles, scripts, layout, interactions — lives in a single portable file.

---

## 🎨 Design System

### Theme
Dark luxury aesthetic with gold/amber accents.

| Token | Value | Usage |
|---|---|---|
| `--gold` | `#C9A84C` | Primary accent, prices, CTAs |
| `--gold-light` | `#E8C96A` | Hover states, highlights |
| `--ember` | `#E05C2A` | Badges, notifications |
| `--charcoal` | `#0D0D0D` | Page background |
| `--text` | `#F2ECD9` | Primary text |
| `--text-muted` | `#A09070` | Secondary text |

### Typography

| Font | Style | Used For |
|---|---|---|
| Cinzel | Display / All-caps | Logo, section headings, prices |
| Cormorant Garamond | Serif / Italic | Card titles, taglines, reviews |
| Outfit | Sans-serif / Light | Body text, labels, buttons |

All fonts are loaded via Google Fonts CDN.

---

## 📄 Sections

The website is a single scrollable page with 9 core sections, each accessible via the navigation bar.

### 1. Hero
- Full-width auto-rotating image slider (3 slides, 4s interval)
- Restaurant name, tagline, and two CTA buttons (Order Now, Book a Table)
- Animated entrance for badge, title, and buttons
- Stats bar: Years of Excellence, Menu Items, Happy Guests
- Scroll indicator

### 2. Menu
Five tabbed categories, each with its own item grid:

| Tab | Items |
|---|---|
| 🔥 BBQ | Seekh Kebab, Chicken Tikka, Mutton Boti, Mix Grill, Chapli Kebab, Malai Boti |
| 🍔 Fast Food | Signature Burger, Zinger, Loaded Fries, Shawarma, Pizza, Buffalo Wings |
| 🍝 Continental | Pasta Arrabbiata, Pan-Seared Salmon, Caesar Salad, Ember Beef Steak |
| 🥤 Drinks | Mint Lemonade, Mango Lassi, Cold Coffee, Mocktail Punch |
| ⭐ Deals | Family BBQ Feast, Couple Dinner Special, Office Lunch Deal |

Each item card shows: image, name, description, price, badge (Bestseller / New / Chef's Pick), and an Add to Cart button.

### 3. Online Ordering
- Order type selector: **Dine-In Pre-Order**, **Takeaway**, **Home Delivery**
- Dynamic form fields (table selector shown for dine-in; address field for delivery)
- Interactive table grid — occupied tables are greyed out
- Date picker, time slot selector, special instructions field
- Loyalty points tracker (earns 1 pt per ₨10 spent)

### 4. Cart Sidebar
- Slides in from the right
- Real-time item list with quantity controls (+/−) and remove buttons
- Subtotal, delivery fee, and total display
- Coupon code field (see Coupon Codes below)
- Checkout button → scrolls to Payment section

### 5. Order Status
- Appears in cart sidebar after placing an order
- Three animated steps: **Received → Preparing → Ready**
- Each step activates with a 2.5s delay to simulate real-time updates

### 6. Payment
Three payment methods, switchable via tabs:

| Method | Details |
|---|---|
| Credit / Debit Card | Live card preview that updates as you type number, name, and expiry |
| Cash on Delivery | Confirmation screen with instructions |
| Mobile Wallet | EasyPaisa and JazzCash options with transaction ID field |

SSL security badge displayed on all payment views.

### 7. Reservation
- Full name, phone, date/time picker, occasion selector
- Animated guest counter (1–20 guests, increment/decrement buttons)
- Decorative restaurant interior photo with availability overlay

### 8. About
- Restaurant origin story and chef highlight
- Three-image gallery (main + two smaller)
- Four feature tiles: Charcoal Grilled, Fresh Daily, Master Chefs, Award Winning

### 9. Reviews
- Six customer testimonials
- Star ratings, reviewer name, date, and source platform (Google / TripAdvisor / Zomato etc.)
- Decorative large quotation mark per card

### 10. Location & Contact
- Google Maps embed (Clifton, Karachi)
- Address, phone, email, and working hours
- WhatsApp button

### 11. Footer
- Brand description and social media links
- Quick navigation links
- Policy links
- Newsletter subscription form with email input

---

## ⚙️ Features Reference

### Cart System
Cart state is held in a JavaScript array (`cart[]`). Each entry has `name`, `price`, `img`, and `qty`. All totals are calculated on every update.

### Coupon Codes
| Code | Discount |
|---|---|
| `EMBER20` | 20% off entire cart |

To add more coupons, edit the `applyCoupon()` function in the `<script>` block.

### Loyalty Points
Points are accumulated in the `loyaltyPoints` variable and displayed in the banner above the ordering form. Rate: **1 point per ₨10 spent**.

### WhatsApp Integration
The floating WhatsApp button links to:
```
https://wa.me/923001234567?text=Hi%2C%20I'd%20like%20to%20place%20an%20order!
```
Replace `923001234567` with your actual WhatsApp business number.

### Order Status Simulation
Triggered by `placeOrder()` → calls `animateOrderStatus()` which adds the `completed` class to each status step at 2.5s intervals. In production, replace this with a real-time API call or WebSocket.

### Scroll Animations
All elements with class `reveal`, `reveal-left`, or `reveal-right` animate in on scroll via `IntersectionObserver`. The `observeReveal()` function is called once on load and again when menu tabs are switched (to capture newly visible cards).

---

## 🛠️ Customization Guide

### Changing the Restaurant Name
Search for `Ember & Spice` and `EMBER & SPICE` throughout the file and replace with your brand name.

### Updating Menu Items
Each menu card follows this structure:

```html
<div class="menu-card" onclick="addToCart('Item Name','Price','image-url',this)">
  <div class="menu-card-img">
    <img src="image-url" alt="Item Name">
    <div class="menu-card-badge">Bestseller</div>  <!-- optional -->
  </div>
  <div class="menu-card-body">
    <div class="menu-card-title serif">Item Name</div>
    <div class="menu-card-desc">Description here.</div>
    <div class="menu-card-footer">
      <div class="menu-card-price">₨ 1,200<small>/unit</small></div>
      <button class="add-to-cart-btn">+</button>
    </div>
  </div>
</div>
```

Price in the `addToCart()` call should be a string like `'1,200'` (commas are stripped automatically).

### Changing Currency Symbol
Search for `₨` and replace with your currency symbol (e.g., `$`, `€`, `£`).

### Updating Contact Info
Find and replace the following values:

| Placeholder | Location |
|---|---|
| `+92 300 123 4567` | Location section, footer |
| `923001234567` | WhatsApp href |
| `hello@emberandspice.pk` | Location section |
| `Plot 45, Block 5, Clifton, Karachi` | Location section |

### Updating the Google Map
Find the `<iframe src="https://www.google.com/maps/embed?...` tag in the Location section and replace the URL with your own Google Maps embed URL (Maps → Share → Embed a map → Copy HTML).

### Changing Colors
All colors are CSS custom properties at the top of the `<style>` block. Edit the `:root {}` section:

```css
:root {
  --gold: #C9A84C;       /* primary accent */
  --ember: #E05C2A;      /* badges, alerts */
  --charcoal: #0D0D0D;   /* background */
  /* ... */
}
```

### Updating Hero Images
The three hero slides use Unsplash URLs. Replace `background-image: url(...)` on `.hero-slide:nth-child(1/2/3)` with your own hosted images.

---

## 📱 Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `> 1024px` | Full desktop layout, two-column grids, hero image panel visible |
| `768px – 1024px` | Image panel hidden on hero, single-column about/reservation/location |
| `< 768px` | Hamburger nav, stacked order types, full-width cart sidebar |
| `< 480px` | Stacked CTAs, condensed menu tabs |

---

## 🔌 Production Integration Notes

The following features are UI-only and need backend integration for production use:

| Feature | Current State | Integration Needed |
|---|---|---|
| Order placement | Shows toast + status animation | REST API / Firebase |
| Table availability | Static (T3, T6, T9 hardcoded as occupied) | Real-time DB (e.g., Firestore) |
| Payment processing | UI only — no real charge | Stripe / HBL / Meezan Bank gateway |
| EasyPaisa / JazzCash | Input field only | JazzCash/EasyPaisa REST API |
| Reservation confirmation | Toast only | Email/SMS via SendGrid / Twilio |
| Newsletter | Toast only | Mailchimp / ConvertKit API |
| Loyalty points | In-memory (resets on reload) | User auth + database |
| Push notifications | Not implemented | Firebase Cloud Messaging |

---

## 🌐 SEO

The `<head>` includes:
- Descriptive `<title>` tag
- `<meta name="description">` with keywords
- `lang="en"` on the `<html>` tag
- Semantic HTML5 elements (`<nav>`, `<section>`, `<footer>`)
- `alt` attributes on all images
- `loading="lazy"` on menu item images

For further SEO: add Open Graph tags, a `sitemap.xml`, and a `robots.txt` when deploying.

---

## ⚡ Performance Notes

- Single file — one HTTP request for the page
- Google Fonts loaded via `<link rel="preconnect">` for faster DNS resolution
- All menu images use `loading="lazy"` to defer off-screen loads
- Unsplash images are served at reduced quality (`q=70`/`q=80`) and limited width (`w=400`/`w=800`)
- CSS transitions use `cubic-bezier` easing for GPU-composited animation
- `IntersectionObserver` used instead of scroll event listeners for reveal animations

---

## 🏗️ Browser Support

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 90+ | ✅ Full |
| IE 11 | ❌ Not supported (uses CSS variables, `IntersectionObserver`) |

---

## 📦 Dependencies

All external resources are loaded via CDN — no npm or local install needed.

| Resource | Source | Used For |
|---|---|---|
| Cinzel | Google Fonts | Display headings |
| Cormorant Garamond | Google Fonts | Serif text |
| Outfit | Google Fonts | Body text |
| Google Maps | Embed iframe | Location map |
| Unsplash | CDN image URLs | Food photography |

---

## 📝 License

This project is provided for personal and commercial use. Food photography is sourced from [Unsplash](https://unsplash.com) under the Unsplash License. Replace with your own photos before publishing commercially.

---

*Built for Ember & Spice, Karachi — where every flame tells a story.*
