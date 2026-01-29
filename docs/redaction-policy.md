# Redaction Policy

Last updated: January 29, 2026

## Objective
Publish documentation without exposing code, secrets, or personal data.

## Must Never Be Published
- Source code
- Credentials, API keys, or connection strings
- Database dumps or real records
- Personal data (names, IDs, phone numbers)
- Internal IPs, hostnames, or infrastructure details

## Allowed Content
- Documentation files
- Architecture diagrams with generic labels
- Redacted screenshots (no real data)

## Pre-Publish Checklist
1) Scan files for secrets
2) Remove or mask any sensitive text
3) Verify there is no code or config with credentials
