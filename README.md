# Portfolio Tracker (GitHub Pages)

This repository hosts a single-page portfolio tracker. It works fully in the browser and stores your positions in localStorage. Prices update via Coinbase (crypto) and Alpha Vantage (equities, requires API key saved in the app Settings). Optional cloud sync via a private GitHub Gist lets you access the same data on multiple devices.

## How to publish on GitHub Pages

1. Create a repository on GitHub and push these files.
   - Ensure `index.html` is at the root of the repository.
   - This repo already contains `.github/workflows/pages.yml` to auto-deploy on pushes to `main` or `master`.
2. In GitHub → Settings → Pages:
   - Build and deployment → Source: select "GitHub Actions".
3. Push to `main` (or `master`). The GitHub Actions workflow will build and deploy.
4. After the deploy job finishes, Pages URL will appear in the workflow summary and in Settings → Pages.

## Using the app
- Add your assets via the form. For crypto you can type just `BTC` (auto-mapped to `BTC-USD`).
- Click "Настройки" to store your Alpha Vantage API key (for stocks/ETFs).
- Click "Обновить цены" to fetch latest prices, or leave the tab open (auto-refresh every 5 minutes).
- Data is kept in your browser only (localStorage). Use Export/Import to backup/restore.
- Cross-device sync: click "Облако" to configure a GitHub Personal Access Token (scope: `gist`) and save/load your data to a private Gist. The token and Gist ID are stored locally in your browser.

### Mobile
- The dashboard, table, and charts are responsive. On mobile, charts are arranged in one column with compact height, reduced paddings, and smaller fonts for clarity.

## Notes
- Public pages expose network requests from the browser. Your Alpha Vantage key is stored in your browser (not the repo). For private keys and 24/7 background refresh, consider moving price fetching to a serverless function with a cron (e.g., Vercel) and proxy the data to the page.
- For cloud sync, your GitHub token is never committed; it's only kept in localStorage. You can revoke it anytime from your GitHub settings.
