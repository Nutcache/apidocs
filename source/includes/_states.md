# States

Retrieve information about states associated to a country, mostly used for organization and customer payloads.

Using the API allows you to do the following with a state data.

| Attribute | Type   | Description                                                                   |
|-----------|--------|-------------------------------------------------------------------------------|
| code      | string | State code in the following format: <br>[Country 2 letter code]-[State code]. |
| country   | number | Unique identifier for a country.                                              |
| id        | number | Unique identifier.                                                            |
| name_dede | string | State name in Germain.                                                        |
| name_enus | string | State name in US english.                                                     |
| name_eses | string | State name in Spanish.                                                        |
| name_esus | string | State name in Spanish / US.                                                   |
| name_frca | string | State name in French / Canada.                                                |
| name_frfr | string | State name in French / France.                                                |
| name_itit | string | State name in Italian.                                                        |
| name_plpl | string | State name in Polish.                                                         |
| name_ptbr | string | State name in Portuguese.                                                     |
| name_ruru | string | State name in Russian.                                                        |
| type      | states | Type of response.                                                             |

## Viewing a state

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/states/12
```

>Response

```json
{
  "states": [
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

This API allows you to view the details of a state.

<span class="http-method http-get">GET</span> `/webapi/states/[id]`

| Parameter | Description                     |
|-----------|---------------------------------|
| id        | Unique identifier of the state. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all states

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/states?limit=2&page=26
```

>Response

```json
{
  "links": [
    {
      "href": "states?limit=2&page=25",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "states?limit=2&page=27",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "states": [
    {
      "type": "states",
      "id": 51,
      "country": 231,
      "code": "US_SC",
      "name_enus": "South Carolina",
      "name_frfr": "Caroline du Sud",
      "name_frca": "Caroline du Sud",
      "name_ruru": "Южная Каролина",
      "name_ptbr": "Carolina do Sul",
      "name_plpl": "Karolina Południowa",
      "name_itit": "Carolina del Sud",
      "name_eses": "Carolina del Sur",
      "name_esus": "Carolina del Sur",
      "name_dede": "South Carolina",
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
      "id": 52,
      "country": 40,
      "code": "CA_SK",
      "name_enus": "Saskatchewan",
      "name_frfr": "Saskatchewan",
      "name_frca": "Saskatchewan",
      "name_ruru": "Саскачеван",
      "name_ptbr": "Saskatchewan",
      "name_plpl": "Saskatchewan",
      "name_itit": "Saskatchewan",
      "name_eses": "Saskatchewan",
      "name_esus": "Saskatchewan",
      "name_dede": "Saskatchewan",
      "links": [
        {
          "href": "countries/40",
          "rel": "countries",
          "type": "GET"
        }
      ]
    }
  ]
}
```

Using this API, you can fetch a list of states.

<span class="http-method http-get">GET</span> `/webapi/states`

## Includes (States)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/states/12?includes=countries
```

The following entity types can be included in this payload type:

| Type      | Description                            |
|-----------|----------------------------------------|
| countries | The country associated with this state |
