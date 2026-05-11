# Lab 1 — NSG Troubleshooting (INC-0042)
**The VM That Cannot Talk**

## Scenario
A Windows VM was deployed in Azure and reported running, but the dev team
could not connect via RDP and had no outbound internet access.

## Problems Found
| # | Problem | Root Cause |
|---|---------|------------|
| 1 | RDP blocked | Deny-All-Inbound at priority 100 hit before Allow-RDP at priority 200 |
| 2 | No outbound internet | Outbound rule only allowed port 80 — HTTPS (443) was missing |

## How I Fixed It
- Swapped NSG inbound priorities using PowerShell
- Updated outbound rule to allow ports 80 and 443 using Azure CLI

## Tools Used
PowerShell · Azure CLI · Bicep

## Certification Alignment
AZ-104 — Configure and Manage Virtual Networking

## Evidence
- `Lab1_Incident_Report_INC0042.docx` — full incident report
- `lab1_proof.png` — fixed NSG rules + live RDP session + TcpTestSucceeded: True
