# weather
import requests

API_KEY = 'your_api_key_here'
BASE_URL = "http://api.openweathermap.org/data/2.5/weather?"

city = input("Enter city name: ")
URL = BASE_URL + "q=" + city + "&appid=" + API_KEY + "&units=metric"

response = requests.get(URL)

if response.status_code == 200:
    data = response.json()
    main = data['main']
    temperature = main['temp']
    humidity = main['humidity']
    pressure = main['pressure']
    weather = data['weather'][0]['description']

    print(f"Temperature: {temperature}°C")
    print(f"Humidity: {humidity}%")
    print(f"Pressure: {pressure} hPa")
    print(f"Weather Description: {weather}")
else:
    print("City not found.")
