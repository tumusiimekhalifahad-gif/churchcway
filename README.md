# Christ Way Church Management System — Cloudflare D1/Workers

This is a Cloudflare-native starter application with a dashboard, first-admin setup, login/logout, role/module gating, branch-scoped data access and basic create/list workflows for members, attendance, visitors, MCs, ministries, events, finance and pastoral care.

## Deploy
1. Create a GitHub repository and upload the contents of this folder.
2. Install Node.js (20+) and run `npm install -g wrangler`.
3. Run `wrangler login`.
4. Create a D1 database: `wrangler d1 create christ-way-church-system`. Copy the database ID into `wrangler.toml`.
5. Apply schema: `wrangler d1 execute christ-way-church-system --remote --file=migrations/0001_schema.sql`.
6. Deploy: `wrangler deploy`.
7. Open the Workers URL. The first visit will show first administrator setup. Choose a long, unique password.

You may also use Cloudflare's Git deployment integration for Workers if enabled in your account. Wrangler deployment is the simplest documented route for this starter.

## Important limitations before real production data
- This is an early operational starter, not a fully audited production system. Perform independent security review and test role/branch boundaries before entering real or sensitive records.
- Initial administrator setup is one-time (the endpoint refuses to run after the first account). Do not expose any account credentials in the repository.
- User creation currently requires administrator-level access; user branch access is assigned from the supplied branch IDs.
- No password reset, MFA, email verification, automated backups, member editing, or export/import workflow yet.
- Finance and pastoral-care deletion is blocked in the interface/API; change history is currently a simple audit log, not a full immutable ledger.
- Set up D1 backups, review logs, and protect the repository. Treat pastoral-care notes as sensitive and avoid entering them until security testing is completed.

## Branches seeded
- Christ Way Church Najjera
- Christ Way Church Bulindo
- Christ Way Church Kyanjanja

## Role keys
`super_admin`, `pastor`, `branch_pastor`, `secretary`, `treasurer`, `mc_leader`, `ministry_leader`, `attendance_officer`, `data_entry`.
