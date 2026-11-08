# Smart Irrigation Advisor

ML 402331 — IoT Machine Learning Project (Fall 2026/2027), American University of Madaba

**Student:** Mustafa Juma (ID 2410102) — individual project
**Track:** Hardware  |  **Idea:** #4 Smart irrigation (ESP32 + soil moisture + DHT22)

## What this project does
An ESP32 reads soil moisture, air temperature and humidity every 5 minutes. A machine learning model predicts whether the soil will reach the plant's critical moisture level within the next 60 minutes, so the user gets a warning before the plant is stressed.

**Research question:** Can a classifier trained on my own ESP32 readings predict "soil reaches the critical level within 60 minutes" with F1 ≥ 0.85 on a held-out test set, and does it beat a plain moisture-threshold rule?

## Status
| Phase | Due | Status |
|---|---|---|
| 1 — Idea, problem, setup | End of Week 3 | Proposal, BOM and starter notebook in this repo |
| 2 — Device, data, baseline | End of Week 6 | Not started |
| 3 — Ensembles and tuning | End of Week 9 | Not started |
| 4 — SVM/clustering, live demo, report | End of Week 12 | Not started |

## Repository layout
```
notebooks/   Colab/Jupyter notebooks (Phase 1: phase1_starter_linear_regression.ipynb)
docs/        Phase 1 proposal (PDF)
hardware/    Bill of materials (CSV)
data/        Collected sensor data (CSV) — added in Phase 2
src/         ESP32 / Python logger code — added in Phase 2
```

## How to run the Phase 1 notebook
**Google Colab:** open `notebooks/phase1_starter_linear_regression.ipynb` from GitHub (Colab → File → Open notebook → GitHub tab) and choose *Runtime → Run all*.

**Locally:**
```bash
pip install -r requirements.txt
jupyter notebook notebooks/phase1_starter_linear_regression.ipynb
```
The notebook uses the Diabetes dataset bundled with scikit-learn, so it needs no downloads or API keys.

## Planned wiring (to be confirmed in Phase 2)
| Part | Pin on ESP32 |
|---|---|
| Capacitive soil moisture sensor, analog out | GPIO34 (ADC1) |
| DHT22 data (10 kΩ pull-up to 3.3 V if bare sensor) | GPIO4 |
| Sensor power | 3.3 V |
| Ground | GND |

## Planned data format (`data/`)
`timestamp, soil_raw_adc, soil_moisture_pct, air_temp_c, humidity_pct, watered_flag, needs_water_60min`

## AI-use statement
An AI assistant (Claude) helped draft the Phase 1 proposal, this README and the starter notebook. I reviewed the content and am responsible for it.

## References
- B. Efron, T. Hastie, I. Johnstone and R. Tibshirani, "Least angle regression," *Annals of Statistics*, vol. 32, no. 2, pp. 407–499, 2004.
- F. Pedregosa et al., "Scikit-learn: Machine learning in Python," *Journal of Machine Learning Research*, vol. 12, pp. 2825–2830, 2011.
