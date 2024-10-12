# OpenWeatherMap API

**Description**:  
The OpenWeatherMap API provides access to current weather data, forecasts, and historical data for any location on Earth. It offers several features such as real-time weather, UV index, air pollution data, and more.

**Authentication**:  
Requires an API key. You can sign up for a free API key at [OpenWeatherMap](https://home.openweathermap.org/users/sign_up).

**Base URL**:  
`https://api.openweathermap.org/data/2.5/`

---

## Endpoints

### 1. **Current Weather Data**

- **Endpoint**: `/weather`
- **Description**: Retrieves current weather data for a specific city.
  
- **Parameters**:
  - `q`: City name (required) (e.g., `q=London`)
  - `appid`: Your API key (required)
  - `units`: Units of measurement. Standard (`Kelvin`), metric (`Celsius`), and imperial (`Fahrenheit`) are available. Default: `standard`.

- **Example Request**:
```bash
curl -X GET "https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY&units=metric"
```

- **Example Response**:
```json
{
  "coord": {
    "lon": -0.1257,
    "lat": 51.5085
  },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 15.0,
    "feels_like": 14.6,
    "temp_min": 14.0,
    "temp_max": 16.0,
    "pressure": 1015,
    "humidity": 67
  },
  "wind": {
    "speed": 3.6,
    "deg": 300
  },
  "sys": {
    "country": "GB",
    "sunrise": 1634033400,
    "sunset": 1634071260
  },
  "name": "London"
}

```

### 2. **5-Day Weather Forecast**

- **Endpoint**: `/forecast`
- **Description**: Retrieves weather forecast data for a specific city.
- **Parameters**:
  - `q`: City name (required) (e.g., `q=London`)
  - `appid`: Your API key (required)
  - `units`: Units of measurement. Standard (`Kelvin`), metric (`Celsius`), and imperial (`Fahrenheit`) are available. Default: `standard`.

- **Example Request**:
```bash
curl -X GET "https://api.openweathermap.org/data/2.5/forecast?q=London&appid=YOUR_API_KEY&units=metric"
```

- **Example Response**:
```json
{
  "cod": "200",
  "message": 0,
  "cnt": 40,
  "list": [
    {
      "dt": 1634037600,
      "main": {
        "temp": 15.0,
        "feels_like": 14.6,
        "temp_min": 14.0,
        "temp_max": 16.0,
        "pressure": 1015,
        "sea_level": 1015,
        "grnd_level": 1014,
        "humidity": 67,
        "temp_kf": 1.0
      },
      "weather": [
        {
          "id": 800,
          "main": "Clear",
          "description": "clear sky",
          "icon": "01d"
        }
      ],
      "clouds": {
        "all": 0
      },
      "wind": {
        "speed": 3.6,
        "deg": 300
      },
      "visibility": 10000,
      "pop": 0,
      "sys": {
        "pod": "d"
      },
      "dt_txt": "2021-10-12 12:00:00"
    }
  ],
  "city": {
    "id": 2643743,
    "name": "London",
    "coord": {
      "lat": 51.5085,
      "lon": -0.1257
    },
    "country": "GB",
    "population": 1000000,
    "timezone": 3600,
    "sunrise": 1634033400,
    "sunset": 1634071260
  }
}
```

### 3. **Air Pollution Data**

- **Endpoint**: `/air_pollution`
- **Description**: Retrieves air pollution data for a specific city.
- **Parameters**:
  - `lat`: Latitude (required) (e.g., `lat=51.5085`)
  - `lon`: Longitude (required) (e.g., `lon=-0.1257`)
  - `appid`: Your API key (required)

- **Example Request**:
```bash
curl -X GET "https://api.openweathermap.org/data/2.5/air_pollution?lat=51.5085&lon=-0.1257&appid=YOUR_API_KEY"
```

- **Example Response**:
```json
{
  "coord": {
    "lon": -0.1257,
    "lat": 51.5085
  },
  "list": [
    {
      "main": {
        "aqi": 1
      },
      "components": {
        "co": 234.29,
        "no": 0.01,
        "no2": 0.02,
        "o3": 0.03,
        "so2": 0.01,
        "pm2_5": 0.01,
        "pm10": 0.01,
        "nh3": 0.01
      }
    }
  ]
}
```

## Rate Limits
- **Free plan**: 60 requests per minute
- **Paid plans**: Higher rate limits available

## Resources
- [Documentation](https://openweathermap.org/api)
- [API Key Signup](https://home.openweathermap.org/users/sign_up)
- [API Pricing](https://home.openweathermap.org/plans)
- [API Status](https://status.openweathermap.org/)
- [Support](https://home.openweathermap.org/support)
