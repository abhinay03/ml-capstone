# Co-Presenter Script — ICE Train Delay Prediction

**Total:** 10 min | **Presenters:** 2 (P1, P2) | **Slides:** 12

---

## Setup (before starting)

- Open `presentation.html` in fullscreen browser (F11)
- Confirm both presenters can see the screen
- P1 controls keyboard navigation

---

## Slide 1 — Title

**Presenter:** P1 (30 sec)

> "Good morning. We're predicting ICE train delays using operational and weather data. This is our capstone project."

**Advance:** P1 presses Right Arrow

---

## Slide 2 — Why Should Anyone Care?

**Presenter:** P1 (45 sec)

> "Every day, millions of German passengers rely on ICE trains. Delays disrupt schedules and cause frustration. Our question: can machine learning predict these delays early enough to act?"

**Handoff:** "Let me hand over to P2 to explain what exactly we're predicting."

**Advance:** P1 presses Right Arrow

---

## Slide 3 — What Are We Predicting?

**Presenter:** P2 (60 sec)

> "Two tasks. Classification: will a stop be delayed by 6 or more minutes? That's an early warning. Regression: how many minutes late? That's severity. We're solving both."

**Advance:** P1 presses Right Arrow

---

## Slide 4 — What Data Did We Use?

**Presenter:** P2 (60 sec)

> "We used Deutsche Bahn's open dataset — 54.8 GB across months. We filtered to ICE trains in July 2024, which gave us 158K stops. After cleaning, 146K stops across 95 stations and 812 trains."

**Advance:** P1 presses Right Arrow

---

## Slide 5 — How Did We Combine Weather?

**Presenter:** P2 (75 sec)

> "The DB data has station IDs but no coordinates. We geocoded each station via Nominatim, then fetched hourly weather from Open-Meteo for every station. Merged on station and planned departure hour — using planned time avoids leaking the target. We matched 90.3% of rows."

**Handoff:** "P1 will walk through what the data revealed."

**Advance:** P1 presses Right Arrow

---

## Slide 6 — How Are Delays Distributed?

**Presenter:** P1 (60 sec)

> "57.7% of stops are on time, 42.3% are delayed. The mean delay is 10.5 minutes, but we've seen a max of 298 minutes. The distribution is right-skewed — most delays are small, but severe ones exist. This imbalance means accuracy alone is misleading, which is why we use F1 and ROC-AUC."

**Advance:** P1 presses Right Arrow

---

## Slide 7 — Does Weather Affect Delays?

**Presenter:** P1 (75 sec)

> "Looking at Pearson correlation: temperature at 0.13, rain and wind near zero. That looks like weather doesn't matter. But that's linear thinking. When we compare dry vs rainy conditions, we see delay rate jump from 41.6% to 44.5%. The effect is nonlinear — and Pearson misses it entirely. This is why we plan to use tree-based models."

**Handoff:** "P2 will explain how we cleaned the data."

**Advance:** P1 presses Right Arrow

---

## Slide 8 — How Did We Clean the Data?

**Presenter:** P2 (60 sec)

> "We started with 158K raw rows. Removed 11,497 cancelled trips — no target to predict. Standardized timezones to Europe/Berlin. Filled under 1K missing station names. Removed leakage columns like actual departure times. Result: 146K clean rows ready for modeling."

**Advance:** P1 presses Right Arrow

---

## Slide 9 — What Is Our Baseline?

**Presenter:** P2 (45 sec)

> "If we simply predict every train is on time, we get 57.7% accuracy. That's our minimum benchmark. Any real model must beat this. For classification we use F1 as primary metric and ROC-AUC for ranking quality. For regression, MAE tells passengers the average error in minutes; RMSE penalizes large mistakes."

**Advance:** P1 presses Right Arrow

---

## Slide 10 — What's Next?

**Presenter:** P2 (45 sec)

> "We'll build a full ML pipeline: feature engineering, baseline models, then Random Forest and XGBoost. The key experiment: Model A with operational features only, vs Model B with weather added. That directly answers whether weather improves prediction."

**Handoff:** "P1 will show how the code is organized."

**Advance:** P1 presses Right Arrow

---

## Slide 11 — How Is the Code Structured?

**Presenter:** P1 (45 sec)

> "Everything is organized into eight notebooks, each with one responsibility: problem definition, acquisition, cleaning, merge, EDA, features, models, and evaluation. The pipeline flows from acquire to clean to merge to EDA to train to evaluate. Each notebook outputs Parquet files for the next step."

**Advance:** P1 presses Right Arrow

---

## Slide 12 — What Did We Achieve?

**Presenter:** P1 (50 sec)

> "To summarise: we built an end-to-end ML pipeline integrating DB data with Open-Meteo weather. We cleaned and analysed 146K ICE stops. We have a leakage-safe dataset. Next up: feature engineering, model training, and comparing with and without weather to answer our research questions. Thank you."

---

## Timing summary

| Slide | Presenter | Time | Cumulative |
|-------|-----------|------|------------|
| 1     | P1        | 30s  | 0:30       |
| 2     | P1        | 45s  | 1:15       |
| 3     | P2        | 60s  | 2:15       |
| 4     | P2        | 60s  | 3:15       |
| 5     | P2        | 75s  | 4:30       |
| 6     | P1        | 60s  | 5:30       |
| 7     | P1        | 75s  | 6:45       |
| 8     | P2        | 60s  | 7:45       |
| 9     | P2        | 45s  | 8:30       |
| 10    | P2        | 45s  | 9:15       |
| 11    | P1        | 45s  | 10:00      |
| 12    | P1        | 50s  | 10:50      |

**Total:** ~10 min 50 sec (adjust pacing during rehearsal)

---

## Navigation notes

- P1 controls keyboard (Right Arrow to advance)
- Handoffs happen between slides (not mid-slide)
- If running short: expand on Slide 7 (nonlinear insight) or Slide 5 (weather pipeline)
- If running long: condense Slides 9 and 10
