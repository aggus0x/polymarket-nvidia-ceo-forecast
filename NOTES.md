# Polymarket NVIDIA CEO forecast — build notes

Entry: `main.py` (Python 3.13, stdlib only). Persistence forecast with a
per-market robust volatility: sigma = mean |1-minute move| over the last
360 minutes x 1.2533, floored at 0.0003, capped at 0.01; spread at horizon
h is sigma x sqrt(h), capped at 0.05 total. No drift (tested, hurt).

Local practice score (p00-p04, answers from the next case's input):
mean pinball loss 0.320615 vs house baseline 0.398458.
Per case: p00 0.4469, p01 0.3172, p02 0.3556, p03 0.2719, p04 0.2116.
Runtime ~0.12s per case (cap 8s); output ~0.28 MB max (cap 1 MB);
two runs byte-identical (deterministic).
