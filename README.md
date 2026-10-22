# Running a team of coding agents: case study

How I run several AI coding and ops agents on real products without losing control of quality or production. Write-up only; no infrastructure details, credentials or client information.

## The setup
- Each agent has one job (builder, QA, release, research) and works one tracked issue at a time.
- Agents never ship on their own judgment alone: a scripted **release gate** decides.

## Release gate
```
 commit ─► test suite ─► build ─► deploy ─► health check ─┬─► keep
                                                          └─► automatic rollback
```
- Tests must pass before deploy; a failed health check restores the previous release.
- Data-changing operations take a verified backup first and write an audit record.

## Human approval built in
- Anything outward-facing (emails, posts, purchases, account changes) is drafted and shown to me as an approval card; nothing goes out until I approve.
- Schema changes and production data changes need an explicit yes.
- Agents report outcomes and decisions, not activity.

## What I learned
- A fast, trustworthy test gate matters more than a smart agent. Cutting gate time roughly in half made agents far more productive.
- One issue per builder prevents agents from overwriting each other's work.
- Approval cards keep the speed of automation without giving up accountability.

*Illustrative only. No code, hostnames or secrets from the real system are included.*
