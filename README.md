# Facilities Management Platform

Production-oriented Facilities Management system for facilities, assets, work orders, inspections, contractors, procurement, SLA tracking, QR assets, maps, audit logs, notifications and PDF reporting.

## Stack
React + TypeScript + Vite · Node.js + Express + TypeScript · Prisma + PostgreSQL · JWT/RBAC · Leaflet/OpenStreetMap.

## GitHub → Azure
The repository is configured for GitHub Actions deployment to Azure App Service.

### Azure resources
Create:
1. Azure App Service for Linux using Node 20.
2. Azure Database for PostgreSQL Flexible Server.

### Required Azure App Service settings
Set these under Configuration → Environment variables:
- DATABASE_URL
- JWT_SECRET
- PORT=4000
- CLIENT_URL (leave empty when frontend and API use the same App Service URL)
- SMTP_HOST, SMTP_PORT, SMTP_USER, SMTP_PASS, SMTP_FROM if email notifications are enabled.

Use SSL for PostgreSQL, for example:
postgresql://USER:PASSWORD@SERVER:5432/facilities?sslmode=require

### GitHub settings
Repository variable:
- AZURE_WEBAPP_NAME = your Azure App Service name

Repository secret:
- AZURE_WEBAPP_PUBLISH_PROFILE = the Azure App Service publish-profile XML

After these are configured, pushing to main triggers the Azure deployment workflow.

## Local development
npm install
npm run db:migrate
npm run db:seed
npm run dev

Demo credentials used by the development seed are documented in the seed file. Change them before production use.

Never commit .env files, database passwords, JWT secrets, SMTP credentials or Azure publish profiles.
