# httpie-curl-examples

Working demo on how to use httpie and curl terminal commands (HEAD, GET, POST, PUT, PATCH, DELETE)

# Prerequisites

- [curl](https://curl.se/)
- [httpie](https://httpie.io/)
- [node.js v22](https://nodejs.org)

# Suggested

- [volta](https://volta.sh/)

# Install

```
npm install
```

# Run server

```
npm start
```

![server running](./screenshots/server-running.png)

# HEAD

## curl

```
curl --head http://localhost:3000/posts
curl --I localhost:3000/posts
```

![head-curl](./screenshots/curl/head.png)

## httpie

```
http HEAD http://localhost:3000/posts
http HEAD localhost:3000/posts
```

![head-httpie](./screenshots/httpie/head.png)

# GET

## curl

```
curl --request 'GET' http://localhost:3000/posts
curl -X 'GET' localhost:3000/posts
```

![get-curl](./screenshots/curl/get.png)

## httpie

```
http GET http://localhost:3000/posts
http localhost:3000/posts
```

![get-httpie](./screenshots/httpie/get.png)

# POST

## curl

```
curl --request 'POST' http://localhost:3000/posts -d '{ "id": "3-curl", "title": "title 3-curl, post", "views": 0 }'
curl -X 'POST' localhost:3000/posts -d '{ "id": "3-curl", "title": "title 3-curl, post", "views": 0 }'
```

![post-curl](./screenshots/curl/post.png)

## httpie

```
http POST http://localhost:3000/posts id='3-httpie' title='title 3-httpie, post' views:=0
http localhost:3000/posts id='3-httpie' title='title 3-httpie, post' views:=0
echo '{ "id": "3-httpie", "title": "title 3-httpie, post", "views": 0 }' | http localhost:3000/posts
http localhost:3000/posts @./data/httpie-post.json
http localhost:3000/posts < ./data/httpie-post.json
```

![post-httpie](./screenshots/httpie/post.png)

# PUT (run previously POST or return `404 Not found`)

## curl

```
curl --request 'PUT' http://localhost:3000/posts/3-curl -d '{ "id": "3-curl", "title": "title 3-curl, put", "views": 1 }'
curl -X 'PUT' localhost:3000/posts/3-curl -d '{ "id": "3-curl", "title": "title 3-curl, put", "views": 1 }'
```

![put-curl](./screenshots/curl/post.png)

## httpie

```
http PUT http://localhost:3000/posts/3-httpie id='3-httpie' title='title 3-httpie, put' views:=1
http PUT localhost:3000/posts/3-httpie id='3-httpie' title='title 3-httpie, put' views:=1
echo '{ "id": "3-httpie", "title": "title 3-httpie, put", "views": 1 }' | http PUT localhost:3000/posts/3-httpie
http PUT localhost:3000/posts/3-httpie @./data/httpie-put.json
http PUT localhost:3000/posts/3-httpie < ./data/httpie-put.json


```

![put-httpie](./screenshots/httpie/put.png)

# PATCH (run previously POST, optionally PUT, or return `404 Not found`)

## curl

```
curl --request 'PATCH' http://localhost:3000/posts/3-curl -d '{ "views": 2 }'
curl -X 'PATCH' localhost:3000/posts/3-curl -d '{ "views": 2 }'
```

![patch-curl](./screenshots/curl/patch.png)

## httpie

```
http PATCH http://localhost:3000/posts/3-httpie views:=2
http PATCH localhost:3000/posts/3-httpie views:=2
echo '{ "views": 2 }' | http PATCH localhost:3000/posts/3-httpie
http PATCH localhost:3000/posts/3-httpie @./data/httpie-patch.json
http PATCH localhost:3000/posts/3-httpie < ./data/httpie-patch.json
```

![patch-httpie](./screenshots/httpie/patch.png)

# DELETE (run previously POST, optionally PUT and PATCH, or return `404 Not found`)

## curl

```
curl --request 'DELETE' http://localhost:3000/posts/3-curl
curl -X 'DELETE' localhost:3000/posts/3-curl
```

![delete-curl](./screenshots/curl/delete.png)

## httpie

```
http DELETE http://localhost:3000/posts/3-httpie
http DELETE localhost:3000/posts/3-httpie
```

![delete-httpie](./screenshots/httpie/delete.png)
