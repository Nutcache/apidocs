# Currencies

Get information about currencies.

Using the API allows you to do the following with currency data.

| Attribute     | Type       | Description                       |
|---------------|------------|-----------------------------------|
| code          | string     | Currency code.                    |
| decimal_count | number     | Number of decimal places.         |
| id            | number     | Unique identifier.                |
| name_dede     | string     | Currency name in German.          |
| name_enus     | string     | Currency name in US english.      |
| name_eses     | string     | Currency name in Spanish.         |
| name_esus     | string     | Currency name in Spanish / US.    |
| name_frca     | string     | Currency name in French / Canada. |
| name_frfr     | string     | Currency name in French / France. |
| name_itit     | string     | Currency name in Italian.         |
| name_plpl     | string     | Currency name in Polish.          |
| name_ptbr     | string     | Currency name in Portuguese.      |
| name_ruru     | string     | Currency name in Russian.         |
| type          | currencies | Type of response.                 |

## Viewing a currency

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/currencies/147
```
>Response

```json
{
  "currencies": [
    {
      "type": "currencies",
      "id": 147,
      "code": "USD",
      "decimal_count": 2,
      "name_enus": "Dollar - United States of America",
      "name_frfr": "Dollar - Etats-Unis d'Amérique",
      "name_frca": "Dollar - Etats-Unis d'Amérique",
      "name_ruru": "Доллар - Соединенные Штаты Америки",
      "name_ptbr": "Dólar - Estados Unidos da América",
      "name_plpl": "dolar amerykański – Stany Zjednoczone",
      "name_itit": "Dollaro - Stati Uniti d'America",
      "name_eses": "Dólar - Estados Unidos",
      "name_esus": "Dólar - Estados Unidos",
      "name_dede": "Dollar - Vereinigten Staaten von Amerika"
    }
  ]
}
```
This API allows you to view the details of a currency.

<span class="http-method http-get">GET</span> `/webapi/currencies/[id]`

| Parameter | Description                        |
|-----------|------------------------------------|
| id        | Unique identifier of the currency. |

## List all currencies

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/currencies?limit=2&page=13
```
>Response

```json
{
  "links": [
    {
      "href": "currencies?limit=2&page=12",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "currencies?limit=2&page=14",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "currencies": [
    {
      "type": "currencies",
      "id": 25,
      "code": "CAD",
      "decimal_count": 2,
      "name_enus": "Dollar - Canada",
      "name_frfr": "Dollar - Canada",
      "name_frca": "Dollar - Canada",
      "name_ruru": "Доллар - Канада",
      "name_ptbr": "Dólar - Canadá",
      "name_plpl": "dolar kanadyjski – Kanada",
      "name_itit": "Dollaro - Canada",
      "name_eses": "Dólar - Canadá",
      "name_esus": "Dólar - Canadá",
      "name_dede": "Kanadischer Dollar – Kanada"
    },
    {
      "type": "currencies",
      "id": 26,
      "code": "CDF",
      "decimal_count": 2,
      "name_enus": "Congolese Franc - Congo/Kinshasa",
      "name_frfr": "Franc congolais - République démocratique du Congo",
      "name_frca": "Franc congolais - République démocratique du Congo",
      "name_ruru": "Конголезский франк - Конго/Киншаса",
      "name_ptbr": "Franco Congolês - Congo/Kinshasa",
      "name_plpl": "frank kongijski – Kongo/Kinszasa",
      "name_itit": "Franco - Congo/Kinshasa",
      "name_eses": "Franco congoleño - Congo/Kinsasa",
      "name_esus": "Franco congoleño - Congo/Kinsasa",
      "name_dede": "Kongo-Franc – Demokratische Republik Kongo"
    }
  ]
}
```
Using this API, you can fetch a list of currencies.

<span class="http-method http-get">GET</span> `/webapi/currencies`