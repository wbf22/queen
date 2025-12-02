very_heavy_bleeding
heavy_bleeding
medium_bleeding
light_bleeding
spotting
positive_pregnancy_test
faintly_positive_pregnancy_test
negative_pregnancy_test
fatigue
tender_breasts
cramps
positive_ovulation_test
faintly_positive_ovulation_test
negative_ovulation_test
sick
stress


You can treat “medium_bleeding”, “heavy_bleeding”, or “very_heavy_bleeding” as likely **cycle day 1** indicators.

Once you have several detected periods:

* average_cycle_length = mean(days_between_period_starts)
* variation = standard deviation

Then:
**predicted next period = last_period_start + average_cycle_length**

You can refine it with weighted averages or recent-cycle weighting.

Apps generally estimate ovulation using **patterns**, not certainty.
Common signals (non-medical):


After ovulation, progesterone rises → slight **BBT increase** (~0.2–0.5°C or °F).
General, safe pattern logic:

```text
Look for a sustained temperature rise over 3+ days
Ovulation *likely* happened 1 day before the rise begins
```

Not guaranteed. Many factors influence temperature.


"positive_ovulation_test" suggests luteinizing hormone (LH) surge.
Non-medical pattern used by apps:
```text
Ovulation likely occurs 12–36 hours after a positive ovulation test
```


Some apps weight signals:
* BBT rise
* ovulation test result
* symptoms (cramps, tender breasts, etc.)
And combine them into a **probability window** rather than a specific day.



* positive_pregnancy_test
* faintly_positive_pregnancy_test
→ App typically switches to **pregnancy mode** manually or automatically.
You can simply reflect the user’s logged test result.
If predicted period is missed by several days:

```text
Show: "Your period is later than expected" 
Not: "you are likely pregnant"
```


Fatigue, tender breasts, nausea, etc. are **not indicators**; apps should **never infer pregnancy** from them.
But you *can* log them and show timelines, trends, or correlations.


## Summary
```
On each day:
  if bleeding is medium/heavy/very_heavy:
    mark day as period start
    recalc averages
```

```
next_period = last_period_start + average_cycle_length
```

Combine:
* last positive ovulation test
* BBT 3-day rise pattern
* average ovulation day from past cycles (e.g., cycle_length - luteal_phase_length_guess)

Then mark a **fertile window**, not an exact date.

E.g.:

```
fertile_window = (estimated_ovulation_day - 4) → (estimated_ovulation_day + 1)
```

---

## ➤ **Pregnancy handling**

```
If positive pregnancy test logged:
    switch to pregnancy mode
If late period detected:
    show neutral message like:
    "Your period is later than expected. Consider taking a test if relevant."
```

No interpretation of symptoms.

---
