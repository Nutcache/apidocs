# Countries

Get information about countries.

Using the API allows you to do the following with a country data.

| Attribute   | Type      | Description                                                                                                                                                                                                                                                                                                        |
|-------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| code        | string    | Country three letter code.                                                                                                                                                                                                                                                                                         |
| currency    | number    | Unique identifier for a currency.                                                                                                                                                                                                                                                                                  |
| date_format | number    | Enum for date format set for the country: </br>0 = ISO format (yyyy-MM-dd) </br>1 = US format w/ dash (MM-dd-yyyy) </br>2 = US format w/ slash (MM/dd/yyyy) </br>3 = International format w/ dash(dd-MM-yyyy) </br>4 = International format w/ slash(dd/MM/yyyy) </br>5 = International format w/ dots(dd.MM.yyyy) |
| id          | number    | Unique identifier.                                                                                                                                                                                                                                                                                                 |
| name_dede   | string    | Country name in Germain.                                                                                                                                                                                                                                                                                           |
| name_enus   | string    | Country name in US english.                                                                                                                                                                                                                                                                                        |
| name_eses   | string    | Country name in Spanish.                                                                                                                                                                                                                                                                                           |
| name_esus   | string    | Country name in Spanish / US.                                                                                                                                                                                                                                                                                      |
| name_frca   | string    | Country name in French / Canada.                                                                                                                                                                                                                                                                                   |
| name_frfr   | string    | Country name in French / France.                                                                                                                                                                                                                                                                                   |
| name_itit   | string    | Country name in Italian.                                                                                                                                                                                                                                                                                           |
| name_plpl   | string    | Country name in Polish.                                                                                                                                                                                                                                                                                            |
| name_ptbr   | string    | Country name in Portuguese.                                                                                                                                                                                                                                                                                        |
| name_ruru   | string    | Country name in Russian.                                                                                                                                                                                                                                                                                           |
| short_code  | string    | Country two letter code.                                                                                                                                                                                                                                                                                           |
| time_format | number    | Enum for time format set for the organization: </br>0 = ISO format (HH:mm), </br>1 = AM/PM format (hh:mm tt)                                                                                                                                                                                                       |
| type        | countries | Type of response.                                                                                                                                                                                                                                                                                                  |


## Viewing a country

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/countries/231
```

>Response

```json
{
  "countries": [
    {
      "type": "countries",
      "id": 231,
      "code": "USA",
      "short_code": "US",
      "currency": 147,
      "date_format": 1,
      "time_format": 1,
      "name_enus": "United States",
      "name_frfr": "États-Unis",
      "name_frca": "États-Unis",
      "name_ruru": "Соединенные Штаты Америки",
      "name_ptbr": "Estados Unidos",
      "name_plpl": "Stany Zjednoczone",
      "name_itit": "Stati Uniti",
      "name_eses": "Estados Unidos",
      "name_esus": "Estados Unidos",
      "name_dede": "Vereinigte Staaten von Amerika",
      "links": [
        {
          "href": "countries/231",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}
```

This API allows you to view the details of a country.

<span class="http-method http-get">GET</span> `/webapi/countries/[id]`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the country. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all countries

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/countries?limit=2&page=20
```

>Response

```json
{
  "links": [
    {
      "href": "countries?limit=2&page=19",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "countries?limit=2&page=21",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "countries": [
    {
      "type": "countries",
      "id": 39,
      "code": "CMR",
      "short_code": "CM",
      "currency": 154,
      "date_format": 0,
      "time_format": 0,
      "name_enus": "Cameroon",
      "name_frfr": "Cameroun",
      "name_frca": "Cameroun",
      "name_ruru": "Камерун",
      "name_ptbr": "Camarões",
      "name_plpl": "Kamerun",
      "name_itit": "Camerun",
      "name_eses": "Camerún",
      "name_esus": "Camerún",
      "name_dede": "Kamerun",
      "links": [
        {
          "href": "countries/39",
          "rel": "self",
          "type": "GET"
        }
      ]
    },
    {
      "type": "countries",
      "id": 40,
      "code": "CAN",
      "short_code": "CA",
      "currency": 25,
      "date_format": 0,
      "time_format": 0,
      "name_enus": "Canada",
      "name_frfr": "Canada",
      "name_frca": "Canada",
      "name_ruru": "Канада",
      "name_ptbr": "Canadá",
      "name_plpl": "Kanada",
      "name_itit": "Canada",
      "name_eses": "Canadá",
      "name_esus": "Canadá",
      "name_dede": "Kanada",
      "links": [
        {
          "href": "countries/40",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}
```

Using this API, you can fetch a list of countries.

<span class="http-method http-get">GET</span> `/webapi/countries`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Country states

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 	 
	 -X GET https://apps.nutcache.com/webapi/countries/231/states
```

>Response

```json
{
  "links": [
    {
      "href": "countries/231/states?limit=10&page=1",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "countries/231/states?limit=10&page=3",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "states": [
    {
      "type": "states",
      "id": 11,
      "country": 231,
      "code": "US_NJ",
      "name_enus": "New Jersey",
      "name_frfr": "New Jersey",
      "name_frca": "New Jersey",
      "name_ruru": "Нью-Джерси",
      "name_ptbr": "Nova Jérsei",
      "name_plpl": "New Jersey",
      "name_itit": "New Jersey",
      "name_eses": "Nueva Jersey",
      "name_esus": "Nueva Jersey",
      "name_dede": "New Jersey",
      "links": [
        {
          "href": "countries/231",
          "rel": "countries",
          "type": "GET"
        }
      ]
    },
    {
      "type": "states",
      "id": 12,
      "country": 231,
      "code": "US_NY",
      "name_enus": "New York",
      "name_frfr": "New York",
      "name_frca": "New York",
      "name_ruru": "Нью-Йорк",
      "name_ptbr": "Nova York",
      "name_plpl": "Nowy Jork",
      "name_itit": "New York",
      "name_eses": "Nueva York",
      "name_esus": "Nueva York",
      "name_dede": "New York",
      "links": [
        {
          "href": "countries/231",
          "rel": "countries",
          "type": "GET"
        }
      ]
    }
  ]
}
```

This endpoint retrieves the states/provinces of a country.

<span class="http-method http-get">GET</span> `/webapi/countries/[id]/states`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the country. |

<aside class="notice">
  The states of a country can also be filtered using filtered searches.
</aside>

## Includes (Countries)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/countries/231?includes=currencies
```

The following entity types can be included in this payload type:

| Type       | Description                                |
|------------|--------------------------------------------|
| currencies | The currency associated with this country. |
