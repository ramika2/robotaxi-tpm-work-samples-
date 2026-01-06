# Case B — PUDO + Rider HMI + Data Flywheel (Executive Summary)

## 1) Problem (user-perceived)
- The most visible robotaxi friction often happens at pickup (PUDO): long waits, constrained pickup points, and last-50m confusion. Even if the ride is stable and safe, long-tail p95 pickup experiences can dominate perception.


## 2) Why it matters 
- PUDO is heavily constrained by stopping rules, closures, congestion, and temporary controls; failures lead to cancellations and complaints.
- In stricter curbside environments, PUDO operability becomes a gating factor for scaling.


## 3) MVP (substantive change) / MVP
Upgrade “one pickup point” into “explainable choice + adaptive learning”:  
- A) Dual-mode: Fast vs Closest pickup  
- B) Incident-aware: downrank/blacklist failing points using fleet telemetry + rider feedback + ops tags; generate alternatives  
- C) Offset clustering: learn requested→actual offsets and cluster stable rendezvous points as Fast defaults

---

## 4) Key metrics
- Pickup success rate
- Time-to-pickup p95 (vehicle arrives at viable point → rider confirms boarding)
- Cancellation rate (bucketed)
- Curb dwell time p95
- Support/RA contacts per 100 trips

---

## 5) V&V
- Scenario regression (20): transit hubs/hospitals/malls, no-stopping zones, work zones, low light, event egress, etc.
- Limited pilots: 2–3 high-demand POIs with Fast + arrival confirmation + blacklisting; compare p95 and cancellation buckets
- Monitoring: blacklist + heatmaps + weekly review; rollback to rules baseline if needed

---

## References (public)
- Apollo Go user experience (designated pickup point & waiting uncertainty): https://city.sina.cn/finance/2024-07-16/detail-incehuei4263596.d.html
- Waymo pickup constraints (walk + countdown): https://support.google.com/waymo/answer/11419762
- Waymo wait-time specifics (busy roads may move; up to ~5 minutes): https://support.google.com/waymo/answer/14249592
- Example public-road L4 trial announcement (context): https://wayve.ai/press/wayve-uber-l4-autonomy-trials/

