# Planetary health datasets

Hands-on material for *Systems Science in Planetary Health*, a course of
the PhD programme in Planetary Health Studies at Universidade de Lisboa.
It holds four real datasets that link environmental measurements to
health, and one notebook to explore them.

## The notebook

`PlanetaryHealth_Datasets.ipynb` opens with a toolbox of one-line
commands, then takes each dataset through the same steps: a short description, a first look at the data, a starter model
compared with simple guesses, and a plot of what the model predicted
against what happened. Each section ends with seven points to explore.
The notebook is saved with its outputs, so it can be read here on GitHub
without running anything.

- **In the browser:** [open it in Google Colab](https://colab.research.google.com/github/QuantitativeBiology/PlanetaryHealth_SystemsScience/blob/main/PlanetaryHealth_Datasets.ipynb).
  A Google account is enough. Use *File → Save a copy in Drive* to keep
  your changes. The data are downloaded from this repository.
- **On your computer:** clone the repository and open the notebook with
  Jupyter from the repository folder. It needs Python 3 with pandas,
  numpy, matplotlib and scikit-learn. The data are read from `data/`.

## The datasets

| # | Dataset | One row is | Exposures | Health outcome |
|---|---|---|---|---|
| 1 | Chicago daily deaths, 1987–2000 | a day | temperature, humidity, PM10, ozone | deaths |
| 2 | Lisbon weekly mortality, 2000–2025 | a week | weather and air quality | deaths |
| 3 | SNS emergency visits, Portugal, 2013–2026 | a hospital group in a month | regional temperature | emergency visits |
| 4 | Dar es Salaam cholera cases, 2015–2018 | a suspected case | weather, district, water source | laboratory result |

## Files in `data/`

| File | Sources | Aggregation |
|---|---|---|
| `chicago_daily_1987_2000.csv` | NMMAPS study, from the R package `dlnm` | none |
| `lisbon_weekly_mortality_2000_2025.csv` | Eurostat weekly deaths; Copernicus ERA5-Land and CAMS via Open-Meteo | daily weather and hourly air quality averaged to weeks, for one point in central Lisbon |
| `sns_emergency_visits_monthly_2013_2026.csv` | SNS Portal da Transparência; NASA POWER | year-to-date counts turned into monthly counts, followed across changes of hospital name; daily temperature summarised per month for one city per health region |
| `ine_deaths_by_cause_region_2020_2021.csv` | INE, Estatísticas da Saúde 2022, table 6.3a | none; selected causes only |
| `cholera_daressalaam_cases_2015_2018.csv` | CholeraClima-TZ, Zenodo 22695115 | none; columns renamed |
| `cholera_daressalaam_weekly_2015_2018.csv` | the case file; Copernicus ERA5 via Open-Meteo | cases counted per week, weather added for every week |
| `bengal_cholera_monthly_1891_1941.csv` | github.com/DebbieShack/Bengal_cholera_data | census population attached per decade |

The last file is a bonus: monthly cholera deaths in British Bengal.

## Columns

**Chicago daily deaths.** `date`, `time`, `year`, `month`, `doy` (day of
year), `dow` (day of week); `death` (all causes except accidents), `cvd`,
`resp`; `temp` (mean temperature, °C), `dptp` (dew point, °F), `rhum`
(relative humidity, %), `pm10` (µg/m³), `o3` (ppb).

**Lisbon weekly mortality.** `week`, `week_start`, `year`,
`week_of_year`; `deaths_lisbon_ama` (Lisbon metropolitan area),
`deaths_portugal`; `tmean`, `tmax_mean`, `tmax_max`, `tmin_mean` (°C),
`rhum` (%), `days_tmax_over_35`; `pm10`, `pm25`, `o3`, `no2` (µg/m³).

**SNS emergency visits.** `month`, `year`, `month_of_year`, `region`,
`hospital_group`, `lat`, `lon`; `ed_visits_total`, `ed_visits_general`,
`ed_visits_paediatric`, `ed_visits_obstetric`, `ed_visits_psychiatric`;
`weather_city`, `tmean`, `tmax_mean`, `tmax_max`, `tmin_min` (°C),
`days_tmax_over_35`, `days_tmin_under_5`.

**INE deaths by cause.** `year`, `region`, `level`, then one column of
death counts per cause. `level` is `country`, `NUTS2` (nine regions that
together cover the country), `NUTS3` (sub-regions of Norte, Centro, Oeste
e Vale do Tejo and Alentejo) or `other` (unknown residence, abroad).

**Dar es Salaam cholera, cases.** `date`, `district`, `ward`, `age`,
`sex`, `occupation`; `diarrhoea`, `vomiting`, `severe_dehydration`;
`lab_positive` (1 = positive), `outcome`; `water_source`; `rainfall_mm`,
`tmax`, `tmin`, `tmean`, `trange`, `humidity`, `wind_dir`, `wind_speed`;
`clean_water_code`, `wastewater_code`, `political_code` (coded as
published; see the Zenodo record).

**Dar es Salaam cholera, weekly.** `week`, `suspected`, `lab_positive`,
`died`; `days_with_weather`, `rainfall_mm_mean`, `tmean`, `humidity`
(from the case file); `era5_rain_mm`, `era5_tmean`, `era5_humidity`.

**Bengal cholera.** `division`, `district`, `year`, `month`, `date`,
`cholera_deaths`, `census_year`, `population`, `area_sq_miles`,
`deaths_per_100k`.

## Sources and attribution

- **Chicago:** US National Morbidity, Mortality and Air Pollution Study,
  distributed with the R package `dlnm` (A. Gasparrini).
- **Lisbon deaths:** Eurostat, table `demo_r_mwk3_t`.
- **Lisbon weather and air quality:** contains modified Copernicus
  Climate Change Service and Copernicus Atmosphere Monitoring Service
  information (ERA5-Land and CAMS), retrieved through Open-Meteo.
- **Emergency visits:** Portal da Transparência do SNS (CC BY 4.0).
- **Regional temperature:** NASA POWER.
- **Deaths by cause and region:** INE, *Estatísticas da Saúde 2022*.
- **Dar es Salaam cholera:** CholeraClima-TZ, Zenodo record 22695115
  (CC BY 4.0); weekly weather from Copernicus ERA5 via Open-Meteo.
- **Bengal cholera:** D. Shackleton,
  github.com/DebbieShack/Bengal_cholera_data.
