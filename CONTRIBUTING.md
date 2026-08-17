# 🤝 Contributing to Beautify GitHub Profile

We love your input! We want to make contributing to this project as easy and transparent as possible, whether it's:

- Reporting a bug
- Discussing the current state of the code
- Submitting a fix
- Proposing new templates or widgets
- Becoming a maintainer

## How to Propose Changes

1. Fork the repo and create your branch from `main`.
2. If you've added code or templates, ensure they follow our [Best Practices](docs/best-practices.md) (adaptive dark/light mode, proper licenses, clean markdown).
3. Ensure no deprecated actions or broken APIs are included.
4. Issue that pull request!

## Standards & Guidelines
- All templates must support **Dark & Light Mode** using `<picture>` or clean contrast.
- Widgets must not rely on unstable or unauthenticated API endpoints where rate limits cause broken images.
- GitHub Actions workflows must specify explicit permissions (e.g. `permissions: contents: write`).

Thank you for contributing!
