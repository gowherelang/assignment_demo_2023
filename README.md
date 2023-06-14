# assignment_demo_2023

![Tests](https://github.com/TikTokTechImmersion/assignment_demo_2023/actions/workflows/test.yml/badge.svg)

This is the backend assignment for 2023 TikTok Tech Immersion.
<br>It is a simulation of an Instant Messaging System, to design and implement the backend. 

## Installation

Tech used:

- Golang 1.18+ for backend
- Docker for containerization
- Redis for database
- Postman for client CURL testing

To install dependency tools:

```bash
make pre
```

## Run

```bash
docker-compose up -d
```

Check if it's running:

```bash
curl localhost:8080/ping
```

## Postman screenshots
### POST
```bash
curl --location 'localhost:8080/api/send' \
--header 'Content-Type: application/json' \
--data '{
    "chat": "alpha:beta",
    "text": "hello beta, from alpha",
    "sender": "alpha"
}'
```
### GET
```bash
curl --location --request GET 'localhost:8080/api/pull' \
--header 'Content-Type: application/json' \
--data '{
"chat": "alpha:beta",
"limit": 20
}'
```
