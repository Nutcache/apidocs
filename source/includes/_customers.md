# Customers

An individual or party with whom you conduct business.

Using the API allows you to do the following with customer data.

| Attribute                  | Type      | Description                                                              |
|----------------------------|-----------|--------------------------------------------------------------------------|
| address                    | string    | Address.                                                                 |
| city                       | string    | Name of the city.                                                        |
| communication_culture_code | string    | Communication culture code. </br>Format: [language]-[country code].      |
| organization               | number    | Unique identifier for an organization.                                   |
| contact                    | string    | Contact name.                                                            |
| country                    | number    | Unique identifier for a country.                                         |
| currency                   | number    | Unique identifier for a currency.                                        |
| email                      | string    | Email address.                                                           |
| id                         | number    | Unique identifier.                                                       |
| legal_notice               | string    | Registration number for the customer.                                    |
| mobile_phone               | string    | Mobile phone number.                                                     |
| name                       | string    | Name of the customer.                                                    |
| phone                      | string    | Phone number.                                                            |
| state                      | number    | Unique identifier for a state.                                           |
| status                     | number    | Enum for the status of the customer: </br>0 = Active. </br>1 = Inactive. |
| tax                        | number    | Unique identifier for a tax.                                             |
| type                       | customers | Type of response.                                                        |
| zip_code                   | string    | Zip code.                                                                |

<aside class="notice">
  Some attributes are available only if the authenticated user has the required permissions.
</aside> 

## Viewing a customer

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/customers/154528
```
>Response

```json
{
  "customers": [
    {
      "type": "customers",
      "id": 154528,
      "organization": 9244,
      "name": "Client #1",
      "status": 0,
      "links": [
        {
          "href": "organizations/9244",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "countries/231",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "states/2",
          "rel": "states",
          "type": "GET"
        },
        {
          "href": "customers/154528",
          "rel": "self",
          "type": "GET"
        }
      ],
      "email": "xhbdv260psct@claimab.com",
      "contact": "Daron D Barrett",
      "address": "4992  Worley Avenue",
      "city": "Richmond",
      "zip_code": "23223",
      "phone": "434-378-0004",
      "mobile_phone": "703-725-9475",
      "country": 231,
      "state": 2,
      "legal_notice": "987654321",
      "communication_culture_code": "en-US",
      "tax": 11591,
      "currency": 147
    }
  ]
}
```
This API allows you to view the details of a customer.

<span class="http-method http-get">GET</span> `/webapi/customers/[id]`

| Parameter | Description                        |
|-----------|------------------------------------|
| id        | Unique identifier of the customer. |

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## List all customers

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/customers
```

>Response

```json
{
  "links": [
    {
      "href": "customers?limit=10&page=2",
      "rel": "navigation-next",
      "type": "GET"
    }
  ],
  "customers": [
    {
      "type": "customers",
      "id": 143222,
      "organization": 1686,
      "name": "Sample client",
      "status": 0,
      "links": [
        {
          "href": "organizations/1686",
          "rel": "organizations",
          "type": "GET"
        },
        {
          "href": "countries/40",
          "rel": "countries",
          "type": "GET"
        },
        {
          "href": "customers/143222",
          "rel": "self",
          "type": "GET"
        }
      ],
      "email": "143222@example.com",
      "contact": "Sample contact name",
      "address": null,
      "city": null,
      "zip_code": null,
      "phone": "123-456-7890",
      "mobile_phone": null,
      "country": 40,
      "state": null,
      "legal_notice": null,
      "communication_culture_code": null,
      "tax": null,
      "currency": null
    }
}
```
Using this API, you can fetch a list of customers.

<span class="http-method http-get">GET</span> `/webapi/customers`

<aside class="notice">
  Use 'includes' to embed additional details in the response.
</aside>

## Includes (Customers)

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
     -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET https://apps.nutcache.com/webapi/customers/154528?includes=countries,states
```

The following entity types can be included in this payload type:

| Type          | Description                                 |
|---------------|---------------------------------------------|
| organizations | The organization containing the customer.   |
| countries     | The country associated with this customer.  |
| currencies    | The currency associated with this customer. |
| states        | The state associated with this customer.    |
| taxes         | The tax associated with this customer.      |
