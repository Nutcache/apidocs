# Getting started

Welcome to The Nutcache API! Use this API to easily interact with your Nutcache account programmatically. This guide offers a comprehensive suite of developer resources and web services to connect Nutcache to your existing tools and workflow.

## Public key

To use the Nutcache API, an owner must first generate a public key. This action can be done directly in Nutcache under the "My account -> Profile" menu. From the "Profile" dialog, select the "MANAGE API KEYS" tab and click the "+ API Key" to continue.

![Manage API Keys](/images/manageapikeys.png)

## Authentication

>Example

```shell
curl -H 'Content-Type: application/x-www-form-urlencoded'
	 -d "grant_type=password&username={YOUR_USERNAME}&password={YOUR_PASSWORD}&api_key={YOUR_API_KEY}"
	 -X POST https://apps.nutcache.com/webapi/token
```

> Response

```json
 {
 "access_token":"{YOUR_TOKEN}",
 "token_type":"bearer",
 "expires_in":1209599
 }

```

Before you start using the API you must generate a Token by using this endpoint.

<span class="http-method http-get">POST</span> `/webapi/token`

<aside class="notice">
  The token is valide 15 days
</aside> 

The token must be provided along with your request within the Authorization header.

Authorization: bearer {YOUR_TOKEN}

## Organization context

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
	 -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E"
	 -X GET https://apps.nutcache.com/webapi/customers
```

An organization context is required when making requests. To do this, simply include the organization GUID, which can be retrieved via the Organization API from the request header.

## Schema

Blank Fields: </br>
Blank fields are made null instead of being omitted.

Timestamps: </br>
All timestamps are returned in the UTC format, YYYY-MM-DDTHH:MM:SSZ. For example, 2016-02-13T23:27:49Z </br>
</br>
Date Fields: </br>
Input for date fields is expected to be in one of the following formats: </br>
YYYY-MM-DD  </br>
YYYY-MM-DDTHH:MM  </br>
YYYY-MM-DDTHH:MMZ  </br>
YYYY-MM-DDTHH:MM:SS  </br>
YYYY-MM-DDTHH:MM:SSZ  </br>
YYYY-MM-DDTHH:MM:SS±hh:mm  </br>
YYYY-MM-DDTHH:MM:SS±hh  </br>
YYYY-MM-DDTHH:MM:SS±hhmm  </br>
If the time zone information is not present, it will be assumed to be in UTC. </br>
A few valid date fields - 2016-02-15T21:16:25Z , 2012-12-24T12:56:15+05:30, 2010-03-23T12:00

## Embedding

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
	 -H 'api-version: 3' 
	 -H 'CompanyGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X GET https://apps.nutcache.com/webapi/projects?include=organizations
```

You can request for additional entities using the "include" keyword up to one level. For example, you can embed an organization entity when requesting a list of projects.

<aside class="notice">
	Refer to each resource for more information on which entities can be included.
</aside>

## Pagination

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN}  
	 -H "api-version: 3" 
	 -H "OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E" 
	 -X GET "https://apps.nutcache.com/webapi/customers?limit=10&page=2
```

API responses that return a list of objects, such as Projects, Customers or Time Entries are paginated. To scroll through the pages, add the parameter page to the query string. The page number starts with 1. By default, the number of objects returned per page is 10 and is limited to 100.

## Rate Limit

A rate limit of 20 000 API calls per API key is allowed.</br>
If you go over this limit, Nutcache will start returning a HTTP 429 Too Many Requests error, and a Retry-After HTTP header containing the number of seconds until you can retry.

`HTTP/1.1 429 Too Many Requests`
`Retry-After: 30`

<aside class="warning">
	There is also a burst limit of 5 API calls per second and 200 per minute.
</aside>
