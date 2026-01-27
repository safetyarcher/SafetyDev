# SafetyDev

Personal projects hosted at **https://safetyarcher.com**

## Overview

This repository hosts multiple applications and tech stacks for my personal website. The domain and DNS are managed through Cloudflare.

## Repository Structure

```
SafetyDev/
├── www/                    # Static home page for TLD (safetyarcher.com)
│   ├── index.html
│   ├── styles.css
│   └── script.js
├── apps/                   # Subdomain applications
│   └── [future apps]       # .NET web apps, APIs, etc.
├── docs/                   # Documentation
│   └── CLOUDFLARE_SETUP.md # Cloudflare configuration guide
└── README.md              # This file
```

## Projects

### Static Home Page (TLD)
- **URL**: https://safetyarcher.com
- **Location**: `/www`
- **Tech Stack**: HTML, CSS, JavaScript
- **Hosting**: Cloudflare Pages

### Applications (Subdomains)
Future applications will be added to the `/apps` directory. Each application may use different tech stacks:
- .NET web applications
- Node.js APIs
- Python services
- And more...

## Getting Started

### Static Home Page (Local Development)

```bash
cd www
python -m http.server 8000
# OR
npx http-server
```

Navigate to `http://localhost:8000`

### Adding a New Application

1. Create a new directory under `apps/`:
   ```bash
   mkdir apps/my-new-app
   ```

2. Add a `README.md` with setup instructions

3. Develop your application with your chosen tech stack

4. Configure subdomain in Cloudflare (see [Cloudflare Setup Guide](docs/CLOUDFLARE_SETUP.md))

## Deployment

### Static Site (TLD)
- Deployed via Cloudflare Pages
- Automatic deployment from `main` branch
- See [Deployment Guide](docs/DEPLOYMENT.md) for step-by-step instructions
- See [www/README.md](www/README.md) for local development

### Applications
Each application has its own deployment strategy based on its tech stack. Refer to:
- [Deployment Guide](docs/DEPLOYMENT.md) for platform-specific instructions
- Individual app READMEs for application-specific details

## Cloudflare Configuration

Domain and DNS are managed through Cloudflare. See the [Cloudflare Setup Guide](docs/CLOUDFLARE_SETUP.md) for detailed configuration instructions.

## Tech Stacks Supported

This repository is designed to support multiple technology stacks:
- ✅ Static HTML/CSS/JavaScript
- 🔜 .NET (C#)
- 🔜 Node.js
- 🔜 Python
- 🔜 Any other stack as needed

## Contributing

This is a personal project repository. If you have suggestions or find issues, feel free to open an issue.

## License

© SafetyArcher. All rights reserved.
