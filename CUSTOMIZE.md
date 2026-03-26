# Quick Customization Guide

## 5-Minute Setup

### Step 1: Update Site Config
Open `src/config.ts` and update:
```typescript
name: 'Your Business Name'
tagline: 'Your main headline'
email: 'your@email.com'
phone: 'your phone'
address: 'your address'
```

### Step 2: Change Content
Edit `src/pages/index.astro`:
- Hero section: Change the tagline and description (lines 13-18)
- About section: Update "Our Story" and "Why Choose Us" (lines 27-49)
- Services: Replace the 3 services (lines 58-72)
- Contact: Already pulls from config.ts

### Step 3: Update Colors
Edit `tailwind.config.mjs` and change color hex values:
```javascript
colors: {
  primary: '#your-brand-color',
}
```

Then search components and replace:
- `bg-neutral-900` → `bg-primary`
- `hover:bg-neutral-800` → `hover:bg-primary-dark`

## Common Changes

### Add a new section to homepage
In `src/pages/index.astro`, add:
```astro
<SectionWrapper id="new-section" title="Section Title" bgColor="white">
  <!-- Your content -->
</SectionWrapper>
```

### Create a new page
Create `src/pages/new-page.astro`:
```astro
---
import MainLayout from '../layouts/MainLayout.astro';
import SectionWrapper from '../components/SectionWrapper.astro';
---

<MainLayout title="New Page">
  <SectionWrapper title="Title">
    <!-- Content -->
  </SectionWrapper>
</MainLayout>
```

### Change logo text to image
In `src/components/Header.astro`, replace:
```astro
{siteConfig.name}
```
with:
```astro
<img src="/logo.png" alt="Logo" class="h-8" />
```

### Update navigation links
In `src/config.ts`, edit:
```typescript
navItems: [
  { label: 'Home', href: '/' },
  { label: 'Services', href: '/services' },
  { label: 'Contact', href: '#contact' },
]
```

### Change footer layout
Edit `src/components/Footer.astro` - it's straightforward HTML structure.

### Add a custom font
1. Get font from Google Fonts
2. Update link in `src/layouts/MainLayout.astro` (line 34-38)
3. Update `fontFamily` in `tailwind.config.mjs`

## Responsive Breakpoints

- `sm:` - 640px and up (tablets)
- `md:` - 768px and up
- `lg:` - 1024px and up (desktops)

Example: `grid-cols-1 md:grid-cols-2` = 1 column on mobile, 2 on medium+ screens

## Color System (Neutral Only)

- `text-neutral-600` = secondary text (lighter)
- `text-neutral-900` = primary text (dark)
- `bg-neutral-50` = light background
- `bg-neutral-900` = dark background
- `border-neutral-200` = subtle border

Change all at once in `tailwind.config.mjs` colors section.

## Button Styles

Primary button:
```astro
<a href="/contact" class="px-6 py-3 bg-neutral-900 text-white rounded-lg hover:bg-neutral-800">
  CTA Text
</a>
```

Secondary button:
```astro
<a href="/learn" class="px-6 py-3 border border-neutral-300 text-neutral-900 hover:border-neutral-400">
  Secondary
</a>
```

## File You'll Edit Most

1. `src/config.ts` - Company info
2. `src/pages/index.astro` - Homepage content
3. `tailwind.config.mjs` - Brand colors
4. `src/components/Header.astro` - Navigation
5. `src/components/Footer.astro` - Footer content

---

**Never edit:**
- `astro.config.mjs`
- `tsconfig.json`
- The `layouts/MainLayout.astro` structure (unless adding new layout)

Keep it simple. The less you customize, the easier it is to duplicate for the next client.
