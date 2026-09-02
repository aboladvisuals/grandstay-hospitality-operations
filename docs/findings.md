# Findings and recommendations

Evidence only. No modelled savings.

## TIME

- 120,000 tickets, 9 Jul 2025–7 Oct 2025.
- Mean FRT 10.04 min; median FRT 4.72 min.
- Mean handle 18.09 min; median handle 13.37 min.
- SLA met 28.09% (breach 72%).
- No negative FRT (min 0.3) or work interval (min 4.5).
- Live-channel FRT ~5 min; Email ~38.7 min.
- Phone SLA met 15.28%; Chat 23.00%; Email 47.68%; Front-Desk 60.77%.
- Peak FRT 12.60 vs off-peak 5.72.
- At peak, Chat/Phone/Front-Desk ~2.8 → ~6.2 min; Email ~21.9 → ~48.9 min.
- Handle time ~18 min on every channel.

**Read:** The 10-minute company average is a mix effect. SLA failure is a tight-target + peak-capacity problem on Phone and Chat.

## SCALE

- Repetitive flag 72,137 / 120,000 = 60.11%.
- Repetitive: FRT 6.89, handle 10.76.
- Not repetitive: FRT 14.79, handle 29.14.
- Peak holds 75,419 tickets (63%).
- High-volume regions noted from ticket pivots: US East, Australia, Japan.
- High-volume hours: 8, 16, 18 (also slower FRT).
- Top categories ~5.9k–6.2k each: Late Checkout, Breakfast Time, Gym Hours, Cancellation Policy, Check-in Time, Wi-Fi Password, Pet Policy, Minibar Price.

**Read:** Most contacts are short, repeated guest questions. Complex work is the minority of tickets and the majority of handle time.

## COST (Nov 2024–Oct 2025)

- Inquiries 11,649 → 16,219 (+39%).
- Cost per contact $52.71 → $58.61 (12-month average $55.16).
- Utilisation 86.0% → 72.8%.
- Overtime hours 1,196 → 1,824.
- October missed revenue field $40,678 (November 2024 was $23,787 — do not swap them).

**Read:** The operation scaled demand with more expensive, less utilised labour.

## AUTOMATION (knowledge sample n = 5,000)

FAQ-style categories: low KB search (~0.5 min) and low per-ticket “time saved” (~1.4–1.8 min).
Complex categories (Legal, Billing, Emergency, Complaint, Contract, Allergy, Accessibility): high KB search (~6 min) and high “time saved” (~14–16 min) because the tickets are already long.

**Read:** Do not rank a concierge by that time-saved column.

## Recommendations

| # | Finding | Action | KPI to watch |
|---|---|---|---|
| 1 | Peak doubles live-channel FRT; Phone/Chat miss SLA | Staff and route Chat/Phone at peak | FRT and SLA met by channel × peak |
| 2 | 60% repetitive; handle 10.8 vs 29.1 | Pilot FAQ concierge on Chat with human handoff | Repetitive volume, automation resolution, FRT, cost/contact |
| 3 | Time-saved field peaks on legal/emergency | Keep those categories human | Escalation rate and CSAT on those categories only (report sample size) |
| 4 | Volume +39%, cost/contact up, utilisation down, OT up | Review roster vs peak; do not hire 1:1 with tickets | Cost/contact, OT, utilisation |
| 5 | Mean FRT 10 hides channel mix | Report median + channel FRT | Median FRT; FRT and SLA by channel |
| 6 | Missed revenue is a field, not a recovery model | Monitor only | Monthly missed revenue |

## Limits

- No CSAT conclusion.
- Knowledge file is a sample.
- Cost table does not slice by channel.
- Ticket-level mean FRT and cost-file monthly response averages do not match; different definition or mix.
- No post-automation outcome in the data.
