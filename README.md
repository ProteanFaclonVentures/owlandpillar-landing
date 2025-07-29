# Owl and Pillar - AI-Powered College Matching

A modern, minimalist landing page for an AI-powered college matching service that helps students find their reach, target, and safety schools.

## Features

- 🎓 AI-powered college matching system
- 🎯 Categorization into Reach, Target, and Safety schools
- 💳 Three-tier pricing model (Basic, Premium, Pro)
- 📱 Fully responsive design
- ♿ WCAG AA compliant for accessibility
- 🚀 Built with Astro for optimal performance
- 🎨 Modern minimalist design with college-themed colors

## Technologies Used

- **Astro** - Static site generator for optimal performance
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with CSS custom properties
- **Google Fonts** - Playfair Display and Inter fonts
- **TypeScript** - Type-safe development

## Getting Started

### Prerequisites

- Node.js 18.17.1 or higher
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/owlandpillar.git
cd owlandpillar
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and visit `http://localhost:4321`

## Build for Production

To build the site for production:

```bash
npm run build
```

The built files will be in the `dist/` directory.

## Deploying to GitHub Pages

### Method 1: Using GitHub Actions (Recommended)

1. Create a new file `.github/workflows/deploy.yml` in your repository:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

env:
  BUILD_PATH: "."

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          
      - name: Install dependencies
        run: npm ci
        working-directory: ${{ env.BUILD_PATH }}
        
      - name: Build with Astro
        run: npm run build
        working-directory: ${{ env.BUILD_PATH }}
        
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ${{ env.BUILD_PATH }}/dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    needs: build
    runs-on: ubuntu-latest
    name: Deploy
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

2. In your repository settings:
   - Go to Settings → Pages
   - Under "Source", select "GitHub Actions"

3. Push your code to the main branch. The workflow will automatically deploy your site.

### Method 2: Manual Deployment

1. Build the project:
```bash
npm run build
```

2. Install gh-pages:
```bash
npm install --save-dev gh-pages
```

3. Add deploy script to `package.json`:
```json
{
  "scripts": {
    "deploy": "gh-pages -d dist"
  }
}
```

4. Deploy:
```bash
npm run deploy
```

## Setting Up a Custom Domain

1. Create a `CNAME` file in the `public/` directory with your domain:
```
owlandpillar.com
```

2. In your domain registrar's DNS settings, add:
   - A record: `@` → `185.199.108.153`
   - A record: `@` → `185.199.109.153`
   - A record: `@` → `185.199.110.153`
   - A record: `@` → `185.199.111.153`
   - CNAME record: `www` → `yourusername.github.io`

3. In GitHub repository settings:
   - Go to Settings → Pages
   - Under "Custom domain", enter `owlandpillar.com`
   - Check "Enforce HTTPS"

4. Wait for DNS propagation (can take up to 24 hours)

## Project Structure

```
owlandpillar/
├── src/
│   └── pages/
│       └── index.astro    # Main landing page
├── public/
│   └── favicon.svg        # Site favicon
├── astro.config.mjs       # Astro configuration
├── tsconfig.json          # TypeScript configuration
├── package.json           # Project dependencies
└── README.md             # This file
```

## Customization

### Colors

The color scheme can be customized in the CSS custom properties:

```css
:root {
  --primary-blue: #003366;
  --primary-gold: #FFB81C;
  --secondary-blue: #0051A5;
  --light-gray: #F5F5F7;
  --dark-gray: #1D1D1F;
  --medium-gray: #6E6E73;
  --white: #FFFFFF;
}
```

### Fonts

The site uses:
- **Playfair Display** for headings
- **Inter** for body text

To change fonts, update the Google Fonts link in `index.astro` and the font variables in CSS.

## Accessibility Features

- Semantic HTML structure
- ARIA labels for form inputs
- Screen reader-only content for context
- High contrast color combinations
- Focus indicators for keyboard navigation
- Responsive design for all devices
- Reduced motion support

## License

This project is licensed under the MIT License.

## Support

For support, email support@owlandpillar.com or open an issue in the GitHub repository.