# Groups

## Get All Groups

```shell
curl -v -u token:secret  "https://api.textinchurch.com/groups"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "My Super Group",
    "comments": "This is a longer description of the group's purpose.",
  },
  {
    "id": 2,
    "name": "Another Awesome Group",
    "comments": "Just more details about how great this group is.",
  }
]
```

This endpoint retrieves all groups.

### HTTP Request

`GET https://api.textinchurch.com/groups`

### Query Parameters

Parameter | Value | Description
--------- | ------- | -----------
where[group_name] | string | query on a specific group name
per_page | 25 | how many records to return per page (min=1, max=100, default=25)
offset | 0 | get results from given start
order | group_name | prefix with a hyphen (-group_name) to reverse the order
order | updated_at | prefix with a hyphen (-updated_at) to reverse the order

## Get a Specific Group

```shell
curl -v -u token:secret  "https://api.textinchurch.com/groups/2"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Another Awesome Group",
  "comments": "Just more details about how great this group is.",
}
```

This endpoint retrieves a specific group.

### HTTP Request

`GET https://api.textinchurch.com/groups/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the group to retrieve

## Create a New Group

```shell
curl -v -u token:secret -X POST -d
'{"data":{"data":{...}}}' "https://api.textinchurch.com/groups"
```

This endpoint creates a new group.

### HTTP Request

`POST https://api.textinchurch.com/groups`

### URL Parameters

Parameter | Type
--------- | -----------
name | string
comments | string
