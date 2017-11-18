# Week-6-API-HW
Week 6 Homework
import json 
import requests
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import random
import openweathermapy as ow
import seaborn as sns

lat = []
lon = []
cities = set([])

while len(cities) < 1500:
    lati = (random.randrange(-90,90,1))
    long = (random.randrange(-180,180,1))
    city = citipy.nearest_city(lati,long)
    city = city.city_name
    lat.append(lati)
    lon.append(long)
    cities.add(city)
    
cities = list(cities)

api_key = "100e237d34c869e8b182ed6faeb536e9"
setting = {"units": "IMPERIAL", "appid": api_key}

weather_data = []
counter = []
count = 0

for city in cities:
    if count < 500:
        try:
            data = ow.get_current(city, **setting)
            weather_data.append(data)
            count = count + 1
            counter.append(count)
        except Exception as e:
            print(f"{city}: {e}, no weather data")
            continue
          
weather_data

summary = ["name", "dt", "sys.country", "main.temp_max", "coord.lat", "main.humidity", "clouds.all", "wind.speed"]
data = [response(*summary) for response in weather_data]
column_names = ["City", "Time", "Country", "Temperature", "Latitude", "Humidity", "Cloudiness", "Wind Speed"]
weather_data = pd.DataFrame(data, index=counter, columns=column_names)
weather_data

cities_list = weather_data

plt.scatter(weather_data["Latitude"], weather_data["Temperature"], marker="o")


plt.title("City Latitude vs. Max Temperature (11/18/17)")
plt.ylabel("Max Temperature (F)")
plt.xlabel("Latitude")
plt.grid(True)

plt.savefig("TemperatureInWorldCities.png")

plt.show()



plt.scatter(weather_data["Latitude"], weather_data["Cloudiness"], marker="o")

plt.title("City Latitude vs. Cloudiness")
plt.ylabel("Humidity (%)")
plt.xlabel("Latitude")
plt.grid(True)
plt.savefig("CloudinessInWorldCities.png")

plt.show()



plt.scatter(weather_data["Latitude"], weather_data["Wind Speed"])

plt.title("City Latitude vs. Wind Speed")
plt.ylabel("Wind Speed (mph)")
plt. xlabel("Latitude")
plt.grid(True)
plt.savefig("WindSpeedInWorldCities.png")

plt.show()


plt.scatter(weather_data["Latitude"], weather_data["Humidity"], marker="o")

plt.title("City Latitude vs. Humidity")
plt.ylabel("Humidity (%)")
plt.xlabel("Latitude")
plt.grid(True)
plt.savefig("HumidityInWorldCities.png")

plt.show()
