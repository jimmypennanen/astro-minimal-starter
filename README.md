# Astro Minimal Starter

A clean, minimal Astro + Tailwind starter template for small business websites. Perfect for building fast, professional sites with minimal JavaScript.

## Features

- **Astro 4** - Fast, modern static site generation
- **Tailwind CSS** - Utility-first styling with minimal customization
- **Minimal JavaScript** - Most content is static HTML
- **Responsive Design** - Mobile-first approach
- **Reusable Components** - Modular, copy-paste friendly
- **Site Config** - Centralized site configuration
- **Professional Out-of-the-Box** - Neutral, clean design

## Project Structure

```
src/
├── components/           # Reusable components
│   ├── Header.astro     # Navigation header
│   ├── Footer.astro     # Footer with contact info
│   └── SectionWrapper.astro  # Reusable section container
├── layouts/
│   └── MainLayout.astro # Main page layout with header/footer
├── pages/
│   ├── index.astro      # Homepage with all sections
│   └── 404.astro        # 404 error page
├── styles/
│   └── global.css       # Global Tailwind styles
└── config.ts            # Site configuration (name, contact, etc)

Public files go in the `public/` folder (create if needed)
```

## Getting Started

### Installation

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Customization Guide

### 1. Site Configuration

Edit `src/config.ts` to update your company info:

```typescript
export const siteConfig = {
  name: 'Your Company Name',
  tagline: 'Your main headline',
  description: 'Brief company description',
  email: 'contact@example.com',
  phone: '+1 (555) 123-4567',
  address: 'Your address',
  // ... more settings
};
```

This config is used throughout the site for consistency.

### 2. Colors & Branding

**Tailwind Colors**: The template uses neutral grays by default. Edit `tailwind.config.mjs` to change the color palette:

```javascript
colors: {
  primary: '#your-color',
  secondary: '#your-color',
  // ...
}
```

**Text & Button Colors**: Update classes in components. For example, change:
- `bg-neutral-900` to your primary color
- `hover:bg-neutral-800` to a darker shade
- `text-neutral-600` for secondary text

### 3. Fonts

The template uses Inter from Google Fonts. To change:

1. Update the Google Fonts link in `src/layouts/MainLayout.astro`
2. Update `fontFamily` in `tailwind.config.mjs`

### 4. Logo/Branding

In `src/components/Header.astro`, replace the text logo with an image:

```astro
<img src="/logo.png" alt="Logo" class="h-8" />
```

### 5. Content & Sections

Edit `src/pages/index.astro` to modify:
- Hero section text
- About section content
- Services (the 3 service boxes)
- Contact information

Keep the `<SectionWrapper>` component structure—it handles layout and spacing.

### 6. Add New Pages

Create a new `.astro` file in `src/pages/`:

```astro
---
import MainLayout from '../layouts/MainLayout.astro';
import SectionWrapper from '../components/SectionWrapper.astro';
---

<MainLayout title="Page Title">
  <SectionWrapper title="Section Title">
    <!-- Your content here -->
  </SectionWrapper>
</MainLayout>
```

The filename becomes the URL. For example, `src/pages/about.astro` → `/about`

### 7. Modify Header Navigation

Edit the `navItems` array in `src/config.ts`:

```typescript
navItems: [
  { label: 'Home', href: '/' },
  { label: 'About', href: '#about' },
  { label: 'Services', href: '#services' },
  { label: 'Contact', href: '#contact' },
],
```

### 8. Footer Customization

Edit `src/components/Footer.astro` to adjust layout or add more information. It pulls from `siteConfig` automatically.

## Styling Tips

### Spacing
- Use Tailwind's spacing scale: `p-4`, `m-8`, `gap-6`, etc.
- Sections use consistent `py-16 sm:py-20 lg:py-24` padding

### Responsive Design
- `sm:` - small screens (640px)
- `md:` - medium screens (768px)
- `lg:` - large screens (1024px)

### Adding Custom Styles

Edit `src/styles/global.css` for global styles, or add inline Tailwind classes in components.

## SEO & Metadata

Customize in `src/config.ts`:
- `description` - Meta description (important for SEO)
- `keywords` - Meta keywords
- `ogImage` - Open Graph image for social sharing
- `author` - Author name

Add page-specific meta by passing props to `MainLayout`:

```astro
<MainLayout title="Page Title" description="Page description">
```

## Performance Tips

- All pages are static HTML—no JavaScript bloat
- Images should be optimized before adding (use tools like TinyPNG)
- Use Astro's `Image` component for automatic optimization (if needed)
- Keep content concise for better performance

## Deployment

### Netlify
```bash
npm run build
# Deploy the `dist/` folder
```

### Vercel
```bash
npm run build
# Connect your repo—Vercel will auto-detect Astro
```

### Traditional Hosting
```bash
npm run build
# Upload the `dist/` folder contents to your server
```

## Tips for Reusing

1. **Duplicate the entire folder** for a new project
2. **Search & Replace** `siteConfig` references to update branding
3. **Keep the structure**—it's designed for easy duplication
4. **Modify colors** in `tailwind.config.mjs` once per project
5. **Keep components minimal**—this template intentionally avoids overcomplication

## No Build Required (Simple Edits)

For quick changes like text, contact info, or service descriptions:
1. Edit `src/config.ts` or `src/pages/index.astro`
2. Dev server auto-reloads

## Troubleshooting

**Port already in use?**
```bash
npm run dev -- --port 3001
```

**Build errors?**
```bash
# Clear cache
rm -rf node_modules .astro dist
npm install
npm run build
```

**Changes not reflecting?**
- Check that you saved the file
- Hard refresh your browser (Cmd+Shift+R)
- Restart the dev server

---

Built with Astro, Tailwind CSS, and simplicity in mind. Happy building!
