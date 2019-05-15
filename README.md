# This is how the [softhouse.rocks API](http://petstore.swagger.io/?url=http://api.softhouse.rocks/swagger.yaml) works and how you test it.

Tools that we used for testing
* Git BASH
* curl
* jq

## How you test POSTS

### How to test a GET method 
```
curl -X GET "http://api.softhouse.rocks/posts?userId=3" -H "accept: application/json" | jq '.'
```
Expected response:
```
  {
    "_id": "5caaef896b334800cbf66354",
    "userId": 3,
    "id": 25,
    "title": "rem alias distinctio quo quis",
    "body": "ullam consequatur ut\nomnis quis sit vel consequuntur\nipsa eligendi ipsum molestiae et omnis error nostrum\nmolestiae illo tempore quia et distinctio",
    "__v": 0
  },
 ```


**How to get the response code (add ```-I```, remove ```| jq '.'```)**
```
curl -I -X GET "http://api.softhouse.rocks/posts?userId=3" -H "accept: application/json"
```
 Expected response code:
 ```
 HTTP/1.1 200 OK
 ```

### How to test a POST method

```
curl -X POST "http://api.softhouse.rocks/posts" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"string\",\"body\":\"string\",\"userId\":0}"
```

Expected response:
```
{
  "_id":"5cdbcb18f4a0350020b4816b",
   "body":"string",
   "title":"string",
   "userId":0,"id":104,"__v":0
}
```  

### How to test a PUT method
```
curl -X PUT "http://api.softhouse.rocks/posts/1" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hello world\",\"body\":\"Hello Sweden\",\"userId\":56}"
```

Expected response:
```
{
  "_id":"5caaef896b334800cbf6633c",
  "userId":56,
  "id":1,
  "title":"Hello world",
  "body":"Hello Sweden",
  "__v":0}
}
```
 
### How to test a PATCH method
```
curl -X PATCH "http://api.softhouse.rocks/posts/1" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hello, Patch\",\"body\":\"Testing PATCH\",\"userId\":4445}"
```

Expected response:
```
{
  "_id":"5caaef896b334800cbf6633c",
  "userId":4445,
  "id":1,
  "title":"Hello, Patch",
  "body":"Testing PATCH",
  "__v":0
}
```

### How to test a DELETE method
```
curl -X DELETE "http://api.softhouse.rocks/posts/2" -H "accept: application/json"
```

Expected response:
```
none
```

## How you test USERS
### How to test a GET method
```
curl -X GET "http://api.softhouse.rocks/users" -H "accept: application/json" | jq "."
```

Expected response:
```
{
    "address": {
      "geo": {
        "lat": -68.6102,
        "lng": -47.0653
      },
      "street": "Douglas Extension",
      "suite": "Suite 847",
      "city": "McKenziehaven",
      "zipcode": "59590-4157"
    },
    "_id": "5caaef896b334800cbf66334",
    "id": 3,
    "name": "Clementine Bauch",
    "username": "Samantha",
    "email": "Nathan@yesenia.net",
    "__v": 0
  }
```

**How to get the response code (add ```-i```, remove ```| jq '.'```)**

```
curl -i -X GET "http://api.softhouse.rocks/users" -H "accept: application/json"
```

Expected response code:
```
HTTP/1.1 200 OK
```

### How to test a POST method
```
curl -X POST "http://api.softhouse.rocks/users" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"name\":\"hcsahcsh\",\"username\":\"scs\",\"email\":\"ax@gmail.com\",\"address\":{\"street\":\"PG vejdes väg\",\"suite\":\"1210\",\"city\":\"Växjö\",\"zipcode\":\"35252\",\"geo\":{\"lat\":0,\"lng\":0}}" 
```

Expected response: 
```
{
  "expose":true,
  "statusCode":400,
  "status":400,
  "body":" {
    \"name\":\"hcsahcsh\",
    \"username\":\"scs\",
    \"email\":\"ax@gmail.com\",
    \"address\":{
       \"street\":\"PG vejdes v?g\",
       \"suite\":\"1210\",
       \"city\":\"V?xj?\",
       \"zipcode\":\"35252\",
       \"geo\": {
        \"lat\":0,\"lng\":0}}",
  "type":"entity.parse.failed"
 }
 ```

**How to get the response code (add ```-i```, remove ```| jq '.'```, replace ```" "``` to ```' '```, username needs to be different from email)**

```
 curl -i -X POST "http://api.softhouse.rocks/users" -H "accept: application/json" -H "Content-Type: application/json" -d '{"name":"string","username":"strinsdfgdddd","email":"stsdfringee","address":{"street":"string","suite":"string","city":"string","zipcode":"string","geo":{"lat":0,"lng":0}}}'
```

Expected response:
```
HTTP/1.1 201 Created
```

### How to test a GET method for fetching a specific user
```
curl -X GET "http://api.softhouse.rocks/users/5" -H "accept: application/json"
```

Expected response:
```
{
  "address": {
    "geo": {
      "lat":-31.8129,
      "lng":62.5342},
    "street":"Skiles Walks",
    "suite":"Suite 351",
    "city":"Roscoeview","zipcode":"33263"},
  "_id":"5caaef896b334800cbf66336",
  "id":5,
  "name":"Chelsey Dietrich",
  "username":"Kamren",
  "email":"Lucio_Hettinger@annie.ca",
  "__v":0
}
```

**How to get the response code (add ```-i```)**
```
curl -i -X GET "http://api.softhouse.rocks/users/5" -H "accept: application/json"
```

Expected response:
```
HTTP/1.1 200 OK
```
 
### How to test a GET method for fetching a specific user
```
curl -X PUT "http://api.softhouse.rocks/users/5" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"name\":\"stringify\",\"username\":\"stringtwo\",\"email\":\"stringthree\",\"address\":{\"street\":\"string\",\"suite\":\"string\",\"city\":\"string\",\"zipcode\":\"string\",\"geo\":{\"lat\":0,\"lng\":0}}}"
```
 
Expected response:
```
 {
  "address": {
    "geo": {
      "lat":0,
      "lng":0},
    "street":"string",
    "suite":"string",
    "city":"string","zipcode":"string"},
  "_id":"5caaef896b334800cbf66336",
  "id":5,
  "name":"stringify",
  "username":"stringtwo",
  "email":"stringthree",
  "__v":0
 }
 ```
 
 **How to get the response code (add ```-i```)**
 
 ```
curl -i -X PUT "http://api.softhouse.rocks/users/5" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"name\":\"stringify\",\"username\":\"stringtwo\",\"email\":\"stringthree\",\"address\":{\"street\":\"string\",\"suite\":\"string\",\"city\":\"string\",\"zipcode\":\"string\",\"geo\":{\"lat\":0,\"lng\":0}}}"
```

Expected response:
```
HTTP/1.1 200 OK
```


## Useful information
* ```-d ``` - 
* ``` -v ``` - verbose mode makes curl mote talkative. It will explain and show a lot more of its doings and add informational tests and prefix them with '*'
* ``` curl -h``` - help mode will give you a list of different curl commands/options
* METHODS : ```GET```, ```POST```, ```PUT```, ```PATCH```, ```DELETE```
* PATHS: ```POSTS```, ```USERS```
* ```Conent-Type: application/json```
