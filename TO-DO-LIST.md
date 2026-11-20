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

- [x] Added a shallow histogram gradient boosting regressor to the notebook and recorded
  its fit time. It uses hour and weekday derived from the existing hour-of-week input,
  the holiday flag and the same 1-, 24- and 168-hour rental counts.
- [x] Compared all four methods on the 1,464 August–September hours after fitting through
  July. Boosting MAE was 114.8 versus 136.0 for calendar-plus-history ridge. At 09:00 it
  improved weekday MAE (294.1 to 156.3) and increased weekend MAE (69.8 to 80.8).
- [x] Froze `models["History gradient boosting"]` for B. Clone this pipeline and refit on
  `train` plus `valid` using `predictors`. The model cell specifies 100 rounds, depth 3,
  learning rate 0.1, at least 20 hours per leaf, squared-error loss, no early stopping
  and seed 42. Apply the same nonnegative clipping at prediction time.
- [x] Added and froze `models["Time-interaction ridge"]` as a second comparison. Keep
  the original ridge penalty of 1 and the same predictors. Let the standardized previous-hour
  count have one slope adjustment per clock hour and weekday/weekend group (48 in total).
  Validation MAE was 91.0 overall, 87.4 in August and 94.6 in September. B can clone
  and refit this pipeline alongside the frozen boosting model.

## Teammate B — Final evaluation and interpretation

After A freezes the model configuration, refit the learned methods on `train` plus `valid`.
Evaluate persistence, calendar ridge, calendar-plus-history ridge and both of A's models on the
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
