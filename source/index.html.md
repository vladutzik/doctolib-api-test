---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

### API design and documentation - Doctolib test task

To simplify the integration process in third party software, we would like to offer our clients and API
which they can expose absences of their staff to our platform. This API should have the following
functionality:

  - Creation of an absence of a dedicated person (e.g. PTO, sickleave,...)
  - Creation of an absence of a group (e.g. team event)
  - Creation of an absence of the whole team (e.g. public holiday)

Please design this API, i.e. write the first draft of the documentation that we would give to our
clients. The audience of the documentation are software engineers that work for our clients on
integrating their system with ours.

# Authorization

> To authorize, use this code:

```ruby
COMING SOON
```
```python
COMING SOON
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer {token}"
```

```javascript
const DoctolibApi = require('doctolib');

const Api = new DoctolibApi('token');
```

> Make sure to replace `{token}` with your API key.

In order server to know who is making the request so that he could decide if you have or you don't have access to certain endpoints, you need to authorize all the Api calls.
You can do that using the API key wich you'll find on our [developer platform](http://example.com/developers) in section [API Settings](http://example.com/developers/api-settings).

If you're making raw requests it's mandatory to add `Authorization` header along with each request as follows: `Authorization: Bearer {token}`, or you can use our SDKs that will make your life easyer. 😏

<aside class="notice">
You must replace <code>{token}</code> with your personal API key.
</aside>

# Person

## Update absence for a dedicated person

```ruby
COMING SOON
```

```python
COMING SOON
```

```shell
curl "http://example.com/api/person/{person_id}/absence"
  -H "Authorization: Bearer {token}"
  -H "Content-Type: application/json"
  -X POST
  --data '{ 
    "starts_at": Timestamp,
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }'
```

```javascript
const DoctolibApi = require('doctolib');

const API = new DoctolibApi('token')

API.Person.createAbsence(person_id, { 
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }).then((response) => {
    // handle success response
  }).catch((error) => {
    // handle error
  });
```

> The above command returns JSON structured like this:

```json
{
  content: {
    success: true,
    absence: {
      person_id: Integer,
      starts_at: Timestamp,
      ends_at: Timestamp,
      reason: String,
    }
  },
  meta: {},
  errors: [{
    person_id: ["Error message 1", "Error message 2"],
  }],
}
```

It's natural that people moght be absent at work either there is a motivated absence or unmotivated absence. Reasons why people might be absent are various but for you it's important to **update the calendar** so that your customers will be aware of the absenve of a certain specialist, and customers who had an appointment will be **notified immideately**.
### This endpoint will create an absence slot for a dedicated person by **{person_id}**.

### HTTP Request

`POST http://example.com/api/person/{person_id}/absence`

### URL Parameters

Parameter | Description
--------- | -----------
person_id | The id of the person who will be added an absence slot.

### Response status codes

Status Code | Meaning
---------- | -------
201 | Created -- Time slot was created.
400 | Bad Request -- Some of your data was corrupted.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Your API key is restricted for this action.
404 | Not Found -- The person with given ID does not exist.

# Group

## Update absence for a group by group_id

```ruby
COMING SOON
```

```python
COMING SOON
```

```shell
curl "http://example.com/api/group/{group_id}/absence"
  -H "Authorization: Bearer {token}"
  -H "Content-Type: application/json"
  -X POST
  --data '{ 
    "starts_at": Timestamp,
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }'
```

```javascript
const DoctolibApi = require('doctolib');

const API = new DoctolibApi('token')

API.Group.createAbsence(group_id, { 
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }).then((response) => {
    // handle success response
  }).catch((error) => {
    // handle error
  });
```

> The above command returns JSON structured like this:

```json
{
  content: {
    success: true,
    absence: {
      group_id: Integer,
      starts_at: Timestamp,
      ends_at: Timestamp,
      reason: String,
    }
  },
  meta: {},
  errors: [{
    group_id: ["Error message 1", "Error message 2"],
  }],
}
```

Sometimes it happens that a certain gropu of people will be absent at work, in oreder to simplify the update procedure, we created this endpoint so that you could update the the status of the entire group with a single API call. 
### This endpoint will create an absence slot for a dedicated group with id **{group_id}**.

### HTTP Request

`POST http://example.com/api/group/{group_id}/absence`

### URL Parameters

Parameter | Description
--------- | -----------
group_id | The id of the group who will be added an absence slot.

### Response status codes

Status Code | Meaning
---------- | -------
201 | Created -- Time slot was created.
400 | Bad Request -- Some of your data was corrupted.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Your API key is restricted for this action.
404 | Not Found -- The group with given ID does not exist.

## Update absence for a custom group

```ruby
COMING SOON
```

```python
COMING SOON
```

```shell
curl "http://example.com/api/group/absence"
  -H "Authorization: Bearer {token}"
  -H "Content-Type: application/json"
  -X POST
  --data '{ 
    "people": [person_id],
    "starts_at": Timestamp,
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }'
```

```javascript
const DoctolibApi = require('doctolib');

const API = new DoctolibApi('token')

API.Group.createBulkAbsence({ 
    "people": [person_id],
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }).then((response) => {
    // handle success response
  }).catch((error) => {
    // handle error
  });
```

> The above command returns JSON structured like this:

```json
{
  content: {
    success: true,
    absence: {
      people: [Integer],
      starts_at: Timestamp,
      ends_at: Timestamp,
      reason: String,
    }
  },
  meta: {},
  errors: [{
    starts_at: ["Error message 1", "Error message 2"],
  }],
}
```

### This endpoint will create an absence slot for a custom group by given ids of peple.

### HTTP Request

`POST http://example.com/api/group/{group_id}/absence`

### URL Parameters

### Response status codes

Status Code | Meaning
---------- | -------
201 | Created -- Time slot was created.
400 | Bad Request -- Some of your data was corrupted.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Your API key is restricted for this action.

# Team

## Update absence for a Team

```ruby
COMING SOON
```

```python
COMING SOON
```

```shell
curl "http://example.com/api/team/{team_id}/absence"
  -H "Authorization: Bearer {token}"
  -H "Content-Type: application/json"
  -X POST
  --data '{ 
    "starts_at": Timestamp,
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }'
```

```javascript
const DoctolibApi = require('doctolib');

const API = new DoctolibApi('token')

API.Team.createAbsence(team_id, { 
    "starts_at": Timestamp,
    "ends_at": Timestamp,
    "reason": string
  }).then((response) => {
    // handle success response
  }).catch((error) => {
    // handle error
  });
```

> The above command returns JSON structured like this:

```json
{
  content: {
    success: true,
    absence: {
      team_id: Integer,
      starts_at: Timestamp,
      ends_at: Timestamp,
      reason: String,
    }
  },
  meta: {},
  errors: [{
    team_id: ["Error message 1", "Error message 2"],
  }],
}
```
If there is a public holiday or a force majore situation and your institution is not working for a period of time, you also should block the appointments and notify users who already has appointmtents for that period of time. That's why you need to update system telling us that you will not be available.
### This endpoint will create an absence slot for a dedicated team with id **{team_id}**.

### HTTP Request

`POST http://example.com/api/team/{team_id}/absence`

### URL Parameters

Parameter | Description
--------- | -----------
team_id | The id of the team who will be added an absence slot.

### Response status codes

Status Code | Meaning
---------- | -------
201 | Created -- Time slot was created.
400 | Bad Request -- Some of your data was corrupted.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Your API key is restricted for this action.
404 | Not Found -- The team with given ID does not exist.
