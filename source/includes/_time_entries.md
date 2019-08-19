# Time Entries

A time entry is a recording of the amount of time a member spent on a specific task.

Using the API allows you to do the following with time entry data.

| Attribute            | Type         | Description                                                                                                                                                  |
|----------------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| billable_minutes     | number       | Billable time entry in minutes. </br>Available for projects that are billable (project.billing_method <> 0).                                                 |
| creation_date        | datetime     | Date the time entry was created.                                                                                                                             |
| creation_userprofile | number       | Unique identifier for a member that originally created the time entry.                                                                                       |
| end_time             | datetime     | Date time that represents the end of the time entry. </br>Available if time tracking mode is set to Start/End time (organization.time_tracking_type = 1)).   |
| id                   | number       | Unique identifier.                                                                                                                                           |
| invoice              | number       | Unique identifier for an invoice.                                                                                                                            |
| member               | number       | Unique identifier for a member.                                                                                                                              |
| minutes              | number       | Number of minutes logged.                                                                                                                                    |
| note                 | string       | Notes.                                                                                                                                                       |
| project              | number       | Unique identifier for a project.                                                                                                                             |
| project_service     | number       | Unique identifier for a project service.                                                                                                                     |
| start_time           | datetime     | Date time that represents the start of the time entry. </br>Available if time tracking mode is set to Start/End time (organization.time_tracking_type = 1)). |
| type                 | time_entries | Type of response.                                                                                                                                            |
| working_date         | datetime     | Date time that represents the day of the time entry.                                                                                                         |

<aside class="notice">
  Some attributes are read-only.
</aside> 

<aside class="notice">
  Some attributes are available based on the organization and/or project settings.
</aside> 

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

## Viewing a time entry

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}' 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/time_entries/1
```

>Response

```json
{
  "time_entries": [
    {
      "type": "time_entries",
      "id": 201001,
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:01:09.25",
      "creation_userprofile": 2814,
      "working_date": "2018-03-07T00:00:00",
      "minutes": 480,
      "note": null,
      "project_service": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "project_services/106963",
          "rel": "project_services",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "time_entries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

This API allows you to view the details of a time entry.

<span class="http-method http-get">GET</span> `/webapi/time_entries/[id]`

| Parameter | Description                          |
|-----------|--------------------------------------|
| id        | Unique identifier of the time entry. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all time entries

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/time_entries
```

>Response

```json
{
  "links": [    
    {
      "href": "time_entries?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "time_entries": [
    {
      "type": "time_entries",
      "id": 201001,
      "billable_minutes": 0,
      "creation_date": "2018-03-06T22:01:09.25",
      "creation_userprofile": null,
      "working_date": "2018-03-07T00:00:00",
      "minutes": 480,
      "note": null,
      "project_service": 106963,
      "member": 9015,
      "project": 6641,
      "links": [
        {
          "href": "projects/6641",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "project_services/106963",
          "rel": "projectitems",
          "type": "GET"
        },
        {
          "href": "members/9015",
          "rel": "members",
          "type": "GET"
        },
        {
          "href": "time_entries/201001",
          "rel": "self",
          "type": "GET"
        }
      ],
      "invoice": null
    }
  ]
}
```

Using this API, you can fetch a list of time entries.

<span class="http-method http-get">GET</span> `/webapi/time_entries`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Includes (Time entries)

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/time_entries/1?includes=members,projects,project_services
```

The following entity types can be included in this payload type:

| Type             | Description                                  |
|------------------|----------------------------------------------|
| invoices         | The invoice associated with this time entry. |
| members          | The member associated with this time entry.  |
| organizations    | The organization containing this time entry. |
| projects         | The project associated with this time entry. |
| project_services | The task associated with this time entry.    |

## Creating a time entry

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3'
     -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E'
     -X POST -d {"timeentries": [{"start_time":"2018-09-20T09:00", "end_time":"2018-09-20T21:45","note":"Modified from API 3",project_service":106972,"member":9015,"project":6645,"invoice":""}]} https://apps.nutcache.com/webapi/time_entries
```

This API allows time entries to be created.

<span class="http-method http-get">POST</span> `/webapi/time_entries`

Time entries created (working_date) inside an approved day/week have the option to notify administrators.

<span class="http-method http-get">POST</span> `/webapi/time_entries?notify=true`

<aside class="notice">
  Some attributes are available based on the organization and/or project settings.
</aside> 

<aside class="notice">
  The authenticated user must have the required permissions to create a time entry.
</aside> 

## Updating a time entry

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3'
     -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E'
     -X PUT -d {"timeentries": [{"start_time":"2018-09-20T09:00", "end_time":"2018-09-20T21:45","note":"Modified from API 3",project_service":106972,"member":9015,"project":6645,"invoice":""}]} https://apps.nutcache.com/webapi/time_entries/1
```

This API allows existing time entries to be modified.

<span class="http-method http-get">PUT</span> `/webapi/time_entries/[id]`

| Parameter | Description                          |
|-----------|--------------------------------------|
| id        | Unique identifier of the time entry. |

Time entries updated inside an approved day/week have the option to notify administrators.

<span class="http-method http-get">PUT</span> `/webapi/time_entries/[id]?notify=true`

<aside class="notice">
  Some attributes are available based on the organization and/or project settings.
</aside>

<aside class="notice">
  The authenticated user must have the required permissions to update a time entry.
</aside> 

<aside class="warning">
  Updating a time entry that has already been invoiced is not permitted.
</aside>

## Deleting a time entry

>Example

```shell
curl -H 'Authorization: nut-basic YVl6T1JtbkdpMHhwaXhCdTQ5b3l6ckpqR2ZGY2Z3Z1Eycnh2aGl0ZDphcGlkb2NzQGFwaWRvY3MuY29tOnBhc3N3b3Jk' 
     -H 'api-version: 3'
     -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E'
     -X DELETE https://apps.nutcache.com/webapi/time_entries/1
```

<span class="http-method http-get">DELETE</span> `/webapi/time_entries/[id]`

| Parameter | Description                          |
|-----------|--------------------------------------|
| id        | Unique identifier of the time entry. |

Time entries deleted inside an approved day/week have the option to notify administrators.

<span class="http-method http-get">DELETE</span> `/webapi/time_entries/[id]?notify=true`

<aside class="notice">
  The authenticated user must have the required permissions to delete a time entry.
</aside> 

<aside class="warning">
  Deleting a time entry that has already been invoiced is not permitted.
</aside>