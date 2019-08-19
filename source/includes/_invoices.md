
# Invoices

A document sent to a customer that includes a list of products sold or tasks provided, with a statement of the sum due.

Using the API allows you to do the following with invoice data.

| Attribute                 | Type     | Description                                                                                                                                                               |
|---------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| balance                   | decimal  | The customer due amount.                                                                                                                                                  |
| customer                  | number   | Unique identifier for a customer.                                                                                                                                         |
| customer_address          | string   | The customer address linked to the invoice.                                                                                                                               |
| customer_city             | string   | The customer city linked to the invoice.                                                                                                                                  |
| customer_email            | string   | The customer email linked to the invoice.                                                                                                                                 |
| customer_legal_notice     | string   | The customer registration number linked to the invoice.                                                                                                                   |
| customer_phone            | string   | The customer phone linked to the invoice.                                                                                                                                 |
| customer_phone_mobile     | string   | The customer mobile phone linked to the invoice.                                                                                                                          |
| customer_postal_zip_code  | string   | The customer zip code linked to the invoice.                                                                                                                              |
| customer_province_state   | string   | The customer state linked to the invoice.                                                                                                                                 |
| description               | string   | Description.                                                                                                                                                              |
| due_date                  | datetime | The customer due date.                                                                                                                                                    |
| estimate                  | number   | Unique identifier for an estimate.                                                                                                                                        |
| id                        | number   | Unique identifier.                                                                                                                                                        |
| invoice_date              | datetime | Date.                                                                                                                                                                     |
| invoice_number            | string   | Document number.                                                                                                                                                          |
| notes                     | string   | Notes visible to the customer.                                                                                                                                            |
| organization              | number   | Unique identifier for an organization.                                                                                                                                    |
| paid_to_date              | decimal  | Amount paid by the customer.                                                                                                                                              |
| purchase_order            | string   | Purchase order.                                                                                                                                                           |
| responsible               | number   | Unique identifier for a member responsible for the invoice.                                                                                                               |
| status                    | number   | Enum for the invoice status : </br>0 = Draft. </br>1 = Sent. </br>2 = Viewed. </br>3 = Partially paid. </br>4 = Paid. </br>5 = Disputed. </br>6 = Void. </br>7 = Deleted. |
| taxes_amount              | decimal  | Amount of taxes to paid.                                                                                                                                                  |
| terms                     | string   | Terms.                                                                                                                                                                    |
| total                     | decimal  | Total amount.                                                                                                                                                             |
| total_amount_before_taxes | decimal  | Total amount before taxes.                                                                                                                                                |
| type                      | invoices | Type of response.                                                                                                                                                         |

<aside class="notice">
	Some attributes are available only if the authenticated user has the required permissions.
</aside> 


## Viewing an invoice

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287
```
> Response

```json
{
 	"invoices": [
		{
			"type":"invoices",
			"id":9287,
			"invoice_number":"0005",
			"customer_name":"Sample client",
			"balance":1225.7900,
			"paid_to_date":100.0000,
			"organization":1686,
			"customer":143222,
			"customer_address":null,
			"customer_city":null,
			"customer_contact":"Sample contact name",
			"customer_country":"Canada",
			"customer_email":"143222@example.com",
			"customer_legal_notice":null,
			"customer_phone":"123-456-7890",
			"customer_phone_mobile":null,
			"customer_postal_zip_code":null,
			"customer_province_state":null,
			"custom_title":null,
			"description":null,
			"due_date":"2018-04-18T00:00:00",
			"estimate":null,
			"invoice_date":"2018-04-18T00:00:00",
			"notes":null,
			"terms":null,
			"purchase_order":null,
			"responsible":9015,
			"status":3,
			"taxes_amount":13.7900,
			"total":1325.7900,
			"total_amount_before_taxes":1312.0000,
			"links":[
				{
				"href":"organizations/1686",
				"rel":"organizations",
				"type":"GET"
				},
				{
				"href":"customers/143222",
				"rel":"customers",
				"type":"GET"
				},
				{
				"href":"invoices/9287",
				"rel":"self",
				"type":"GET"
				}
			]
		}
	]
}
```

This API allows you to view an invoice.

<span class="http-method http-get">GET</span> `/webapi/invoices/[id]`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the invoice. |

<aside class="notice">
	Use 'includes' to embed additional details in the response.
</aside>

## List all invoices

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices
```
>Response

```json
{
  "links": [
    {
      "href": "invoices?limit=1&page=1",
      "rel": "navigation-previous",
      "type": "GET"
    },
    {
      "href": "invoices?limit=1&page=3",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "invoices": [
    {
      "type": "invoices",
      "id": 14654,
      "invoice_number": "0002",
      "customer_name": "Client 1",
      "balance": 51.5,
      "paid_to_date": 0,
      "organization": 9244,
      "customer": 154528,
      "customer_address": null,
      "customer_city": null,
      "customer_contact": null,
      "customer_country": "Canada",
      "customer_email": null,
      "customer_legal_notice": null,
      "customer_phone": null,
      "customer_phone_mobile": null,
      "customer_postal_zip_code": null,
      "customer_province_state": null,
      "custom_title": null,
      "description": null,
      "due_date": "2018-09-20T00:00:00",
      "estimate": null,
      "invoice_date": "2018-09-20T00:00:00",
      "notes": null,
      "terms": null,
      "purchase_order": null,
      "responsible": 29550,
      "status": 0,
      "taxes_amount": 1.5,
      "total": 51.5,
      "total_amount_before_taxes": 50,
      "links": [
        {
          "href": "organizations/9244",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "customers/154528",
          "rel": "customers",
          "type": "GET"
        },
        {
          "href": "invoices/14654",
          "rel": "self",
          "type": "GET"
        }
      ]
    }
  ]
}
```
Using this API, you can fetch a list of invoices.

