# GrandStay Hospitality — Operations Intelligence

> **Portfolio case study:** https://aboladvisuals.github.io/projects/grandstay-hospitality-operations/

Portfolio case study: guest-support baseline for a global hospitality group (luxury, business, and extended-stay).

**Analyst:** [aboladvisuals](https://github.com/aboladvisuals)  
**Tools:** Excel, Power Query, PivotTables, Power BI, PowerPoint (recommendations)  
**Grain:** 120,000 tickets (9 Jul–7 Oct 2025) + 12 monthly cost rows (Nov 2024–Oct 2025)

This repo documents the analysis. It does not claim a live production dashboard or an implemented chatbot.

---

## Problem

GrandStay guest support was under pressure from slow first response, missed SLAs, repetitive guest questions, rising cost per contact, falling utilisation, and rising overtime. Leadership was considering an Intelligent Travel Concierge. This project built a measurable TIME / SCALE / COST baseline first.

---

## Dashboard

### 1 — Executive

![Executive dashboard](executive%20dashboard%20grandstay.png)

| KPI | Result |
|---|---|
| Tickets | 120,000 |
| Median FRT | 4.7 min |
| SLA met | 28.09% |
| Median handle | 13.37 min |
| Repetitive | 60.11% |
| Cost / contact (Oct 2025) | $58.61 |

Mean FRT was 10.0 minutes. Median is 4.7 because Email (~39 min) pulls the mean. Live channels sit near 5 minutes.

### 2 — Time and demand

![Time and demand](grandstay%20time%20%26%20demand%20ss.png)

| Channel | SLA met | Off-peak FRT | Peak FRT |
|---|---|---|---|
| Phone | 15.28% | 2.80 | 6.20 |
| Chat | 23.00% | 2.78 | 6.22 |
| Email | 47.68% | 21.91 | 48.90 |
| Front-Desk | 60.77% | 2.79 | 6.24 |

Peak hours more than double live-channel wait. Top volume categories are FAQs (Late Checkout, Breakfast Time, Gym Hours).

### 3 — Cost and workforce

![Cost and workforce](grandstay%20cost%20%26%20workforce%20screenshot.png)

Nov 2024 to Oct 2025:

| Measure | First | Last |
|---|---|---|
| Inquiries | 11,649 | 16,219 (+39%) |
| Cost per contact | $52.71 | $58.61 |
| Utilisation | 86.0% | 72.8% |
| Overtime hours | 1,196 | 1,824 |

---

## Findings

**TIME.** 72% of tickets missed SLA. Phone and Chat fail because targets are 1.5–2 minutes, not because they are slower than Email.

**SCALE.** 60% of tickets are flagged repetitive and take 10.8 minutes of handle time versus 29.1 for other work.

**COST.** Volume +39% while cost per contact rose and utilisation fell. Overtime rose from 1,196 to 1,824 hours.

**Automation.** Do not rank a concierge by “minutes saved” in the 5,000-row knowledge sample. That field is largest on Legal, Billing, Emergency, Complaint and Contract because those tickets are already long.

Full write-up: [docs/findings.md](docs/findings.md)  
CV wording: [docs/cv-blurb.md](docs/cv-blurb.md)

---

## Recommendations

1. Staff and route Chat and Phone in peak hours before buying a new tool. Keep Email on its 30-minute target.
2. Pilot a concierge on repetitive FAQ categories on Chat, with a human handoff for non-standard asks.
3. Do not automate Legal, Emergency, Complaint, Contract or Billing first.
4. Review roster versus peak. Do not hire 1:1 with monthly ticket growth.
5. Report median FRT and FRT by channel. Stop using 10 minutes as the company wait time.
6. Treat missed revenue ($40,678 in Oct 2025) as a monitor, not a promised automation recovery.

---

## Data and method

| Source | Grain | Rows |
|---|---|---|
| Agent performance logs | 1 ticket | 120,000 |
| Cost efficiency metrics | 1 month | 12 |
| Knowledge / escalation sample | 1 ticket | 5,000 |
| Inquiry volume patterns | hour x region x channel | 43,125 |

Power Query metrics: `FRT`, `HANDLE_TIME_MIN`, `SLA_STATUS` using each ticket's own `sla_target_min` (Phone 1.5, Chat 2, Front-Desk 5, Email 30). Ticket and cost tables were not joined.

## Limits

No CSAT conclusion. Knowledge file is a sample. Cost cannot be sliced by channel. No bot was implemented. No hours-saved or dollar-saved outcome exists in this dataset. The `.pbix` and 50MB Excel workbook stay off GitHub on purpose.
