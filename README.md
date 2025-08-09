# OWASP Mobile Application Security Project Website

This repository contains the source and configuration for the **OWASP Mobile Application Security Project website** ([mas.owasp.org](https://mas.owasp.org/)).

## OWASP MAS Resources Overview

| Resource | Description |  | GitHub Repo |
|----------|-------------|-------|------------|
| <img src="docs/assets/masvs_cover.png" alt="MASVS Cover" width="60" /> | **MASVS (Mobile Application Security Verification Standard)** <br> The industry standard for mobile app security requirements. |  | [OWASP/masvs](https://github.com/OWASP/masvs) |
| <img src="docs/assets/maswe_cover.png" alt="MASWE Cover" width="60" /> | **MASWE (Mobile Application Security Weakness Enumeration)** <br> A categorized list of common security and privacy weaknesses in mobile apps. |  | [OWASP/maswe](https://github.com/OWASP/maswe) |
| <img src="docs/assets/mastg_cover.png" alt="MASTG Cover" width="60" /> | **MASTG (Mobile Application Security Testing Guide)** <br> A comprehensive manual for mobile app security testing and reverse engineering. |  | [OWASP/mastg](https://github.com/OWASP/mastg) |

## Development

This website aggregates, organizes, and presents documentation from the main MAS resources using [MkDocs](https://www.mkdocs.org/) and the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) theme.

The site structure is as follows:

- All source files are in the `docs/` directory.
- Navigation and content aggregation are configured in `mkdocs.yml`.
- The site uses plugins such as `mkdocs-awesome-pages-plugin` and `mkdocs-material`.

## Local Development

To build and serve the website locally see [this guide](https://mas.owasp.org/contributing/7_Run_the_Website/).

## Deployment

GitHub Actions build and deploy the site on push to `main` (see `.github/workflows/`).  
The workflow fetches the latest content from the upstream MASTG, MASVS, and MASWE repos before building.

## Contributing

Website improvements, bug fixes, and documentation updates are welcome!
See [our contributing guidelines](https://mas.owasp.org/contributing/) for details.
