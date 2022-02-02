---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - ruby
  - javascript

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Purrfect API
---

# Introduction

Welcome to the Purrfect API! You can use our API to access Purrfect API endpoints, which can get information on
pet registrations in our database.

We have language bindings in Ruby and JavaScript! You can view code examples in the dark area to the right, and
you can switch the programming language of the examples with the tabs in the top right.

# Authentication

Purrfect API expects the username and password key to be included in all API requests:

`Username: sdet_challenge`

`Password: wackySumm3r`

<aside class="notice">
All you requests should use the provided basic authorization!
</aside>

# Purrfect API

## Get All Registrations

```ruby
require 'net/http'

Net::HTTP.get(URI('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations'))
```

```javascript
const axios = require('axios');

axios.get('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations')
  .then(response => {
    console.log(response.data);
    console.log(response);
  })
  .catch(error => {
    console.log(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "pet_name": "Fluffums",
    "pet_owner": "Robert",
    "color": "yellow",
    "description": "The fluffiest yellow cat",
    "age": 7
    "species": "cat",
    "vaccination_status": true,
    "services":["bath", "clipping"],
    "created_at": "2022-01-23T15:33:28.340Z",
    "updated_at": "2022-01-23T15:33:28.340Z"
  },
  {
    "id": 2,
    "pet_name": "Pedro The Perro",
    "pet_owner": "Miriam",
    "color": "black",
    "description": "Royally spoiled dog",
    "age": 3
    "species": "dog",
    "vaccination_status": true,
    "services":["massage", "walk"],
    "created_at": "2022-01-23T15:33:28.340Z",
    "updated_at": "2022-01-23T15:33:28.340Z"
  }
]
```

This endpoint retrieves all pet registrations


### HTTP Request

`GET https://sdet-challenge.herokuapp.com/api/v1/pet_registrations`

### Success Code

<aside class="success">
200
</aside>

## Get a Specific Registration

```ruby
require 'net/http'

Net::HTTP.get(URI('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/2'))
```

```javascript
const axios = require('axios');

axios.get('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/2')
  .then(response => {
    console.log(response.data);
    console.log(response);
  })
  .catch(error => {
    console.log(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "pet_name": "Sparky",
  "pet_owner": "Mark",
  "color": "brown",
  "description": "Cute corgy",
  "age": 3,
  "species": "dog",
  "vaccination_status": true,
  "services":["spa", "walk"],
  "created_at": "2022-01-23T15:33:28.340Z",
  "updated_at": "2022-01-23T15:33:28.340Z"
}
```

This endpoint retrieves a specific registration.

### HTTP Request

`GET https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/<ID>
`
### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the registration to retrieve

### Success Code

<aside class="success">
200
</aside>

## Create a Registration

```ruby
require 'net/http'
require 'JSON'

Net::HTTP.post  URI('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations'),
                {
                  "pet_name"=> "Storm",
                  "pet_owner"=> "Mike",
                  "color"=> "black",
                  "description"=> "a scary GSD",
                  "age"=> 4,
                  "species"=> "dog",
                  "vaccination_status"=> true,
                  "membership"=> true,
                  "services"=> ["bath"]
                }.to_json,
                "Content-Type" => "application/json"
````

```javascript
const axios = require('axios');

axios.post('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/api/v1/pet_registrations', {
  "pet_name": "Storm", "pet_owner": "Mike", "color": "brown", "description": "a nice warm cat",
  "age": 2, "species": "dog", "vaccination_status": true, "membership": true, "services": ["vitamins", "bath"]
})
  .then(response => {
    console.log(response.data);
    console.log(response);
  })
  .catch(error => {
    console.log(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "id": 16,
  "pet_name": "willis",
  "pet_owner": "Alex",
  "color": "brown",
  "description": "a nice cuddling cat",
  "age": 2,
  "species": "dog",
  "vaccination_status": true,
  "services": [
    "vitamins",
    "bath"
  ],
  "membership": true,
  "created_at": "2022-01-25T20:11:11.423Z",
  "updated_at": "2022-01-25T20:11:11.423Z"
}
```

This endpoint deletes a specific registration.

### HTTP Request

`POST https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/api/v1/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the registration to delete


### Success Code

<aside class="success">
201
</aside>


## Delete a Specific Registration

```ruby
require 'net/http'

Net::HTTP.new('https://sdet-challenge.herokuapp.com').delete('/api/v1/pet_registrations/4')
```

```javascript
const axios = require('axios');

axios.delete('http://example.com/api/v1/pet_registrations/17')
  .then(response => {
    console.log(response.data);
    console.log(response);
  })
  .catch(error => {
    console.log(error);
  });

```

> The above command returns JSON structured like this:

```json
n/a
```

This endpoint deletes a specific registration.

### HTTP Request

`DELETE https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the registration to delete

### Success Code

<aside class="success">
204
</aside>


## Update a Specific Registration

```ruby
require 'net/http'
require 'JSON'

Net::HTTP.new('https://sdet-challenge.herokuapp.com').put('/api/v1/pet_registrations/5',
                                     {"pet_name"=> "wolfie"}.to_json,
                                     "Content-Type" => "application/json")

````

```javascript
const axios = require('axios');

axios.put('https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/5',{
    "pet_name": "wolfie"
    })
  .then(response => {
    console.log(response.data);
    console.log(response);
  })
  .catch(error => {
    console.log(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "pet_name": "wolfie",
  "pet_owner": "me",
  "color": "yellow",
  "description": "a nice warm cat",
  "age": 2,
  "species": "cat",
  "vaccination_status": true,
  "membership": true,
  "services": [
    "vitamins",
    "bath"
  ],
  "id": 3,
  "created_at": "2022-01-23T15:55:22.933Z",
  "updated_at": "2022-01-26T15:06:28.641Z"
}
```

This endpoint deletes a specific registration.

### HTTP Request

`PUT https://sdet-challenge.herokuapp.com/api/v1/pet_registrations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the registration to delete

### Success Code

<aside class="success">
204
</aside>
