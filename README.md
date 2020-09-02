# practice-loopback

This is the code written while roughly following the [LoopBack](https://loopback.io/doc/en/lb4/todo-tutorial.html) [Todo Tutorial](https://loopback.io/doc/en/lb4/todo-tutorial.html).

Technologies used:

- loopback: 4.0.6
- node: v18.9.0
- npm: 9.1.2

## Set up

Install the node application:

```bash
cd todo-list
npm i
```

Start the loopback server:

```
npm start
```

The OpenAPI docs should now be available at: [http://127.0.0.1:3000/explorer/](http://127.0.0.1:3000/explorer/)

## API Requests

The easiest way to make requests is by using the [OpenAPI UI](http://127.0.0.1:3000/explorer/) (access while the server is running locally).

### **GET** Health Check `/ping`

Example request:

```bash
curl -X 'GET' \
  'http://127.0.0.1:3000/ping' \
  -H 'accept: application/json'
```

Example response:

```bash
{
  "greeting": "Hello from LoopBack",
  "date": "2022-12-28T13:06:19.045Z",
  "url": "/ping",
  "headers": {
    "host": "127.0.0.1:3000",
    "user-agent": "curl/7.79.1",
    "accept": "application/json"
  }
}
```

### **GET** Todos Count `/todos/count`

Example request:

```bash
curl -X 'GET' \
  'http://127.0.0.1:3000/todos/count' \
  -H 'accept: application/json'
```

Example response:

```bash
{
  "count": 5
}
```

### **PUT** Todos Update Full By Id `/todos/{id}`

Example request:

```bash
curl -X 'PUT' \
  'http://127.0.0.1:3000/todos/1' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "id": 1,
  "title": "Updated title",
  "desc": "Updated description",
  "isComplete": true
}'
```

Example response:

```bash
200 No Content
```

### **PATCH** Todos Update Partial By Id `/todos/{id}`

Example request:

```bash
curl -X 'PATCH' \
  'http://127.0.0.1:3000/todos/1' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "Updated"
}'
```

Example response:

```bash
204 No Content
```

### **GET** Todos Get By Id `/todos/{id}`

Example request:

```bash
curl -X 'GET' \
  'http://127.0.0.1:3000/todos/1' \
  -H 'accept: application/json'
```

Example response:

```bash
{
  "id": 1,
  "title": "Take over the galaxy",
  "desc": "MWAHAHAHAHAHAHAHAHAHAHAHAHAMWAHAHAHAHAHAHAHAHAHAHAHAHA",
  "isComplete": false
}
```

### **DELETE** Todos Delete By Id `/todo/{id}`

Example request:

```bash
curl -X 'DELETE' \
  'http://127.0.0.1:3000/todos/1' \
  -H 'accept: application/json'
```

Example response:

```bash
204 No Content
```

### **POST** Todos Create `/todos`

Example request:

```bash
curl -X 'POST' \
  'http://127.0.0.1:3000/todos' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "string",
  "desc": "string",
  "isComplete": true
}'
```

Example response:

```bash
{
  "id": 6,
  "title": "string",
  "desc": "string",
  "isComplete": true
}
```

### **PATCH** Todos Update Partial `/todos`

Example request:

```bash
curl -X 'PATCH' \
  'http://127.0.0.1:3000/todos' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "desc": "string"
}'
```

Example response:

```bash
{
  "count": 5
}
```

### **GET** Todos Get `/todos`

Example request:

```bash
curl -X 'GET' \
  'http://127.0.0.1:3000/todos' \
  -H 'accept: application/json'
```

Example response:

```bash
[
  {
    "id": 1,
    "title": "Take over the galaxy",
    "desc": "MWAHAHAHAHAHAHAHAHAHAHAHAHAMWAHAHAHAHAHAHAHAHAHAHAHAHA",
    "isComplete": false
  },
  {
    "id": 2,
    "title": "destroy alderaan",
    "desc": "Make sure there are no survivors left!",
    "isComplete": false
  },
  {
    "id": 3,
    "title": "play space invaders",
    "desc": "Become the very best!",
    "isComplete": false
  },
  {
    "id": 4,
    "title": "crush rebel scum",
    "desc": "Every.Last.One.",
    "isComplete": true
  },
  {
    "id": 5,
    "title": "test",
    "desc": "show up",
    "isComplete": false
  }
]
```