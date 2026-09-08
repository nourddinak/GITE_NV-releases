# GITE_NV Releases & Official Landing Page

Official releases, downloads, and documentation site for **GITE_NV** — the modern GitHub Environment, Secrets & SSH Deploy Key Orchestrator.

---

## What is GITE_NV?

GITE_NV saves reusable configuration profiles for your applications and microservices, allowing 1-click deployments of encrypted secrets, environment variables, and SSH deploy keys to any GitHub repository.

### Key Highlights
- **100% Local SQLite Persistence**: ACID-compliant SQLite storage in `%APPDATA%` that survives application updates and browser cache wipes.
- **Automated VPS Discovery**: 1-click script (`bash <(curl -fsSL https://raw.githubusercontent.com/nourddinak/SCRIPTS/main/setup-github.sh)`) auto-detects server settings and generates GitHub Actions deploy keys.
- **Default-to-Secret Security**: All imported variables default to encrypted write-only secrets to eliminate accidental credential leaks.
- **Per-Repo & Account Keys**: Deploy isolated repo keys or register once across your entire GitHub account.

---

## Downloads (Windows Desktop)

| Release Asset | File | Size | Type |
|---|---|---|---|
| **Windows Setup Installer** | `GITE_NV Setup 0.0.2.exe` | ~120 MB | Full NSIS Installer with Start Menu & Shortcuts |
| **Windows Portable** | `GITE_NV-Portable-0.0.2.exe` | ~120 MB | Zero-install standalone executable |

> **Note**: Binary executables are excluded from Git tracking via `.gitignore` because GitHub limits commits to 100MB. Binary releases are published as GitHub Release assets.

---

## Publishing to GitHub Pages & GitHub Releases

Follow these steps from the `GITE_NV-releases` folder:

### 1. Initialize Git & Push Website (Lightweight, < 1 MB)
```powershell
cd c:\Users\bob\Desktop\GITE_NV-releases

# Initialize git
git init
git add .
git commit -m "feat: launch GITE_NV official releases site"

# Create public repo and push website files
gh repo create GITE_NV-releases --public --source=. --push
```

### 2. Enable GitHub Pages (Free Web Hosting)
```powershell
gh repo edit --enable-pages --pages-branch=main
```
Your landing page will be instantly live at:
`https://nourddinak.github.io/GITE_NV-releases/`

### 3. Create GitHub Release & Upload Executables
Upload the 120MB `.exe` files directly to GitHub Releases (bypassing the 100MB git commit restriction):
```powershell
gh release create v0.0.2 "GITE_NV Setup 0.0.2.exe" "GITE_NV-Portable-0.0.2.exe" --title "GITE_NV v0.0.2 (Windows Desktop)" --notes "Initial public release of GITE_NV Windows Desktop edition featuring local SQLite persistence, automated VPS SSH key discovery, and encrypted secret management."
```
Once uploaded, the download buttons on your landing page will immediately download the executables directly from GitHub CDN.
