# Case B — Research Notes (Deep Dive)

## Positioning

- This doc clarifies: inspiration → hypothesis → implementation path → evaluation → limitations & improvements.
- No implementation claims; it’s a verifiable research/delivery outline.


# Part 1 — Incident-aware PUDO 

## 1) Inspiration 

- Navigation apps surface incidents quickly by converting fleet behaviors + user feedback into signals that immediately shape recommendations.

## 2) Signals (tiered by trust)
- S1 Fleet telemetry (high trust): repeated stop failures, detours, abnormal slowing/braking, frequent relocations  
- S2 Rider prompts (medium trust): structured post-arrival feedback  
- S3 Ops/support/RA tags (high trust, sparse): work zones, police control, event egress, double-parking  
- S4 External feeds (availability varies): roadworks/closures, partner incident signals

## 3) Taxonomy 
- Temporary closures/work zones  
- No-stopping enforcement zones  
- Congestion/double-parking preventing curb access  
- Findability mismatch (human/vehicle coordination)

## 4) Product actions 
- A) Downrank/blacklist when failure signals spike over X hours  
- B) Auto-generate alternative rendezvous candidates per POI  
- C) Expose trade-off: Fast vs Closest (walk vs wait)  
- D) Ops hotspot list: top failing points + incident distribution

## 5) Evaluation
- A/B: compare p95, cancellation buckets, relocation rate with/without blacklisting  
- Event-day replay: verify tail spikes are dampened during work zones/events

## 6) Gaps & improvements 
- False positives/negatives: thresholds must avoid over-blacklisting  
- Cold start/sparsity: rules baseline + gradual learning  
- Fairness: underserved areas may lag  
- External feed availability varies by city

---

# Part 2 — Offset clustering 

## 1) Hypothesis 
- If requests at A consistently end up being served faster at nearby B/C, learn B/C as default rendezvous clusters.

## 2) Minimal dataset 
- requested_point, actual_pickup_point, displacement  
- walk ETA, wait time, dwell time  
- outcome (success/cancel/relocations)  
- incident tags (if available)

## 3) Outputs 
- 1–3 stable pickup clusters with: success rate, avg walk, time-to-pickup p95, dwell p95, blocking proxies
- Use: default Fast pickup points and fallback candidates when points fail

## 4) Linkage with incident-aware
- Clustering provides steady-state best points; incident sensing handles temporary disruptions
- When incidents disable a point, fall back to alternate clusters or rules baseline

## 5) Gaps & improvements
- Multi-objective trade-offs require explainable weighting  
- Avoid overfitting: online updates needed when conditions change  
- Selection bias: include cancellations, not only successful trips

---

## References 
- Apollo Go user experience: https://city.sina.cn/finance/2024-07-16/detail-incehuei4263596.d.html
- Waymo pickup constraints: https://support.google.com/waymo/answer/11419762

