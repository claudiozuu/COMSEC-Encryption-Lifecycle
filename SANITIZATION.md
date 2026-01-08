# OPSEC / Sanitization Note

For public sharing, ensure all screenshots and datasets are sanitized:

- Remove real key IDs, short titles, device identifiers, and unit-specific sensitive details.
- Use mock data when possible.

## What to Sanitize (Checklist)

### Screenshots (Power BI / Power Automate / Outlook)
- Key IDs / short titles
- Custodian names
- Unit names, org structure, and locations
- Device identifiers (radio IDs, serials, kit names, tail numbers, etc.)
- Email addresses, distribution lists, signatures
- Workspace / dataset names if they reveal unit/org

### Datasets / Exports (Excel/CSV)
- Key ID / Short Title
- Custodian
- Loaded On/Into Device
- Any notes/comments that reveal operational details
- Any unique identifiers that can be traced back to a unit/device

## Recommended Safe Replacements

- Replace Key IDs with: `KEY-001`, `KEY-002`, etc.
- Replace Short Titles with: `IW-SATCOM-A`, `FM-MONTHLY-A`, etc.
- Replace devices with: `DEVICE-01`, `DEVICE-02`
- Replace people with: `USER-A`, `USER-B`
- Replace units with: `UNIT-X`

## Verification Before Posting
- Zoom in on screenshots and confirm **no readable sensitive text**.
- Open images in full size to confirm blur/redaction is effective.
- Ensure no raw exports (CSV/XLSX) contain real identifiers.
