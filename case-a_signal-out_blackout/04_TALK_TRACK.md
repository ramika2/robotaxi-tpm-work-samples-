# Case A — Talk Track


1) City-scale signal failures can push robotaxis into overly conservative stalls, causing blocking and RA overload.  
2) My MVP: signal-out mode + non-blocking-first + tiered fallback + fleet anomaly detection and ops actions.  
3) I track blocking p95/rate, RA load, and completion rate, validated via scenario regression, limited beta, and monitoring with rollback.

---

problem → MVP → metric definitions (why p95) → V&V → release gates → risks/open questions.

