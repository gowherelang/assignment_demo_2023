# assignment_demo_2023

![Tests](https://github.com/TikTokTechImmersion/assignment_demo_2023/actions/workflows/test.yml/badge.svg)

This is the backend assignment for [TikTok Tech Immersion Programme 2023](https://bytedance.sg.feishu.cn/docx/CEusdOSGHody93xCekHlbBOvgGR), to design and implement the backend system of an Instant Messaging System.
Only the backend is developed for this assignment, frontend is not required (viewed using Postman).

## Installation

Tech used:

- Golang 1.18+ for backend
- TikTok's Kitex framework for RPC-server
- Thrift as Interface Definition Language (IDL) to define structs and services
- Docker for containerization
- Redis for database, key-value
- Postman API for testing backend using CURL

System design from assignment:
![system design image for Postman](https://raw.githubusercontent.com/gowherelang/assignment_demo_2023/main/postman/systemdesign.png)
## Run docker

```bash
docker-compose up -d
```

Check if it's running:

```bash
curl localhost:8080/ping
```

## Postman screenshots
### POST a message from user1 (alpha) to user2 (beta), format of chat "user1:user2" 
```bash 
curl --location 'localhost:8080/api/send' \
--header 'Content-Type: application/json' \
--data '{
    "chat": "alpha:beta",
    "text": "hello beta, from alpha",
    "sender": "alpha"
}'
```
![POST image for Postman](https://raw.githubusercontent.com/gowherelang/assignment_demo_2023/main/postman/postman%20POST.png)
### GET messages between 2 users
"limit" = maximum number of messages to pull
<br>"cursor" = index which you want to start to pull
e.g. msg list = [1, 2, 3, 4, 5], cursor = 2, limit = 2, results in [3, 4] 
```bash
curl --location --request GET 'localhost:8080/api/pull' \
--header 'Content-Type: application/json' \
--data '{
"chat": "alpha:beta",
"cursor": 0,
"limit": 20,
"reverse": true
}'
```
![GET image for Postman](https://raw.githubusercontent.com/gowherelang/assignment_demo_2023/ffc2076b581aea175992bfe10e4d16f34bf03ef5/postman/postman%20GET.png)
