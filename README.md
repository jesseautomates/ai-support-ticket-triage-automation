# AI Support Ticket Triage Automation

This project demonstrates an AI-powered workflow that automatically **classifies, enriches, and routes support tickets**.

The system simulates how support operations teams can use AI and automation to reduce manual triage work and improve ticket routing speed.

Built using **n8n**, **OpenAI**, and **Google Sheets**.

---

## Architecture

[![Architecture](images/architecture-diagram.png)](https://github.com/jesseautomates/ai-support-ticket-triage-automation/blob/main/workflow/data/images/architecture-diagram.png)

---

## Workflow Overview

The automation processes incoming support tickets through the following stages:

1. **Ticket ingestion**
   Support tickets are loaded from a dataset stored in Google Sheets.

2. **Schema normalization**
   Ticket fields are standardized so downstream systems can process them consistently.

3. **AI classification**
   Each ticket is analyzed using OpenAI to determine:

   * category
   * urgency
   * sentiment
   * recommended support queue
   * escalation flags
   * confidence score

4. **Response validation**
   The workflow checks for malformed or empty AI responses.

5. **Fallback logic**
   If the AI response fails validation, fallback classification logic is applied to ensure reliable routing.

6. **Priority enrichment**
   Additional operational signals are calculated:

   * `vip_flag`
   * `sla_risk`
   * `priority_score`

7. **Queue routing**
   Tickets are routed to simulated support queues such as:

   * Tier 1 Support
   * Billing Operations
   * Technical Support
   * Customer Success
   * Product Feedback

8. **Operational logging**
   Each processed ticket is logged with routing decisions and enrichment data.

---

## Example Output Fields

The workflow produces operational metadata such as:

* `assigned_team`
* `destination_system`
* `delivery_action`
* `vip_flag`
* `sla_risk`
* `priority_score`
* `processed_at`

This simulates how production support systems track ticket routing and prioritization.

---

## Repository Contents

```
workflow/
    ai-ticket-triage-workflow.json

data/
    sample-support-tickets.csv

images/
    architecture-diagram.png
```

---

## How to Use

1. Import the workflow JSON into **n8n**
2. Load the sample ticket dataset
3. Connect your OpenAI credentials
4. Execute the workflow to simulate ticket triage

---

## Potential Extensions

This prototype could be extended with real integrations such as:

* Jira
* Zendesk

Next Project: [AI Support Escalation Risk Detection] https://github.com/jesseautomates/ai-support-escalation-risk-detection
