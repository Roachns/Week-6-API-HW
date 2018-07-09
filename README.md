# WeatherPy Homework

In this example, I've created a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To accomplish this, I've utilized a [simple Python library](https://pypi.org/project/citipy/), the [OpenWeatherMap API](https://openweathermap.org/api),and a little common sense to create a representative model of weather across world cities.

My objective was to build a series of scatter plots that showcase the following relationships:
- Temperature (F) vs. Latitude
- Humidity (%) vs. Latitude
- Cloudiness (%) vs. Latitude
- Wind Speed (mph) vs. Latitude

My final notebook will:
- Randomly select at least 500 unique (non-repeat) cities based on latitude and longitude.
- Perform a weather check on each of the cities using a series of successive API calls.
- Include a print log of each city as it's being processed with the city number and city name.
- Save both a CSV of all data retrieved and png images for each scatter plot.
