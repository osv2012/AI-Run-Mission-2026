# Model Selection Note

**Date:** 2026-07-13
**Author:** Sergei Osmachkin — SRE
**Project:** Azure infrastructure for dev team
**Task:** Create a plan for implementing a Premium Azure Function App using a Terraform module
**Committed location:** https://github.com/osv2012/AI-Run-Mission-2026

---

## Evaluation Criteria

| # | Criterion | Why it matters for this task |
|---|-----------|------------------------------|
| 1 | Accuracy — existing Azure Functions should remain completely outside the blast radius | Existing Azure Functions should remain completely outside the blast radius |
| 2 | Format compliance — output is formatted as a Terraform module | Output is formatted as Terraform module |
| 3 | Completeness — includes App Service Plan, Storage Account, Function App, app settings, no missing required arguments | Plan includes all required resources — App Service Plan, Storage Account, Function App, and app settings — with no obviously missing required arguments |

---

## Prompt Used

As Devops Engineer in accordance with best pactices:
Create plan for implementing Premium Azure Function App using Terraform module.
Existing Function Apps are deployed in resource group rg-existing-prod. The new module must use the same RG.
Creterias:
Accuracy - Existing Azure Functions should remain completely safe.
Format compliance - Output is formatted as Terraform module.
Completeness - Plan includes all required resources — App Service Plan, Storage Account, Function App, and app settings — with no obviously missing required arguments.

---

## Output Comparison

### Model A: [Model name]
> Gemini 3.5 Flash

### Model B: [Model name]
> GPT 5.5

---

## Scorecard

| Criterion | Model A score (1–3) | Model A evidence | Model B score (1–3) | Model B evidence |
|-----------|---------------------|------------------|---------------------|------------------|
| Accuracy | 1 | has a typo that breaks terraform init.  | 1 | deploys resources into the protected resource group. |
| Format | 3| Output included separate main.tf, variables.tf, and outputs.tf sections with correct HCL block structure. | 3 | Output included separate main.tf, variables.tf, and outputs.tf sections with correct HCL block structure. |
| Completeness | 3 | Output contained azurerm_service_plan (EP tier), azurerm_storage_account, azurerm_linux_function_app, and app_settings block with required keys. | 3 | Output contained azurerm_service_plan (EP tier), azurerm_storage_account, azurerm_linux_function_app, and app_settings block with required keys. |
| **Total** | 7 | | 7 | |

---

## Decision

**Selected model:** GPT 5.5

**Rationale:** Both models scored equally on format and completeness. On accuracy, both scored 1 — but Gemini's failure was a provider typo (fixable), while GPT's failure was deploying into the protected resource group (structural). I chose GPT because its completeness output was more directly actionable, and I will correct the resource group placement in my next prompt iteration.

---

## Active Constraint

**What could change this decision within 30 days:**
If EPAM engagement policy restricts GPT-5.5 access or DIAL updates Gemini's provider type, this decision reverts to Gemini.

---

## Revision history

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 2026-07-13 | Initial commit |
