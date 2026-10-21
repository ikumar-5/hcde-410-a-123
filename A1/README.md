# A1 — Working with Open Data

**Dataset:** Burke-Gilman Trail counter north of NE 70th St (hourly bike and pedestrian counts, by direction)
**Source:** <paste the dataset page URL here> (API ID `2z5v-ecg8`, pulled 2026-10-13)
**License / terms of use:** <copy from the dataset page, see below>

## Questions I asked
- Q1: When is the trail busiest and quietest?
- Q2: Do cyclists and pedestrians use the trail at different times of day?
- Q3: Is there evidence of commuting, not just recreation (weekday vs. weekend patterns)?
- Q4: Does direction of travel flip between morning and evening?

## How to re-run
Open `A1.ipynb` and run all cells (needs `requests`, `pandas`, `matplotlib`).
The notebook pulls 2019 data directly from the City of Seattle's API, so no data file is needed.

## Files
- `A1.ipynb`: the analysis and written answers
- `bg_hourly_2019.csv`: cleaned hourly data saved by the notebook
- `LICENSE`: license for this repository

## Notes
One limitation of the data is discussed at the end of the notebook. AI assistance used for code is documented in the notebook's AI-use note.

Adapted from cdsw-2020: https://wiki.communitydata.science/Seattle_open_data