# GrandStay Hospitality — Operations Intelligence

Portfolio case study: guest-support baseline for a global hospitality group (luxury, business, and extended-stay).

**Analyst:** [aboladvisuals](https://github.com/aboladvisuals)  
**Tools:** Excel, Power Query, PivotTables, Power BI, PowerPoint (recommendations)  
**Grain:** 120,000 tickets (9 Jul–7 Oct 2025) + 12 monthly cost rows (Nov 2024–Oct 2025)

This repo documents the analysis. It does not claim a live production dashboard or an implemented chatbot.

---

## Problem

GrandStay guest support was under pressure from:

- Slow first response and missed SLAs
- A large share of repetitive guest questions
- Rising cost per contact
- Falling agent utilisation and rising overtime
- Weak visibility (one company-wide average wait hid channel mix)

The organisation was considering an Intelligent Travel Concierge. The analysis was a **measurable TIME / SCALE / COST baseline** so any automation pilot would target the right work.

---

## Data

| Source | Grain | Rows | Used for |
|---|---|---|---|
| Agent performance logs | 1 ticket | 120,000 | FRT, handle time, SLA, channel, peak, category |
| Cost efficiency metrics | 1 month | 12 | Cost/contact, utilisation, overtime, volume |
| Knowledge / escalation sample | 1 ticket | 5,000 | Automation candidates, not company totals |
| Inquiry volume patterns | hour x region x channel | 43,125 | Supporting demand context |

Ticket data and the cost file are **different grains**. They were not joined. Channel slicers do not change monthly cost.

### Metrics created in Power Query

- `FRT` = first response minus created (minutes)
- `HANDLE_TIME_MIN` = (resolved minus first response) + after-call work
- `SLA_STATUS` = MET if FRT <= that ticket's `sla_target_min`, else BREACHED

SLA targets differ by channel (Phone 1.5 min, Chat 2, Front-Desk 5, Email 30). A single company target was not used.

---

## Dashboard

Three Power BI pages. Recommendations live in a slide deck, not a fourth report page.

Add screenshots to `images/` as `01-executive.png`, `02-time-demand.png`, `03-cost-workforce.png` (see note below).

### 1 — Executive

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

| Channel | SLA met | Off-peak FRT | Peak FRT |
|---|---|---|---|
| Phone | 15.28% | 2.80 | 6.20 |
| Chat | 23.00% | 2.78 | 6.22 |
| Email | 47.68% | 21.91 | 48.90 |
| Front-Desk | 60.77% | 2.79 | 6.24 |

Peak hours more than double live-channel wait. Highest-volume categories are standard FAQs (Late Checkout, Breakfast Time, Gym Hours, and similar).

### 3 — Cost and workforce

Nov 2024 to Oct 2025:

| Measure | First | Last |
|---|---|---|
| Inquiries | 11,649 | 16,219 (+39%) |
| Cost per contact | $52.71 | $58.61 |
| Utilisation | 86.0% | 72.8% |
| Overtime hours | 1,196 | 1,824 |

Volume grew while each contact got more expensive and paid time was used less efficiently.

---

## Findings (short)

**TIME.** 72% of tickets missed SLA. The failure is concentrated on Phone and Chat because those targets are 1.5-2 minutes, not because those channels are slower than Email. Peak (63% of tickets) is an amplifier: live-channel FRT moves from ~2.8 to ~6.2 minutes.

**SCALE.** 60% of tickets are flagged repetitive and take 10.8 minutes of handle time versus 29.1 for the rest. That is the first automation shortlist — high volume, shorter work, FAQ categories.

**COST.** Inquiries +39% in twelve months. Cost per contact $52.71 to $58.61. Utilisation 86% to 73%. Overtime 1,196 to 1,824. This is not a volume-only story.

**Do not sort automation by minutes-saved per ticket in the knowledge sample.** That field is largest on Legal, Billing, Emergency, Complaint and Contract because those tickets are already long. Those categories stay human.

---

## Recommendations

1. Staff and route to **Chat and Phone in peak hours** (demand also stacks around 08:00, 16:00, 18:00) before buying a new tool. Keep Email on its 30-minute target.
2. Pilot a concierge on **repetitive FAQ categories on Chat**, with a hard handoff when the guest is not asking a standard policy/hours question.
3. **Do not automate Legal, Emergency, Complaint, Contract or Billing first.**
4. Review roster versus peak and overtime rules. Hiring in a straight line with monthly ticket growth will not fix falling utilisation.
5. Report **median FRT and FRT by channel** to leadership. Stop using 10 minutes as the company wait time.
6. Treat the cost file's missed-revenue field as a **monitor**, not as a promised recovery from automation. October figure: $40,678.

Full write-up: [docs/findings.md](docs/findings.md)  
CV wording: [docs/cv-blurb.md](docs/cv-blurb.md)

---

## Limits

- CSAT is missing on a large share of tickets; no CSAT lift is claimed.
- Knowledge / escalation is a **5,000-row sample**, not 120,000 tickets.
- Cost cannot be sliced by channel or peak.
- Monthly cost-file averages for response time do not match ticket-level mean FRT. Different definition or mix — they were not forced to join.
- No concierge was implemented. No hours-saved or dollar-saved outcome exists in this dataset.

---

## Screenshots

Upload these three files on GitHub (Add file → Upload):

- `images/01-executive.png`
- `images/02-time-demand.png`
- `images/03-cost-workforce.png`

The `.pbix` (~9 MB) and staged Excel (~50 MB) stay on your machine. Git is the write-up and screenshots, not the data dump.

## License

Portfolio project for demonstration. Dataset is a case-study extract, not GrandStay production access.
