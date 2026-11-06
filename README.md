# Nurture

Crop planning with NASA Earth observation data.

Nurture is the project our team, **Team Tukhor**, built for the **NASA Space Apps Challenge 2023**. It placed **1st Runner-up at NASA Space Apps Challenge Bangladesh 2023**.

The idea is simple: farmers and agricultural officers should be able to decide what to grow, and where, from real data instead of guesswork. Nurture brings together NASA's soil moisture data (SMAP), MODIS vegetation and land data, tree canopy data and the GEOGLAM Crop Monitor, and turns them into suggestions, maps and charts that are easy to read.

## What it does

| Feature | What you get |
| --- | --- |
| Crop suitability | Enter the average temperature, annual rainfall and soil type of a piece of land, and Nurture lists the crops that suit it. |
| Tree canopy map | An interactive map of sample locations showing tree canopy, soil moisture and rainfall, coloured by canopy level. |
| Location search and dashboard | Search for a place on Google Maps and open a dashboard with charts for temperature, humidity, soil moisture, soil pH, rainfall, and flood and drought probability. |
| Tree canopy forecast | A linear regression script that estimates tree canopy five years ahead from historical readings. |
| Farming chatbot | Answers common farming questions in the browser by matching keywords. |

## Built with

- **Python:** Flask, pandas, scikit-learn
- **Web:** HTML, CSS, JavaScript, Leaflet, D3.js, Chart.js, Google Maps JavaScript API
- **Data sources:** NASA SMAP soil moisture, MODIS, tree canopy and vegetation data, GEOGLAM Crop Monitor

## Project structure

```
app.py                      Flask app for the crop suitability predictor
requirements.txt
templates/
    predictor.html          form and results page used by app.py
scripts/
    crop_suggestion_cli.py  the same crop suggestion logic, in the terminal
    tree_canopy_forecast.py tree canopy forecast with linear regression
web/
    home.html               landing page
    tree-canopy-map.html    tree canopy, soil moisture and rainfall map
    tree-canopy-map.js
    map-click.html          map with place search
    location-search.html    Google Maps place search
    place-dashboard.html    charts for the selected place
    chatbot.html            farming chatbot
    assets/
data/
    crop_suitability_data.csv   temperature, rainfall and soil ranges for each crop
    land_data.csv               sample land records
    map_points.csv              sample points for the map
    data.csv, dataset1.csv, dataset2.csv
```

## How to run

**Crop suitability predictor**

```bash
pip install -r requirements.txt
```

```bash
python app.py
```

Then open http://127.0.0.1:5000. Soil type is one of Sandy, Loamy or Clayey.

**Web pages**

Start a small local server from the project folder:

```bash
python -m http.server 8000
```

Then open http://localhost:8000/web/home.html.

The location search page needs a Google Maps API key. Put your own key in `web/location-search.html` in place of `YOUR_GOOGLE_MAPS_API_KEY`.

**Tree canopy forecast**

`scripts/tree_canopy_forecast.py` reads two CSV files of canopy readings (`data1.csv` and `data2.csv`) that share a `timestamp` column. Add your own files with those names and run it from the project folder.

## Notes

This is a hackathon prototype built in a weekend. The datasets in `data/` and the values on the place dashboard are small samples used for the demo, not complete NASA downloads.

## Team Tukhor

- **Md. Musfiqur Rahman Akib**: researcher and developer
- [@SamahFeroz](https://github.com/SamahFeroz)
- [@KTahmidS](https://github.com/KTahmidS)

The original hackathon repository is [SamahFeroz/TeamTukhor](https://github.com/SamahFeroz/TeamTukhor). This copy keeps its full commit history and organises the files into a cleaner structure.
