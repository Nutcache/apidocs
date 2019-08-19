# Timers

A Nutcache timer is a stopwatch used to record time spent on a task.

Using the API allows you to do the following with timer data.

| Attribute           | Type     | Description                                                                             |
|---------------------|----------|-----------------------------------------------------------------------------------------|
| email_reminder_sent | boolean  | Set to True if a reminder is sent when a timer runs more than 24 hours.                 |
| id                  | number   | Unique identifier.                                                                      |
| max_end_time_utc    | datetime | End time maximum value (UTC time)                                                       |
| member              | number   | Unique identifier for a member.                                                         |
| minutes             | number   | Minutes.                                                                                |
| project             | number   | Unique identifier for a project.                                                        |
| project_service     | number   | Unique identifier for a project service.                                                |
| status              | number   | Enum for the timer status: </br>0 = Started. </br>1 = Stopped. </br>2 = System stopped. |
| time_start_local    | datetime | Timer start (local time).                                                               |
| time_start_utc      | datetime | Timer start (UTC time).                                                                 |
| type                | timers   | Type of response.                                                                       |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

## Viewing a timer

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/timers/3546
```
>Response

```json
{
  "timers": [
    {
      "type": "timers",
      "id": 3546,
      "member": 9015,
      "time_start_local": "2018-09-07T11:55:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:55:47.377",
      "minutes": 0,
      "status": "1",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3546",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_service": null
    }
  ]
}
```

This API allows you to view the details of a timer.

<span class="http-method http-get">GET</span> `/webapi/timers/[id]`

| Parameter | Description                     |
|-----------|---------------------------------|
| id        | Unique identifier of the timer. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all timers

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/timers
```
>Response

```json
{
  "links": [
    {
      "href": "timers?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "timers": [
    {
      "type": "timers",
      "id": 3546,
      "guid": "{aa8995ef-59e9-4173-ad5c-b923b46e20d7}",
      "member": 9015,
      "time_start_local": "2018-09-07T11:55:00",
      "max_end_time_utc": "2018-09-08T04:00:04",
      "time_start_utc": "2018-09-07T15:55:47.377",
      "minutes": 0,
      "status": "1",
      "email_reminder_sent": false,
      "project": 7224,
      "links": [
        {
          "href": "projects/7224",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "timers/3546",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_service": null
    }
  ]
}
```

Using this API, you can fetch a list of timers.

<span class="http-method http-get">GET</span> `/webapi/timers`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Includes (Timers)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/timers/3546?includes=projects,members
```

The following entity types can be included in this payload type:

| Type             | Description                                       |
|------------------|---------------------------------------------------|
| members          | The member associated with the timer.             |
| projects         | The project associated with the timer.            |
| project_services | The service associated with the timer.            |
| sprint_stories   | The project board card associated with the timer. |