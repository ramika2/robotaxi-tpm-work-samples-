# Case B — Metrics (PUDO + HMI)

## Why p95 matters 

- PUDO pain is long-tail: a few extremely bad pickups can decide whether users return; p95 reflects this better than averages.


## Core metrics
M1 Pickup success rate  
boarded + trip started / pickup requests.

M2 Time-to-pickup p95  
p95 of time from vehicle arrival at viable point → rider boarding confirmation.

M3 Cancellation rate (bucketed)  
buckets: can’t find car / too long wait/relocation/safety concern/rider/system.

M4 Curb dwell time p95  
p95 curb dwell from stop state → boarded (or cancel/relocate).

M5 Relocation rate  
orders with relocations / total orders (or relocations per order).

M6 Support contacts per 100 trips  
support/RA touches as ops cost proxy.

## Minimum logging fields 
- requested_point / actual_pickup_point / displacement  
- walk ETA / wait ETA / chosen mode（Fast vs Closest）  
- incident flags（construction/closure/no-stopping/congestion proxy）  
- outcome + cancellation bucket



## References
- Waymo wait-time notes: https://support.google.com/waymo/answer/14249592