<span class="http-method http-get">GET</span> `/webapi/invoices/`

<aside class="notice">
	Use 'includes' to embed additional details in the response.
</aside>

## Invoice details

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287/invoice_details
```
>Response

```json
{
	"invoice_details":
	[
		{
			"type":"invoice_details",
			"id":23926,
			"description":"Administration - taxable",
			"quantity":1.0000,
			"price":40.0000,
			"total_price":40.0000,
			"invoice_detail_type":1,
			"project":7224,
			"links":
				[
					{
					"href":"projects/7224",
					"rel":"projects",
					"type":"GET"
					},
					{
					"href":"invoices/9287",
					"rel":"invoices",
					"type":"GET"
					}
				],
			"item":337523,
			"tax":376,
			"invoice":9287
		}
	]
}
```

This endpoint retrieves the invoice details.

<span class="http-method http-get">GET</span> `/webapi/invoices/[id]/invoice_details`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the invoice. |

| Attribute           | Type            | Description                                                    |
|---------------------|-----------------|----------------------------------------------------------------|
| description         | string          | Description.                                                   |
| id                  | number          | Unique identifier for an invoice detail.                       |
| invoice             | number          | Unique identifier for an invoice.                              |
| invoice_detail_type | number          | Enum for invoice detail type: </br>0 = Product. </br>1 = Task. |
| item                | number          | Unique identifier for an item.                                 |
| price               | decimal         | Rate/Unit price.                                               |
| project             | number          | Unique identifier for a project.                               |
| quantity            | decimal         | Units/Quantity                                                 |
| tax                 | number          | Unique identifier for an invoice tax.                          |
| total_price         | decimal         | Total price.                                                   |
| type                | invoice_details | Type of response.                                              |

<aside class="notice">
	Some attributes are available only if the authenticated user has the required permissions.
</aside> 

<aside class="notice">
	The details of an invoice can also be filtered using filtered searches
</aside>

<aside class="notice">
	Use 'includes' to embed additional details in the response.
</aside>

## Invoice taxes

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287/invoice_taxes
```

>Response

```json
{
	"invoice_taxes":
	[
		{
			"type":"invoice_taxes",
			"total":7.8000,
			"code":"HST",
			"compound":false,
			"identification":null,
			"rate":0.130000,
			"sequence_number":1,
			"invoice":9287,
			"links":
				[
					{
					"href":"invoices/9287",
					"rel":"invoices",
					"type":"GET"
					}
				],
			"tax":375
			},
			{
			"type":"invoice_taxes",
			"total":3.9900,
			"code":"QST",
			"compound":false,
			"identification":null,
			"rate":0.099750,
			"sequence_number":1,
			"invoice":9287,
			"links":
				[
					{
					"href":"invoices/9287",
					"rel":"invoices",
					"type":"GET"
					}
				],
			"tax":376},
			{
			"type":"invoice_taxes",
			"total":2.0000,
			"code":"GST",
			"compound":false,
			"identification":null,
			"rate":0.050000,
			"sequence_number":2,
			"invoice":9287,
			"links":
				[
					{
					"href":"invoices/9287",
					"rel":"invoices",
					"type":"GET"
					}
				],
			"tax":376
		}
	]
}
```

This endpoint retrieves the taxes of an invoice.

<span class="http-method http-get">GET</span> `/webapi/invoices/[id]/invoice_taxes`

| Parameter | Description                       |
|-----------|-----------------------------------|
| id        | Unique identifier of the invoice. |

| Attribute       | Type          | Description                           |
|-----------------|---------------|---------------------------------------|
| code            | string        | Tax code.                             |
| compound        | boolean       | True if tax is compound.              |
| identification  | string        | Registration / identifier.            |
| invoice         | number        | Unique identifier for an invoice.     |
| rate            | decimal       | Rate.                                 |
| sequence_number | number        | Sequence order.                       |
| tax             | number        | Unique identifier for an invoice tax. |
| total           | decimal       | Total amount for this tax.            |
| type            | invoice_taxes | Type of response.                     |

<aside class="notice">
	Some attributes are available only if the authenticated user has the required permissions.
</aside> 

<aside class="notice">
	The taxes of an invoice can also be filtered using filtered searches
</aside>

<aside class="notice">
	Use 'includes' to embed additional details in the response.
</aside>

## Includes (Invoices)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287?includes=invoice_details,invoice_taxes
```

The following entity types can be included in this payload type:

| Type            | Description                               |
|-----------------|-------------------------------------------|
| organizations   | The organization containing this invoice  |
| customers       | The customer associated with this invoice |
| members         | The responsible member for this invoice   |
| invoice_details | The invoice's detail rows                 |
| invoice_taxes   | The taxes summary of this invoice         |

## Includes (Invoice details)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287/invoice_details?includes=projects
```

The following entity types can be included in this payload type:

| Type     | Description                                       |
|----------|---------------------------------------------------|
| invoices | The invoice associated with this invoice detail.  |
| items    | The item associated with this invoice detail.     |
| projects | The project associated with this invoice details. |

## Includes (Invoice taxes)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/invoices/9287/invoice_taxes?includes=taxes
```

The following entity types can be included in this payload type:

| Type     | Description                                      |
|----------|--------------------------------------------------|
| invoices | The invoice associated with this invoice detail. |
| taxes    | The tax associated with this invoice detail.     |
