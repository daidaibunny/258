# Assignment 2 team handoff

## Completed by the project starter

- [x] Define a one-hour-ahead forecast and a chronological training, validation and test split.
- [x] Load and check 8,760 hourly observations, plot the time series and weekday/weekend profiles.
- [x] Implement previous-hour persistence, calendar ridge and calendar-plus-history ridge.
- [x] Compare the three methods on the same 1,464 August–September validation hours.
- [x] Measure the contribution of hourly, daily and weekly lags across four monthly refits.
- [x] Compare validation errors by hour and examine the 09:00 weekday and weekend forecasts.

## Teammate A — Model comparison

Add one nonlinear regression model to test whether a rental count has a different effect
at different hours of the day. A shallow gradient-boosted tree is one option. Use the same
calendar and lag inputs available at forecast time. Compare against the strongest existing
ridge model on the August–September validation rows, using the same July training cutoff.

**Deliverable:** a modeling subsection explaining the model, its settings and runtime,
plus a validation row and the model configuration that teammate B should refit. A clearly
explained negative result is a valid outcome.

## Teammate B — Final evaluation and interpretation

After A freezes the model configuration, refit the learned methods on `train` plus `valid`.
Evaluate persistence, calendar ridge, calendar-plus-history ridge and A's comparison on the
same 1,464 October–November hours. At each forecast time the previous hour's observed count
is available. Fit encoders and scaling on the training history only.

**Deliverable:** a final table in rentals per hour and an error-analysis figure. Report the
number of hours in each group if comparing operating and closure hours. Use group results or
a short forecast trace to explain where the model helped and where it struggled.

## Teammate C — Related work, presentation and submission

Find original studies on Seoul rentals or a comparable demand-forecasting task. Compare
their forecast horizon, available inputs and evaluation split with this project. Explain
which results can be compared directly and what could account for differences.

**Deliverable:** the related-work section with verified citations, plus a roughly 20-minute
presentation organized around the five rubric sections. A and B supply their model and
evaluation walkthroughs. C combines them with the existing data section and related work,
exports `workbook.html`, checks the video link and coordinates the Gradescope group submission.
The later peer-grading assignment has its own instructions.
