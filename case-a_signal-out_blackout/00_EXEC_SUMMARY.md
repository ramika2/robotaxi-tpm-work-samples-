# Case A - Blackout/Signal-out Robustness(Executive summary)
## 1) Problem
During city-scale outages or traffic-signal failures, robotaxis can become overly conservative and stall, causing intersection/critical-lane blocking, RA overload, trip disruption, and public/regulatory pressure.
example:

## 2) Why it matters
- High-visibility risk: blocking and disruptions directly impact trust and road order.
- For pilots and scaling, it's not only safety-operable degrade-and-recover matters.

## 3）MVP deliverables 
- Vehicle: define a signal-out mode + non-blocking-first behavior (avoid conflict zones; exit/pull over if needed).
- Service: tiered fallback (reroute → exit conflict zone → pull over → RA → terminate trip as last resort).
- Fleet: city-scale anomaly detection (event density/RA spikes/blocking) → ops actions (pause, shrink geofence, recall).
- Auditability: minimum logging schema + review template.


## 4) Key success metrics 
- Blocking events per 1,000 trips
- Blocking time p95
- Completion rate during outage windows
- RA load (minutes per trip + queue length if available)
- Logging completeness

## 5) V&V approach 
- Simulation/replay: 20-scenario regression suite (every release)
- Limited beta: low-risk windows, watch blocking + RA
- Monitoring: alert thresholds + rollback/pause playbook framework

## 6) Release gates (example)
- P0 safety issues = 0
- Blocking event rate not worse; blocking time p95 improves or does not regress
- RA load within ops capacity threshold
- Logging completeness ≥ 99%


## References (public) 
- Reuters (global robotaxi deployments & ops challenges): https://www.reuters.com/business/media-telecom/driverless-future-gains-momentum-with-global-robotaxi-deployments-2025-12-22/
- Waymo Help (operability context): https://support.google.com/waymo/answer/9696059
