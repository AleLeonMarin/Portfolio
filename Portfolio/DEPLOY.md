# Deployment Guide - GitHub Pages

This portfolio is configured for automatic deployment to GitHub Pages.

## Automatic Deployment (Recommended)

### Setup Steps

1. **Push your code to GitHub:**
   ```bash
   git add .
   git commit -m "Setup GitHub Pages deployment"
   git push origin main
   ```
   
   *Note: If deploying from `react-dev` branch, update line 6 in `.github/workflows/deploy.yml`*

2. **Enable GitHub Pages:**
   - Go to your GitHub repository
   - Settings → Pages
   - Source: **GitHub Actions**
   
3. **Add Formspree secret (optional but recommended):**
   - Settings → Secrets and variables → Actions
   - New repository secret:
     - Name: `VITE_FORMSPREE_ENDPOINT`
     - Value: `https://formspree.io/f/meoneavb`

4. **Wait for deployment:**
   - Actions tab shows the build progress
   - After ~2 minutes, your site will be live at:
     - `https://aleleonmarin.github.io/Portfolio/` (default)
     - Or your custom domain if configured

### Custom Domain (Optional)

1. Add a `CNAME` file in `/public` with your domain:
   ```
   yourdomain.com
   ```

2. Configure DNS with your provider:
   - Type: `CNAME`
   - Host: `@` or `www`
   - Value: `aleleonmarin.github.io`

3. In GitHub Settings → Pages:
   - Custom domain: enter your domain
   - Enforce HTTPS: check this box

## Manual Deployment (Alternative)

If you prefer manual deployment using gh-pages:

1. **Install gh-pages:**
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Update base path in `vite.config.js`:**
   ```javascript
   base: '/Portfolio/',  // Change from '/' to '/Portfolio/'
   ```

3. **Deploy:**
   ```bash
   npm run deploy
   ```

4. **Enable GitHub Pages:**
   - Settings → Pages
   - Source: Deploy from branch
   - Branch: `gh-pages` → `/ (root)`

## Important Notes

- **Environment Variables:** `.env.local` is not committed. Add secrets in GitHub Actions settings.
- **Base Path:** Using `/` works for custom domains. Use `/Portfolio/` for `username.github.io/Portfolio/`
- **Branch:** Workflow triggers on `main` branch by default (change in `.github/workflows/deploy.yml` if needed)
- **Build Time:** ~2-3 minutes for first deployment

## Troubleshooting

**404 errors:** Check `base` path in `vite.config.js` matches your deployment URL

**Blank page:** Verify build succeeded in Actions tab and Pages source is set correctly

**Form not working:** Add `VITE_FORMSPREE_ENDPOINT` secret in repository settings

## Commands

- `npm run dev` - Local development
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm run deploy` - Manual deployment (requires gh-pages package)
