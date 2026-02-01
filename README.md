# DevBox Landing Page

## Getting Started

### Install Dependencies

```bash
npm install
```

### Development Server

```bash
npm run dev
```

Visit `http://localhost:5173` to see the landing page.

### Build for Production

```bash
npm run build
```

The static site will be generated in the `dist/` folder, ready to deploy to any static hosting service (Vercel, Netlify, GitHub Pages, etc.).

### Preview Production Build

```bash
npm run preview
```

## Project Structure

```
devbox-landing/
├── src/
│   ├── lib/
│   │   ├── Nav.svelte       # Navigation component
│   │   ├── Hero.svelte      # Hero section with app preview
│   │   ├── Features.svelte  # Feature cards
│   │   ├── Tools.svelte     # Tools showcase
│   │   ├── CTA.svelte       # Download CTA
│   │   └── Footer.svelte    # Footer
│   ├── App.svelte           # Main app component
│   ├── main.js              # Entry point
│   └── app.css              # Global styles
├── public/                  # Static assets
├── index.html               # HTML template
└── package.json
```

## Deployment

Execute `npm run deploy` to build and deploy the site to GitHub Pages. 

## Customization

All design tokens are defined as CSS variables in `src/app.css`:

- `--accent-primary`: Primary accent color (neon green)
- `--accent-blue`: Secondary accent color (electric blue)
- `--bg-primary`, `--bg-secondary`, `--bg-tertiary`: Background colors
- `--text-primary`, `--text-secondary`, `--text-muted`: Text colors

## Tech Stack

- **Svelte 4** - Reactive UI framework
- **Vite** - Build tool and dev server