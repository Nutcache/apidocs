# Expenses

Describes the expenses incurred in connection with a company's operations, including the expense amount, taxes, suppliers and other people associated with the expense.

Using the API allows you to do the following with with expense data.

| Attribute           | Type     | Description                                                                                             |
|---------------------|----------|---------------------------------------------------------------------------------------------------------|
| amount_after_taxes  | decimal  | The total amount to pay, including the taxes.                                                           |
| amount_before_taxes | decimal  | The subtotal amount, without the taxes.                                                                 |
| amount_due          | decimal  | The outstanding amount.                                                                                 |
| amount_paid         | decimal  | The amount already paid.                                                                                |
| billable            | boolean  | Expense is billable.                                                                                    |
| description         | string   | Description.                                                                                            |
| due_date            | date     | The expense due date.                                                                                   |
| expense_date        | date     | The expense date.                                                                                       |
| expense_number      | string   | Unique number for the expense.                                                                          |
| id                  | number   | Unique identifier.                                                                                      |
| invoice             | number   | Unique identifier of an invoice                                                                         |
| member              | number   | Unique identifier of a member.                                                                          |
| organization        | number   | Unique identifier for an organization.                                                                  |
| project             | number   | Unique identifier of a project.                                                                         |
| status              | number   | Enum for the expense status: </br>0 = To pay. </br>1 = Partially paid. </br>2 = Paid. </br>3 = Deleted. |
| taxes_amount        | decimal  | Amount of taxes to paid.                                                                                |
| type                | expenses | Type of response.                                                                                       |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

## Viewing an expense

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/234359

```
>Response

```json

{
  "expenses": [
    {
      "type": "expenses",
      "id": 234359,
      "expense_number": "0010",
      "expense_date": "2018-10-03T00:00:00",
      "organization": 9244,
      "links": [
        {
          "href": "organizations/9244",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "projects/20196",
          "rel": "projects",
          "type": "GET"
        },
        {
          "href": "expenses/234359",
          "rel": "self",
          "type": "GET"
        }
      ],
      "billable": false,
      "description": null,
      "due_date": "2018-10-31T00:00:00",
      "status": 0,
      "amount_after_taxes": 105,
      "amount_before_taxes": 100,
      "amount_due": 105,
      "amount_paid": 0,
      "taxes_amount": 5,
      "project": 20196,
      "member": 29550,
      "invoice": null
    }
  ]
}


```

This API allows you to view the details of a expense.

<span class="http-method http-get">GET</span> ` /webapi/expenses/[id]`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the expense. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all expenses

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/

```

>Response

```json

{
  "links": [
    {
      "href": "expenses?limit=2&page=2",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "expenses?limit=2&page=4",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "expenses": [
    {
      "type": "expenses",
      "id": 234354,
      "expense_number": "0005",
      "expense_date": "2018-10-03T00:00:00",
      "organization": 9244,
      "links": [
        {
          "href": "organizations/9244",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "expenses/234354",
          "rel": "self",
          "type": "GET"
        }
      ],
      "billable": false,
      "description": null,
      "due_date": "2018-10-03T00:00:00",
      "status": 0,
      "amount_after_taxes": 8,
      "amount_before_taxes": 8,
      "amount_due": 8,
      "amount_paid": 0,
      "taxes_amount": 0,
      "project": null,
      "member": 29550,
      "invoice": null
    }
  ]
}


```

Using this API, you can fetch a list of expenses.

<span class="http-method http-get">GET</span> ` /webapi/expenses/`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Expense taxes

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/234300/expense_taxes

```

>Response

```json

{
  "expense_taxes": [
    {
      "type": "expense_taxes",
      "expense": 234359,
      "id": 229029,
      "tax_amount": 5,
      "tax_code": "A tax",
      "links": [
        {
          "href": "expenses/234359",
          "rel": "expenses",
          "type": "GET"
        }
      ]
    }
  ]
}


```

If you want to get a detailed list of taxes for an expense:

<span class="http-method http-get">GET</span> ` /webapi/expenses/[id]/expense_taxes`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the expense. |

| Attribute  | Type          | Description                       |
|------------|---------------|-----------------------------------|
| expense    | number        | Unique identifier of the expense. |
| id         | number        | Unique identifier.                |
| tax_amount | decimal       | The amount to be paid.            |
| tax_code   | string        | The name or code.                 |
| type       | expense_taxes | Type of response.                |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

<aside class="notice">
  The taxes for an expense can also be filtered using filtered searches.
</aside>

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Includes (Expenses)

>Example

```shell

curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/expenses/234359?includes=customers

```

The following entity types can be included in this payload type:

| Type          | Description                                |
|---------------|--------------------------------------------|
| organizations | The organization containing this expense.  |
| customers     | The customer associated with this expense. |
| invoices      | The invoice associated with this expense.  |
| expense_taxes | The taxes associated to this expense.      |
