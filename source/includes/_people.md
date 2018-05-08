# People

## Get All People

```shell
curl -v -u token:secret "https://api.textinchurch.com/people"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "first_name": "Marianne",
    "last_name": "Bagley",
    "email":"MarianneBBagley@rhyta.com",
    "phone":"620-225-4989",
    "address_1":"1866 Roosevelt Road",
    "address_2":"",
    "city":"Dodge City",
    "state":"KS",
    "zip":"67801"
  },
  {
    "id": 2,
    "first_name": "Alfonso",
    "last_name": "Larry",
    "email":"AlfonsoLLarry@jourrapide.com",
    "phone":"805-764-0954",
    "address_1":"4316 Par Drive",
    "address_2":"",
    "city":"Pomona",
    "state":"CA",
    "zip":"91766"
  }
]
```

This endpoint retrieves all people.

### HTTP Request

`GET https://api.textinchurch.com/people`

### Query Parameters

Parameter | Value | Description
--------- | ------- | -----------
where[first_name] | string | query on a specific first name
where[last_name] | string | query on a specific last name
where[email] | string | query on a specific email
where[phone] | string | query on a specific mobile phone number
per_page | 25 | how many records to return per page (min=1, max=100, default=25)
offset | 0 | get results from given start
order | first_name | prefix with a hyphen (-first_name) to reverse the order
order | last_name | prefix with a hyphen (-last_name) to reverse the order
order | created_at | prefix with a hyphen (-created_at) to reverse the order

## Get a Specific Person

```shell
curl -v -u token:secret "https://api.textinchurch.com/people/2"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "first_name": "Alfonso",
  "last_name": "Larry",
  "email":"AlfonsoLLarry@jourrapide.com",
  "phone":"805-764-0954",
  "address_1":"4316 Par Drive",
  "address_2":"",
  "city":"Pomona",
  "state":"CA",
  "zip":"91766"
}
```

This endpoint retrieves a specific person.

### HTTP Request

`GET https://api.textinchurch.com/people/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the person to retrieve


## Create a New Person

```shell
curl -v -u token:secret -X POST -d
'{"data":{"data":{...}}}' "https://api.textinchurch.com/people"
```

This endpoint creates a new person.

### HTTP Request

`POST https://api.textinchurch.com/people`

### URL Parameters

Parameter | Type | Notes
--------- | ----------- | -----------
first_name | string |
last_name | string |
email | string |
phone | string |
address | string |
address_2 | string |
city | string |
state | string | 2 character abbreviation
zip | string |
