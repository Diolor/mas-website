# OWASP Mobile Application Security Project Website

This repository contains the source and configuration for the **OWASP Mobile Application Security Project website** ([mas.owasp.org](https://mas.owasp.org/)).
It aggregates, organizes, and presents documentation from the main MAS resources using [MkDocs](https://www.mkdocs.org/) and the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) theme.

> **Note:** This repository does **not** contain the full content for MASVS, MASTG, or MASWE—these live in their own repositories.

## OWASP MAS Resources Overview

| Resource | Description | GitHub Repo |
|----------|-------------|------------|
| MASVS (Mobile Application Security Verification Standard) | The industry standard for mobile app security requirements. | [OWASP/masvs](https://github.com/OWASP/masvs) |
| MASTG (Mobile Application Security Testing Guide) | A comprehensive manual for mobile app security testing and reverse engineering. | [OWASP/mastg](https://github.com/OWASP/mastg) |
| MASWE (Mobile Application Security Weakness Enumeration) | A categorized list of common security and privacy weaknesses in mobile apps. | [OWASP/maswe](https://github.com/OWASP/maswe) |

## Local Development

To build and serve the website locally:

```bash
pip install -r requirements.txt
./run_web.sh
```

Or run directly:

```bash
mkdocs serve
```

See `run_web.sh` for options (e.g., custom port, public interface, GitHub token).

## Deployment

**Manual:**  

Deploy to GitHub Pages with:

```bash
mkdocs gh-deploy
```

**Automated:**

GitHub Actions build and deploy the site on push to `main` (see `.github/workflows/`).  
The workflow fetches the latest content from the upstream MASTG, MASVS, and MASWE repos before building.

## Site Structure

- All source files are in the `docs/` directory.
- Navigation and content aggregation are configured in `mkdocs.yml`.
- The site uses plugins such as `mkdocs-awesome-pages-plugin` and `mkdocs-material`.

## Contributing

Website improvements, bug fixes, and documentation updates are welcome!
See [our contributing guidelines](https://mas.owasp.org/contributing/) for details.
