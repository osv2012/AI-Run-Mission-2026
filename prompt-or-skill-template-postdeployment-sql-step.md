# Prompt Template: Add next post-deployment sql-script to SQL DDL script as next step in GH Action workflow

**Date:** 2026-07-13
**Author:** Sergei Osmachkin — SRE
**Project:** Azure infrastructure for dev team
**Model:** GitHub Copilot Chat
**DIAL location:** /
**Committed location:** https://github.com/osv2012/AI-Run-Mission-2026

---

## Purpose

Generates a GitHub Actions YAML step block that inserts a post-deployment SQL script into an existing DDL workflow, for a DevOps/SRE engineer, during CI/CD pipeline configuration for MS Fabric SQLDB gold schema deployments.

---

## Variable Placeholders

| Placeholder | Description | Example value |
|---|---|---|
| `{{step_name}}` | Label for the new workflow step | Add Id sequences to Gold schema |
| `{{env_variable_name}}` | Env variable name holding the new script's path | SEQUENCES_SQL_FILE |

---

## Output Format Instruction

YAML only, no preamble

---

## Prompt Body

Add new last workflow step with name {{step_name}} as azure/sql-action@v2.3 with template:
with:
  connection-string: ${{ secrets.FABRIC_SQL_CONNECTION_STRING }};Authentication=Active Directory Service Principal;User ID=${{ secrets.ARM_CLIENT_ID }};Password=${{ secrets.ARM_CLIENT_SECRET }}
  path: ${{ env.{{env_variable_name}} }}
  arguments: -b -V 11 -v SchemaName="${{ env.SCHEMA_NAME }}"

---

## Test Run (Author)

**Input values used:**
- `{{step_name}}` = Add Id sequences to Gold schema
- `{{env_variable_name}}` = SEQUENCES_SQL_FILE

**Output quality:** Output was a valid YAML step block with correct placeholder substitution — usable as-is.

---

## Peer Review

**Reviewer:** [Name — Role]
**Date reviewed:** YYYY-MM-DD
**Model used by reviewer:** [Model name]

**Reviewer input values used:**
- `{{placeholder_1}}` = [value reviewer used]
- `{{placeholder_2}}` = [value reviewer used]

| Review question | Reviewer answer |
|---|---|
| Could you run the template without asking the author anything? | Yes / No — [one sentence] |
| Was the output format what you expected? | Yes / No — [one sentence] |
| Would you use this template on your own work? | Yes / No — [one sentence] |
| One concrete improvement suggestion | [One sentence] |

---

## Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2026-07-13 | Initial commit, peer review pending | Sergei Osmachkin |
Peer review not completed — solo project, no reviewer available.
