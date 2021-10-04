
# API Testing Application

Simple example of a blogging site backend running across multiple docker containers. Showcases CRUD functionality using Express, user authentication and sessions, data storing, and load balancing

Users can sign up, login, create posts, update posts, and delete posts. Post information will be stored inside a MongoDB database with a named volume so the information is retained when the containers are taken down

User session is stored in Redis. User requests are load balanced in Nginx

## Getting Started

Install Docker and Docker Compose on your machine  
Docker containers used:

| Image | Tag |
| --- | --- |
| Node | 15 |
| Mongo | latest |
| Redis | latest |
| Nginx | stable-alpine |


Docker volume: Mongo

There are two environments:

1. Development
2. Production

To start an environment, use the docker-compose command. Example:

`docker-compose -f docker-compose.yml -f docker-compose.dev.yml up`  

The server will be running at http://localhost:3000

## API Testing

| Method | Route  | Response |
| --- | --- | --- |
| Create | /api/v1/posts | Creates a post. Returns `"status": "success"` along with the ID and the body of the post if post succeeds, `"status": "failed"` if it fails |
| Read All Posts |  /api/v1/posts/ | Returns all of the posts |
| Read Specific Post |  /api/v1/posts/ `<ID of the post>` | Returns a specific post referenced from post ID |
| Update | /api/v1/posts/ `<ID of the post>` | Updates the contents of a specific post. Returns `"status": "success"` along with the ID and the body of the updated post if update succeeds, `"status": "failed"` if it fails |
| Delete |  /api/v1/posts/ `<ID of the post>` | Deletes a specific post. Returns `"status": "success"`if delete succeeds, `"status": "failed"` if it fails |

Body format example:
```
{
    "title": "my first post"
    "body": "body of first post"
}
```