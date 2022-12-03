# lovelace-dhmz-weather-card
Home Assistant Custom Components for DHMZ weather service ("Državni hidrometeorološki zavod Republike Hrvatske" / "Croatian Meteorological and Hydrological Service")

The `dhmz` weather platform provide meteorological data for DHMZ service ("Državni hidrometeorološki zavod Republike Hrvatske / "Croatian Meteorological and Hydrological Service") - https://meteo.hr/ . Data from DHMZ is listed on https://meteo.hr/proizvodi.php?section=podaci&param=xml_korisnici and provided under Open Licence of Republic of Croatia - https://data.gov.hr/otvorena-dozvola and https://data.gov.hr/open-licence-republic-croatia .

This repository is custom weather card combining graphical forecast data in weather card. It is not standalone, 
it needs to be installed together with (https://github.com/kpisacic/DHMZ-home-assistant-custom-component) .

The following device types and data are supported:

- [Custom Weather Card](#custom-card) - Custom lovelace card with 5-days forecast and DHMZ specifics

## Installation

There are two options; manual or HACS installation:

*Manual installation*
- Create under your `www` folder subfolders `community`, and under it `lovelace-dhmz-weather-card`
- Copy `dhmz-weather-card.js` from `dist` repository folder to previously created `lovelace-dhmz-weather-card`

*HACS installation*

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)

- Use HACS custom repository (not default) - (https://github.com/kpisacic/lovelace-dhmz-weather-card)

## Custom card

To add custom card for DHMZ weather, add following to your lovelace configuration YAML file:

To add custom card for Štampar pollen forecast, add following to your lovelace configuration YAML file:

1. Add resources to lovelace configuration (iz using HACS installation, you can skip this point) `local/community/lovelace-dhmz-weather-card/dhmz-weather-card.js`

2. In views and cards section add following card

```yaml
    cards:
      - type: 'custom:dhmz-weather-card'
        mode: hourly
        weather: weather.dhmz_maksimir
        show_today_text: true
        show_tomorrow_text: true
```

With `weather` attribute you should state name of the entity configured in weather compontent.
For mode, please use `daily` or `hourly`, since `hourly` was mostly customized and tested and is preffered to be used.
Attribute `show_today_text` - shows today's text forecast (true|false), default is true.
Attribute `show_tomorrow_text` - shows tomorrow's text forecast (true|false), default is true.

