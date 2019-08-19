# Search

## Filtered Searches

Filtered searches can be used to find entities that match specific search criteria.

## Usage

>Filter Construct

```json
{
  "filter_rules": [
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    }
  ]
}
```

<span class="http-method http-post">POST</span> `_entity_/filtered`

>Filters can be combined together as follows:

```json
{
  "filter_rules": [
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    },
    {
      "property": "_name_",
      "operator": "_operator_",
      "value": "_value_"
    }
  ]
}
```

<aside class="notice">
  Filtered requests can combine filter rules with sorting rules by adding both properties to the payload.
</aside>

>Example

```shell
curl -H 'Authorization: bearer {YOUR_TOKEN} 
     -H 'Content-Type:application/json' 
	 -H 'api-version: 3' 
	 -H 'OrganizationGuid: 846E176E-7C4B-4BFD-A894-C98F2988927E' 
	 -X POST https://apps.nutcache.com/webapi/customers/filtered 
	 -d '{"filter_rules": [{"property": "name","operator": "ct","value": "Test"}]}'
```

## Filter Operators

| Operator | Description             |
|----------|-------------------------|
| eq       | Equals.                 |
| neq      | Not Equals.             |
| gt       | Greater Than.           |
| lt       | Less Than.              |
| gte      | Greater Than or Equals. |
| lte      | Less Than or Equals.    |
| ct       | Contains.               |
| sw       | Starts With.            |
| ew       | Ends With.              |

## Sorting

>Sorting Construct

```json
 "sorting_rules": [
    {
      "property": "description",
      "direction": "desc"
    },
    {
      "property": "code",
      "direction": "asc"
    }
  ]
```

Results from filtered searches can be sorted using filtered actions with sorting rules.

<aside class="notice">
  Filtered requests can combine filter rules with sorting rules by adding both properties to the payload.
</aside>

## Sort Directions

| Direction  | Supported Terms   |
|------------|-------------------|
| Ascending  | asc, ascending.   |
| Descending | desc, descending. |