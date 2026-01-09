# Infowall.net

Production SonicJS instance for infowall.net - A modern information hub built on Cloudflare's edge platform.

## About

This is a production website built with [SonicJS](https://sonicjs.com), a TypeScript-first headless CMS designed for Cloudflare Workers. The site serves as both a real-world application and a testing ground for SonicJS features.

## Technology Stack

- **SonicJS** - Headless CMS on Cloudflare Workers
- **Cloudflare D1** - SQLite database at the edge
- **Cloudflare R2** - Object storage for media
- **Cloudflare KV** - Caching layer
- **TypeScript** - Type-safe development
- **Hono.js** - Web framework

## Getting Started

### Prerequisites

- Node.js 18+
- Cloudflare account
- Wrangler CLI

### Development Setup

```bash
# Install dependencies
npm install

# Create local D1 database
wrangler d1 create local-d1

# Update wrangler.toml with database_id from above

# Apply migrations
npm run db:migrate:local

# Seed admin user
npm run seed

# Start development server
npm run dev
```

Access the admin at: http://localhost:8787/admin

### Admin Credentials

- **Email:** mmcintosh@infowall.com
- **Password:** [as configured during setup]

## Deployment

### Preview Environment

```bash
# Deploy to preview
wrangler deploy --env preview
```

### Production

```bash
# Create production database
wrangler d1 create infowall-prod-db

# Update production wrangler config with database_id

# Apply migrations
npm run db:migrate

# Deploy
wrangler deploy --env production
```

## Project Structure

```
infowall/
├── src/
│   ├── collections/     # Content collection definitions
│   └── index.ts         # Worker entry point
├── migrations/          # Database migrations (from @sonicjs-cms/core)
├── scripts/             # Utility scripts
├── wrangler.toml        # Cloudflare configuration
└── package.json
```

## Documentation

- [SonicJS Documentation](https://sonicjs.com)
- [Cloudflare Workers Docs](https://developers.cloudflare.com/workers/)
- [Project Plan](../INFOWALL_PROJECT_PLAN.md)
- [Implementation Guide](../INFOWALL_IMPLEMENTATION_GUIDE.md)

## Related Repositories

- **SonicJS Core:** [mmcintosh/sonicjs](https://github.com/mmcintosh/sonicjs) (fork)
- **Upstream:** [lane711/sonicjs](https://github.com/lane711/sonicjs)

## License

MIT
