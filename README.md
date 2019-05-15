# This is how softhouse.rocks API works.

Tools that we used 
command prompt/terminal
curl
jq

How you test POSTS

How to test a GET method 

curl -X GET "http://api.softhouse.rocks/posts?userId=3" -H "accept: application/json" | jq '.'

Expected response:
  {
    "_id": "5caaef896b334800cbf66354",
    "userId": 3,
    "id": 25,
    "title": "rem alias distinctio quo quis",
    "body": "ullam consequatur ut\nomnis quis sit vel consequuntur\nipsa eligendi ipsum molestiae et omnis error nostrum\nmolestiae illo tempore quia et distinctio",
    "__v": 0
  },


How to test a POST method

curl -X POST "http://api.softhouse.rocks/posts" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"string\",\"body\":\"string\",\"userId\":0}"

Expected response: 
{
  "_id":"5cdbcb18f4a0350020b4816b",
   "body":"string",
   "title":"string",
   "userId":0,"id":104,"__v":0
  }

How to test a PUT method

curl -X PUT "http://api.softhouse.rocks/posts/1" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hello world\",\"body\":\"Hello Sweden\",\"userId\":56}"

Expected response:
{
  "_id":"5caaef896b334800cbf6633c",
  "userId":56,
  "id":1,
  "title":"Hello world",
  "body":"Hello Sweden",
  "__v":0}
}
 
How to test a PATCH method

curl -X PATCH "http://api.softhouse.rocks/posts/1" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hello, Patch\",\"body\":\"Testing PATCH\",\"userId\":4445}"

Expected response:
{
  "_id":"5caaef896b334800cbf6633c",
  "userId":4445,
  "id":1,
  "title":"Hello, Patch",
  "body":"Testing PATCH",
  "__v":0
}

How to test a DELETE method

curl -X DELETE "http://api.softhouse.rocks/posts/2" -H "accept: application/json"

Expected response:
