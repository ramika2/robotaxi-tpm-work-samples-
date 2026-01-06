# Case B — PRD (PUDO + Rider HMI + Data Flywheel)

## 1) Goals
- Improve pickup success
- Reduce long-tail time-to-pickup (p95)
- Reduce relocations and cancellations
- Reduce long-tail curb dwell (p95) to minimize blocking/complaints

## 2) Users & stakeholders 
Riders, ops/support, RA (optional), city/partners (optional interfaces).

## 3) MVP functional requirements
### 3.1 Dual-mode pickup
FR1: Offer Fast vs Closest with walk ETA, wait ETA, and risk labels (likely relocation/longer wait).

FR2: Default to the most reliable option with an explainable rationale (more compliant, fewer relocations, lower tail).

### 3.2 Arrival confirmation & staging
FR3: stage off-curb until rider nears rendezvous; enter curb when rider is close; timeout triggers relocate/cancel.

### 3.3 Incident-aware PUDO
FR4: If failure signals spike over X hours, downrank/blacklist the point and generate alternatives.

### 3.4 Offset clustering 
FR5: Cluster requested→actual offsets per POI/area; output 1–3 stable clusters with success rate, p95 wait, walk mins, blocking proxies.

### 3.5 Findability & anti-misboarding
FR6:Last-50m guidance (landmarks + direction + “I’m here” light/flash handshake).

FR7: Anti-misboarding: short code on app + matching external display.


## 4) Non-goals
- No city-wide curb reservation/pricing system (only extensible interfaces)
- No perception/planning algorithm implementation details

---

## References
- Waymo pickup constraints (walk + countdown): https://support.google.com/waymo/answer/11419762

