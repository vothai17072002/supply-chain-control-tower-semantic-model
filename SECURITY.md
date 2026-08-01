# Security and confidentiality

This repository intentionally excludes source-system credentials, tenant/workspace identifiers, real records, proprietary DAX expressions, PBIX/PBIR exports, and organization branding.

If you find content that appears organization-specific or sensitive, open a private security report with the repository owner rather than a public issue.

## Production control model represented

- least-privilege workspace roles and managed deployment identities;
- separate review of workspace permissions, Build permission, RLS, and OLS;
- export, sharing, Analyze in Excel, and external-user controls;
- sensitivity labels, audit logs, and periodic access reviews;
- negative authorization tests for restricted personas;
- secret-free source control and parameterized environment bindings.

These are target controls described by the case study. This repository does not claim that a specific tenant's security posture was fully assessed.
