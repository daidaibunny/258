# Forecasting hourly bike rentals in Seoul

At the beginning of an hour, how much does recent usage help predict citywide rentals?
The [executed notebook](seoul_bike_demand.ipynb) contains the data exploration, models,
figures and development results. [Team assignments and remaining work](TO-DO-LIST.md)
cover the final evaluation, presentation and submission.

In four monthly forecasts from June through September 2018, adding the previous hour's
rental count to a calendar model reduced mean absolute error from 533.6 to 154.1
rentals per hour. Adding counts from one day and one week earlier reduced it to 150.9.
On the held-out October–November test period, refit through September, a ridge model that
lets the previous-hour count have a different slope for each clock hour and day type reached
73.8 rentals per hour, against 108.4 for single-slope history ridge, 99.4 for gradient boosting
and 200.3 for repeating the previous hour.

## Run the notebook

From the repository root, use [uv](https://docs.astral.sh/uv/) to start JupyterLab.

```sh
uv sync --locked --python 3.12
uv run jupyter lab seoul_bike_demand.ipynb
```

The notebook downloads the CSV directly from UCI. An original `SeoulBikeData.csv` beside
the notebook also works offline. After the team finishes the notebook, this command
runs it from a fresh kernel and produces the course's required HTML file.

```sh
uv run jupyter nbconvert --execute --to html --output workbook seoul_bike_demand.ipynb
```

Dataset credit: S. Easwaramoorthy (2020), *Seoul Bike Sharing Demand*, UCI Machine Learning
Repository, licensed under CC BY 4.0. [Dataset and license](https://doi.org/10.24432/C5F62R)

See the [course instructions](Assignment%202%20instructions.pdf) for the full rubric.
