# API Testing Application

Simple example of a blogging site backend running across multiple docker containers. Showcases CRUD functionality using Express, user authentication and sessions, data storing, and load balancing

Users can sign up, login, create posts, update posts, and delete posts. Post information will be stored inside a MongoDB database with a named volume so the information is retained when the containers are taken down

User session is stored in Redis. User requests are load balanced in Nginx

## Getting Started
Install Docker and Docker Compose on your machine

Docker containers:
1. Node (node:15)
2. Mongo (mongo)
3. Redis (redis)
4. Nginx (nginx:stable-alpine)

Docker volumes:
1. Mongo

There are two environments:

1. Development
2. Production

To start an environment, use the docker-compose command
`docker-compose -f docker-compose.yml -f docker-compose.dev.yml up`

The server will be running at http://localhost:3000

## API Testing
### Post
Route : http://localhost:3000/api/v1/posts

Body example:
```
{
    "title": "my first post"
    "body": "body of first post"
}
```
Response:

Creates a post. Returns `"status": "success"` along with the ID and the body of the post if post succeeds, `"status": "failed"` if it fails

### Get
Route : http://localhost:3000/api/v1/posts

Response:

Returns all of the posts

Route : http://localhost:3000/api/v1/posts/**ID of the post**

Response :

Returns a specific post

### Update
Route : http://localhost:3000/api/v1/posts/**ID of the post**

Body example:
```
{
    "title": "my first post updated"
    "body": "body of first post updated"
}
```
Response:

Update the contents of a specific post. Returns `"status": "success"` along with the ID and the body of the updated post if update succeeds, `"status": "failed"` if it fails

### Delete
Route : http://localhost:3000/api/v1/posts/**ID of the post**

Response :

Deletes a specific post. Returns `"status": "success"`if delete succeeds, `"status": "failed"` if it fails