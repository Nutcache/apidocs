# Projects

A project is a planned work or activity that is to be completed over a period of time using the Scrum or any other Agile methodology.

Using the API allows you to do the following with project data.

| Attribute                          | Type     | Description                                                                                                                                                                                                                                                                                                                                          |
|------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| billing_approved_entries_only      | boolean  | Only consider approved timesheet entries for project billing. </br>Available if billing_method <> 0.                                                                                                                                                                                                                                                 |
| billing_invoice_method_fixed_fee   | decimal  | Fixed fee for the project. </br>Available if billing_method = 4.                                                                                                                                                                                                                                                                                     |
| billing_invoice_method_hourly_rate | decimal  | Fixed hourly rate for the project.  </br>Available if billing_method = 3.                                                                                                                                                                                                                                                                            |
| billing_method                     | number   | Enum for billing method set for the project : </br>0 = No invoice will be created for this project. </br>1 = Billable amount is calculated from the services' rate. </br>2 = Billable amount is calculated from the members' rate. </br>3 = Billable amount is a fixed-fee. </br>4 = Billable amount is calculated from a project fixed hourly rate. |
| budget_approved_only               | boolean  | Only consider approved timesheet entries when calculating project budget.                                                                                                                                                                                                                                                                            |
| budget_restrictive                 | boolean  | Budgets cannot be exceeded for the project, allowing for a better control of worked hours and expenses.                                                                                                                                                                                                                                              |
| budget_scope                       | number   | Enum for budget scope set for the project: </br>0 - Global. </br>1 = Per member [Enterprise only]. </br>2 = Per service [Enterprise only].                                                                                                                                                                                                           |
| budget_type                        | number   | Enum for budget type set for the project: </br>0 = Worked hours. </br>1 = Billable hours. </br>2 = Costs. </br>3 = Billable amounts.                                                                                                                                                                                                                 |
| customer                           | number   | Unique identifier for a customer.                                                                                                                                                                                                                                                                                                                    |
| description                        | string   | Description for the project.                                                                                                                                                                                                                                                                                                                         |
| display_color                      | string   | HTML color code to identify the project.                                                                                                                                                                                                                                                                                                             |
| EffectiveBudgetAmount              | decimal  | Budget amount of the projet depending on its budget type (budget_type).                                                                                                                                                                                                                                                                              |
| EffectiveBudgetMinutes             | number   | Budget minutes  of the projet depending on its budget type (budget_type).                                                                                                                                                                                                                                                                            |
| end_date                           | datetime | End date set for the project.                                                                                                                                                                                                                                                                                                                        |
| id                                 | number   | Unique identifier.                                                                                                                                                                                                                                                                                                                                   |
| name                               | string   | Unique name for the project.                                                                                                                                                                                                                                                                                                                         |
| organization                       | number   | Unique identifier for an organization.                                                                                                                                                                                                                                                                                                               |
| primary_contact_email              | string   | Primary contact email.                                                                                                                                                                                                                                                                                                                               |
| primary_contact_name               | string   | Primary contact name.                                                                                                                                                                                                                                                                                                                                |
| primary_contact_phone              | string   | Primary contact phone.                                                                                                                                                                                                                                                                                                                               |
| project_type                       | number   | Enum for the type of project: </br>0 = Agile. </br>1 = Scrum.                                                                                                                                                                                                                                                                                        |
| secondary_contact_email            | string   | Secondary contact email.                                                                                                                                                                                                                                                                                                                             |
| secondary_contact_name             | string   | Secondary contact name.                                                                                                                                                                                                                                                                                                                              |
| secondary_contact_phone            | string   | Secondary contact phone.                                                                                                                                                                                                                                                                                                                             |
| start_date                         | datetime | Start date set for the project.                                                                                                                                                                                                                                                                                                                      |
| status                             | number   | Enum for the status of the project: </br>0 = Planned. </br>1 = In progress. </br>2 = Completed. </br>3 = Canceled. </br>4 = Archived.                                                                                                                                                                                                                |
| type                               | projects | Type of response.                                                                                                                                                                                                                                                                                                                                    |
| vision                             | string   | Project vision.                                                                                                                                                                                                                                                                                                                                      |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

## Viewing a project

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects/6640
```

> Response

```json
{
  "projects": [
    {
      "type": "projects",
      "id": 6640,
      "Organization": 1686,
      "code": "Agile sample project (non-billable)",
      "display_color": "#607d8b",
      "status": 1,
      "links": [
        {
          "href": "organizations/1686",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "customers/143222",
          "rel": "customers",
          "type": "GET"
        },
        {
          "href": "projects/6640",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_type": 0,
      "description": "Leverage the Agile approach to organize and manage your projects with boards.",
      "Vision": "Project vision",
      "primary_contact_email": null,
      "primary_contact_name": null,
      "primary_contact_phone": null,
      "secondary_contact_email": null,
      "secondary_contact_name": null,
      "secondary_contact_phone": null,
      "start_date": "2018-01-22T00:00:00",
      "end_date": null,
      "budget_scope": "1",
      "budget_type": "1",
      "EffectiveBudgetAmount": 0,
      "EffectiveBudgetMinutes": 0,
      "budget_approved_only": false,
      "budget_restrictive": false,
      "billing_method": "NotBillable",
      "billing_invoice_method_fixed_fee": 0,
      "billing_invoice_method_hourly_rate": 0,
      "billing_approved_entries_only": false,
      "customer": 143222,
      "project_budget": null
    }
  ]
}
```

This API allows you to view the details of a project.

<span class="http-method http-get">GET</span> `/webapi/projects/[id]`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the project. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all projects

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3'
     -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E'
     -X GET https://apps.nutcache.com/webapi/projects
```

>Response

```json
{
  "links": [    
    {
      "href": "projects?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "projects": [
    {
      "type": "projects",
      "id": 6640,
      "Organization": 1686,
      "code": "Agile sample project (non-billable)",
      "display_color": "#607d8b",
      "status": 1,
      "links": [
        {
          "href": "organizations/1686",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "customers/143222",
          "rel": "customers",
          "type": "GET"
        },
        {
          "href": "projects/6640",
          "rel": "self",
          "type": "GET"
        }
      ],
      "project_type": 0,
      "description": "Leverage the Agile approach to organize and manage your projects with boards.",
      "Vision": "Project vision",
      "primary_contact_email": null,
      "primary_contact_name": null,
      "primary_contact_phone": null,
      "secondary_contact_email": null,
      "secondary_contact_name": null,
      "secondary_contact_phone": null,
      "start_date": "2018-01-22T00:00:00",
      "end_date": null,
      "budget_scope": "1",
      "budget_type": "1",
      "EffectiveBudgetAmount": 0,
      "EffectiveBudgetMinutes": 0,
      "budget_approved_only": false,
      "budget_restrictive": false,
      "billing_method": "NotBillable",
      "billing_invoice_method_fixed_fee": 0,
      "billing_invoice_method_hourly_rate": 0,
      "billing_approved_entries_only": false,
      "customer": 143222,
      "project_budget": null
    }
  ]
}
```

<span class="http-method http-get">GET</span> `/webapi/projects`

Using this API, you can fetch a list of projects.

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Project members

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3'
     -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E'
     -X GET https://apps.nutcache.com/webapi/projects/6640/project_members
```
> Response

```json
{
  "project_members": [
    {
      "type": "project_members",
      "id": 73582,
      "name": "John Smith",
      "email": "john.smith@example.com",
      "display_color": "#ef6c00",
      "status": 1,
      "project": 6640,
      "links": [
        {
          "href": "projects/6640",
          "rel": "projects",
          "type": "GET"
        }
      ],
      "billing_rate": null,
      "budget_amount": 0,
      "budget_minutes": 0,      
      "member": 29550
    }
  ]
}
```

This endpoint retrieves the project members for a project.

<span class="http-method http-get">GET</span> `/webapi/projects/[id]/project_members`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the project. |

| Attribute      | Type            | Description                                                                                                                                            |
|----------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| billing_rate   | decimal         | Billing rate for the project member. </br>The billing rate is available only if the project invoice method is set to member rate (billing_method = 2). |
| budget_amount  | decimal         | Budget amount set for the member depending on the project budget type (budget_type)                                                                    |
| budget_minutes | number          | Budget minutes set for the member depending on the project budget type (budget_type)                                                                   |
| display_color  | string          | HTML color code to identify the member.                                                                                                                |
| email          | string          | Member email.                                                                                                                                          |
| id             | number          | Unique identifier for a project member.                                                                                                                |
| member         | number          | Unique identifier for the member of the organization.                                                                                                  |
| name           | string          | Member name.                                                                                                                                           |
| project        | number          | Unique identifier for the project.                                                                                                                     |
| status         | number          | Enum for the status of the member in the project: </br>0 = Inactive. </br>1 = Active.                                                                  |
| type           | project_members | Type of response.                                                                                                                                      |


<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

<aside class="notice">
  The project members for a project can also be filtered using filtered searches.
</aside>

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>


## Project services

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects/6640/project_services
```

> Response

```json
{
  "project_services": [
    {
      "type": "project_services",
      "id": 130317,
      "description": "A service",
      "order": 0,
      "status": 0,
      "project": 6640,
      "links": [
        {
          "href": "projects/6640",
          "rel": "projects",
          "type": "GET"
        }
      ],
      "notes": "123",
      "billing_rate": 10,
      "budget_amount": 0,
      "budget_minutes": 0,
      "item": null
    }
  ]
}
```

This endpoint retrieves the project services for a project.

<span class="http-method http-get">GET</span> `/webapi/projects/[id]/project_services`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the project. |

| Attribute      | Type             | Description                                                                                                                                                     |
|----------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| billing_rate   | decimal          | Billing rate for the service in the project. </br>The billing rate is available only if the project invoice method is set to service rate (billing_method = 2). |
| budget_amount  | decimal          | Budget amount set for the service in the project depending on the budget type of the project (budget_type).                                                     |
| budget_minutes | number           | Budget minutes set for the service in the project depending on the budget type of the project (budget_type).                                                    |
| description    | string           | Description for the service in the project.                                                                                                                     |
| id             | number           | Unique identifier for a service in the project.                                                                                                                 |
| item           | number           | Unique identifier for the item.                                                                                                                                 |
| notes          | string           | Additional notes for the service in the project.                                                                                                                |
| order          | number           | Display order of the project service in the project.                                                                                                            |
| project        | number           | Unique identifier for the project.                                                                                                                              |
| status         | number           | Enum for the status of the service in the project: </br>0 = Active. </br>1 = Inactive.                                                                          |
| type           | project_services | Type of response.                                                                                                                                               |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

<aside class="notice">
  The project services for a project can also be filtered using filtered searches.
</aside>

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>


## Includes (Projects)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects/6640?includes=customers
```

The following entity types can be included in this payload type:

| Type             | Description                                |
|------------------|--------------------------------------------|
| organizations    | The organization containing this project.  |
| customers        | The customer associated with this project. |
| project_services | The services associated with this project. |
| project_members  | The members assigned to this project.      |

## Includes (Project members)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects/6640/project_members?includes=members
```

The following entity types can be included in this payload type:

| Type     | Description                                      |
|----------|--------------------------------------------------|
| members  | The member associated with this project member.  |
| projects | The project associated with this project member. |

## Includes (Project services)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects/6640/project_services?includes=items
```

The following entity types can be included in this payload type:

| Type     | Description                                       |
|----------|---------------------------------------------------|
| items    | The item associated with this project service.    |
| projects | The project associated with this project service. |
