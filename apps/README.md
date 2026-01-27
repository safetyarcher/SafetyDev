# Applications

This directory contains subdomain applications with different tech stacks.

## Structure

Each application should have its own subdirectory:

- `app-name/` - Application root directory
  - `README.md` - Application-specific documentation
  - Source code and configuration files

## Example Applications

### .NET Web Application (Future)

```
apps/
  dotnet-webapp/
    README.md
    src/
    tests/
```

### Node.js API (Future)

```
apps/
  api/
    README.md
    src/
    package.json
```

## Deployment

Each application may have different deployment requirements:

- Configure subdomain DNS in Cloudflare
- Set up appropriate hosting (Azure, AWS, etc.)
- Configure CI/CD pipelines as needed

## Getting Started

When creating a new application:

1. Create a new directory under `apps/`
2. Add a README.md with setup instructions
3. Include tech stack-specific configuration
4. Update root README.md with project information
