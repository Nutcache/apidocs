# Organizations

A Nutcache organization is an entity comprising multiple members with various roles and projects with varying constraints and goals.

Using the API allows you to do the following with organization data.

| Attribute             | Type          | Description                                                                                                                                                                                                                                                                                                                   |
|-----------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| active_user_count     | number        | Number of active members.                                                                                                                                                                                                                                                                                                     |
| address               | string        | Address.                                                                                                                                                                                                                                                                                                                      |
| city                  | string        | Name of the city.                                                                                                                                                                                                                                                                                                             |
| country               | number        | Unique identifier for a country.                                                                                                                                                                                                                                                                                              |
| currency              | number        | Unique identifier for a currency.                                                                                                                                                                                                                                                                                             |
| date_format           | number        | Enum for date format set for the organization: </br>0 = ISO format (yyyy-MM-dd). </br>1 = US format w/ dash (MM-dd-yyyy). </br>2 = US format w/ slash (MM/dd/yyyy). </br>3 = International format w/ dash(dd-MM-yyyy). </br>4 = International format w/ slash(dd/MM/yyyy). </br>5 = International format w/ dots(dd.MM.yyyy). |
| email                 | string        | Email contact.                                                                                                                                                                                                                                                                                                                |
| guid                  | string        | Alternative unique identifier.                                                                                                                                                                                                                                                                                                |
| id                    | number        | Unique identifier.                                                                                                                                                                                                                                                                                                            |
| is_demo               | boolean       | Indicates if the organization is for demo purposes.                                                                                                                                                                                                                                                                           |
| is_owner              | boolean       | Indicates if the current user is the owner.                                                                                                                                                                                                                                                                                   |
| last_activity_date    | datetime      | Last date/time this organization was accessed.                                                                                                                                                                                                                                                                                |
| logo_url              | string        | URL for organization logo.                                                                                                                                                                                                                                                                                                    |
| name                  | string        | Name of the organization.                                                                                                                                                                                                                                                                                                     |
| notification_count    | number        | Number of notifications.                                                                                                                                                                                                                                                                                                      |
| phone                 | string        | Phone number.                                                                                                                                                                                                                                                                                                                 |
| state                 | state         | Unique identifier for a state.                                                                                                                                                                                                                                                                                                |
| status                | number        | Enum for the status of the organization: </br>0 = Active. </br>1 = Inactive. </br>2 = Expired.                                                                                                                                                                                                                                     |
| time_format           | number        | Enum for time format set for the organization: </br>0 = ISO format (HH:mm). </br>1 = AM/PM format (hh:mm tt).                                                                                                                                                                                                                 |
| time_rounding         | number        | Enum for time rounding set for time entries in the organization: </br>0 = None. </br>1 = Round to nearest. </br>2 = Round up to nearest.                                                                                                                                                                                      |
| time_rounding_minutes | number        | Number, in minutes, set to automatically round time entries, if time rounding is set.                                                                                                                                                                                                                                         |
| time_span_format      | number        | Enum for duration (time) format set for the organization: </br>0 = Decimal (e.g. 2.5). </br>1 = Short time (e.g. 2:30).                                                                                                                                                                                                       |
| time_tracking_type    | number        | Enum for time tracking mode set for the organization: </br>0 = Duration. </br>1 = Start/End time.                                                                                                                                                                                                                             |
| type                  | organizations | Type of response.                                                                                                                                                                                                                                                                                                             |
| website               | string        | Site identifier for the organization.                                                                                                                                                                                                                                                                                         |
| zip_code              | string        | Zip code.                                                                                                                                                                                                                                                                                                                     |                                                                                                                                  
<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside>    

## Viewing an organization

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/organizations/6745

```

>Response

```json

{
  "organizations": [
    {
      "type": "organizations",
      "id": 1660,
      "guid": "7b1fb609-eba9-4b4d-91a8-b136cecaddaf",
      "name": "Green Bay Packers",
      "email": "1660@example.com",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": null,
      "country": 4,
      "state": null,
      "currency": 3,
      "website": null,
      "logo_url": "",
      "last_activity_date": "2018-01-11T18:59:50.07",
      "notification_count": 168,
      "is_owner": true,
      "is_demo": false,
      "date_format": 0,
      "time_format": 0,
      "time_span_format": 1,
      "time_rounding": 0,
      "time_rounding_minutes": 0,
      "time_tracking_type": 0,
      "active_user_count": 1,
      "links": [
        {
          "href": "countries/4",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "currencies/3",
          "rel": "currencies",
          "type": "GET"
        },
        {
          "href": "organizations/1660",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}

```

This API allows you to view the details of an organization.

<span class="http-method http-get">GET</span> ` /webapi/organizations/<id>`

| Parameter | Description                            |
|-----------|----------------------------------------|
| id        | Unique identifier of the organization. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all organizations

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/organizations

```

>Response

```json

{
  "links": [
    {
      "href": "organizations?limit=10&page=1",
      "rel": "navigation-prev",
      "type": "GET"
    },
    {
      "href": "organizations?limit=10&page=3",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "organizations": [
    {
      "type": "organizations",
      "id": 1660,
      "guid": "7b1fb609-eba9-4b4d-91a8-b136cecaddaf",
      "name": "Green Bay Hackers",
      "email": "1660@example.com",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": null,
      "country": 4,
      "state": null,
      "currency": 3,
      "website": null,
      "logo_url": "",
      "last_activity_date": "2018-01-11T18:59:50.07",
      "notification_count": 167,
      "is_owner": true,
      "is_demo": false,
      "date_format": 0,
      "time_format": 0,
      "time_span_format": 1,
      "time_rounding": 0,
      "time_rounding_minutes": 0,
      "time_tracking_type": 0,
      "active_user_count": 1,
      "links": [
        {
          "href": "countries/4",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "currencies/3",
          "rel": "currencies",
          "type": "GET"
        },
        {
          "href": "organizations/1660",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}

```

Using this API, you can fetch a list of organizations.

<span class="http-method http-get">GET</span> `/webapi/organizations`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Includes (Organizations)

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -X GET https://apps.nutcache.com/webapi/organizations/6745?includes=countries,states,currencies

```

The following entity types can be included in this payload type:

| Type       | Description                                     |
|------------|-------------------------------------------------|
| countries  | The country associated with this organization.  |
| states     | The state associated with this organization.    |
| currencies | The currency associated with this organization. |
