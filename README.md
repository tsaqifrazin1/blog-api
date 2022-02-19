# blog-api

## How To Use

### Local

- Make sure you have installed MongoDB on your local and create `nodeblog` database
- Clone this repository into your local repository `git clone https://github.com/tsaqifrazin1/blog-api.git`
- Run `npm install` => `npm run start`
- If you get `listening on http://localhost:3000` on your console, you can use the api on your local now.

### Public Endpoint

`https://blog-api-fem.herokuapp.com`

## REST API

The REST API to the example blog-api is described below (following example is for local, for the public endpoint, please change `localhost:3000` to `https://blog-api-fem.herokuapp.com` in Request section)

## Auth

- #### Sign in with seed data

  ##### Request

  `POST /auth/signin`

        curl --location --request POST 'localhost:3000/auth/signin' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "username": "katamon",
            "password": "test"
        }'

  ##### Response

        HTTP/1.1 200 OK
        X-Powered-By: Express
        Access-Control-Allow-Origin: *
        Vary: X-HTTP-Method-Override
        Content-Type: application/json; charset=utf-8
        Content-Length: 184
        ETag: W/"b8-Dye/xnHuNAPNleIb9K5kSRejxRg"
        Date: Thu, 17 Feb 2022 17:30:09 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlNzgwOTM0NGUxOTRhMzViYjgwMmQiLCJpYXQiOjE2NDUxMTkwMDgsImV4cCI6MTY0NTk4MzAwOH0.19aZfo_LdCLDj3pZghHipueUXiiG4TebJHhqpQtkn24"}

## Users

CRUD Users collections

- #### Read All Users data

  ##### Request

  `GET /api/users`

      curl --location --request GET 'localhost:3000/api/users/'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 190
      ETag: W/"be-hQ2DOoSVEdyuf1XM2P/mB5FhKeI"
      Date: Thu, 17 Feb 2022 17:35:17 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      [{"_id":"620e7809344e194a35bb802c","username":"Xoko","__v":0},{"_id":"620e7809344e194a35bb802d","username":"katamon","__v":0},{"_id":"620e7809344e194a35bb802b","username":"Jimmylo","__v":0}]

- #### Create User Data

  ##### Request

  `POST /api/users`

      curl --location --request POST 'localhost:3000/api/users/' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "username": "Razin",
          "password": "pass"
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Vary: X-HTTP-Method-Override
      Content-Type: application/json; charset=utf-8
      Content-Length: 184
      ETag: W/"b8-4KkZMsAbXAJGqlJlY9BU1CcbbUg"
      Date: Thu, 17 Feb 2022 17:47:31 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOGEzMjM0NGUxOTRhMzViYjgwNGUiLCJpYXQiOjE2NDUxMjAwNTEsImV4cCI6MTY0NTk4NDA1MX0.K5OJBOl9jo0rsJftQBKoMpBhLx1mrz9ZDoJn_2HHYV4"}

- #### Get One User data by \_id

  ##### Request

  `GET /api/users/<id>` (get \_id from one of user in Read All Users data)

      curl --location --request GET 'localhost:3000/api/users/620e8ddbc2ae8c9fe206f61f'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 63
      ETag: W/"3f-9sqD19yohsaKJbDKy39nZTGjh7Q"
      Date: Thu, 17 Feb 2022 18:03:47 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e8ddbc2ae8c9fe206f61f","username":"Jimmylo","__v":0}

- #### Get me

  ##### Request

  `GET /api/users/me?access_token=<token you get from signin>` (get \_id from one of user in Read All Users data)

      curl --location --request GET 'localhost:3000/api/users/me?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGIiLCJpYXQiOjE2NDUxMjM0NjEsImV4cCI6MTY0NTk4NzQ2MX0.sRhWLNMEh2RxcPU43LFD6wqiMQFVOjys_AEZMyaqKiY'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 63
      ETag: W/"3f-9sqD19yohsaKJbDKy39nZTGjh7Q"
      Date: Thu, 17 Feb 2022 18:03:47 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e8ddbc2ae8c9fe206f61f","username":"Jimmylo","__v":0}

- #### Update User data by \_id

  ##### Request

  `PUT /api/users/<id>?access_token=<token you get from signin>` (get \_id from one of user in Read All Users data)

      curl --location --request PUT 'localhost:3000/api/users/620e975b3fa79592ba5ea34b?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGIiLCJpYXQiOjE2NDUxMjM0NjEsImV4cCI6MTY0NTk4NzQ2MX0.sRhWLNMEh2RxcPU43LFD6wqiMQFVOjys_AEZMyaqKiY' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "username": "jimmylo"
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 63
      ETag: W/"3f-w9BkDRisztzClMVTT2BCjrWN5Vo"
      Date: Thu, 17 Feb 2022 18:49:39 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e975b3fa79592ba5ea34b","username":"jimmylo","__v":0}

- #### Delete User data by \_id

  ##### Request

  `DELETE /api/users/<id>?access_token=<token you get from signin>` (get \_id from one of user in Read All Users data)

      curl --location --request DELETE 'localhost:3000/api/users/620e975b3fa79592ba5ea34b?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGIiLCJpYXQiOjE2NDUxMjM0NjEsImV4cCI6MTY0NTk4NzQ2MX0.sRhWLNMEh2RxcPU43LFD6wqiMQFVOjys_AEZMyaqKiY'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 63
      ETag: W/"3f-w9BkDRisztzClMVTT2BCjrWN5Vo"
      Date: Thu, 17 Feb 2022 18:53:42 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e975b3fa79592ba5ea34b","username":"jimmylo","__v":0}

## Categories

CRUD Categories collection

- #### Read All Categories data

  ##### Request

  `GET /api/categories`

      curl --location --request GET 'localhost:3000/api/categories/`

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 178
      ETag: W/"b2-TiBqU2ffPVzVGBmDhtFnSqwNdig"
      Date: Thu, 17 Feb 2022 19:03:43 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      [{"_id":"620e975b3fa79592ba5ea351","name":"intros","__v":0},{"_id":"620e975b3fa79592ba5ea352","name":"angular","__v":0},{"_id":"620e975b3fa79592ba5ea353","name":"UI/UX","__v":0}]

- #### Create Categories Data

  ##### Request

  `POST /api/categories?access_token=<token you got from signin>`

      curl --location --request POST 'localhost:3000/api/categories/?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "name": "Tech"
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Vary: X-HTTP-Method-Override
      Content-Type: application/json; charset=utf-8
      Content-Length: 56
      ETag: W/"38-8xo5rGcy6ALhdf9tncTWxMFbtWY"
      Date: Thu, 17 Feb 2022 19:09:02 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"name":"Tech","_id":"620e9d4e3fa79592ba5ea378","__v":0}

- #### Get One Categories data by \_id

  ##### Request

  `GET /api/categories/<id>` (get \_id from one of categories in Read All Categories data)

      curl --location --request GET 'localhost:3000/api/categories/620e9d4e3fa79592ba5ea378'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 56
      ETag: W/"38-Vogr97rDVQbbn+JC38f0SXWxaA4"
      Date: Thu, 17 Feb 2022 19:12:42 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e9d4e3fa79592ba5ea378","name":"Tech","__v":0}

- #### Update Categories data by \_id

  ##### Request

  `PUT /api/categories/<id>?access_token=<token you get from signin>` (get \_id from one of categories in Read All Categories data)

      curl --location --request PUT 'localhost:3000/api/categories/620e9d4e3fa79592ba5ea378?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "name": "IT"
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 54
      ETag: W/"36-31lt6G6ABuzUg3/g74mkQKflHEs"
      Date: Thu, 17 Feb 2022 19:15:59 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e9d4e3fa79592ba5ea378","name":"IT","__v":0}

- #### Delete Categories data by \_id

  ##### Request

  `DELETE /api/categories/<id>?access_token=<token you get from signin>` (get \_id from one of categories in Read All Categories data)

      curl --location --request DELETE 'localhost:3000/api/categories/620e9d4e3fa79592ba5ea378?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 54
      ETag: W/"36-31lt6G6ABuzUg3/g74mkQKflHEs"
      Date: Thu, 17 Feb 2022 19:20:25 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e9d4e3fa79592ba5ea378","name":"IT","__v":0}

## Posts

CRUD Posts collection

- #### Read All Posts

  ##### Request

  `GET /api/posts`

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 840
      ETag: W/"348-9QaZxfaKbAf1b8gJ7jsf4f/2rIk"
      Date: Thu, 17 Feb 2022 19:22:45 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      [{"_id":"620e975b3fa79592ba5ea357","title":"Learn angular 2 today","text":"Angular to is so dope","author":null,"categories":[{"_id":"620e975b3fa79592ba5ea351","name":"intros","__v":0}],"__v":1},{"_id":"620e975b3fa79592ba5ea358","title":"10 reasons you should love IE7","text":"IE7 is so amazing","author":{"_id":"620e975b3fa79592ba5ea34c","username":"Xoko","password":"$2a$10$PXjlnLgQsDykcWWatRckBu0hlag/smgX/iUSIRXK9gPIvB8pRDzCS","__v":0},"categories":[{"_id":"620e975b3fa79592ba5ea352","name":"angular","__v":0}],"__v":1},{"_id":"620e975b3fa79592ba5ea359","title":"Why we switched to Go","text":"go is dope","author":{"_id":"620e975b3fa79592ba5ea34d","username":"katamon","password":"$2a$10$quezfFMMJDwAtBPBWcLMyOm71gao4z3idRTtzZNS8DHTw3arUNVyi","__v":0},"categories":[{"_id":"620e975b3fa79592ba5ea353","name":"UI/UX","__v":0}],"__v":1}]


      curl --location --request GET 'localhost:3000/api/categories/`

- #### Create Post Data

  ##### Request

  `POST /api/posts?access_token=<token you got from signin>`

      curl --location --request POST 'localhost:3000/api/posts?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "title": "Learn IT",
          "text": "NodeJs",
          "author": "620e975b3fa79592ba5ea34c",
          "categories": ["620e975b3fa79592ba5ea351"]
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Vary: X-HTTP-Method-Override
      Content-Type: application/json; charset=utf-8
      Content-Length: 155
      ETag: W/"9b-ak+AXvoS42Eoa+8rHdg8Du0AsJc"
      Date: Thu, 17 Feb 2022 19:33:59 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

- #### Read One Post Data

  ##### Request

  `GET /api/posts/620e975b3fa79592ba5ea357`

      curl --location --request GET 'localhost:3000/api/posts/620e975b3fa79592ba5ea357'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 161
      ETag: W/"a1-UclRLmSWZu8LV+PTok83qgLm6YM"
      Date: Thu, 17 Feb 2022 19:39:37 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e975b3fa79592ba5ea357","title":"Learn angular 2 today","text":"Angular to is so dope","author":null,"categories":["620e975b3fa79592ba5ea351"],"__v":1}
            {"title":"Learn IT","text":"NodeJs","author":"620e975b3fa79592ba5ea34d","categories":["620e975b3fa79592ba5ea351"],"_id":"620ea3273fa79592ba5ea389","__v":0}

- #### Update One Post by \_id

  ##### Request

  `PUT /api/posts/<id>?access_token=<token you get from signin>` (get \_id from one of post in Read All Posts data)

      curl --location --request PUT 'localhost:3000/api/posts/620e975b3fa79592ba5ea357?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU' \
      --header 'Content-Type: application/json' \
      --data-raw '{
          "title": "Let'\''s Learn",
          "text": "Great"
      }'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 135
      ETag: W/"87-Kc1EnFUCRRLp+mbvYgvIymTDIzQ"
      Date: Thu, 17 Feb 2022 19:47:18 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e975b3fa79592ba5ea357","title":"Let's Learn","text":"Great","author":null,"categories":["620e975b3fa79592ba5ea351"],"__v":1}

- #### Delete One post by \_id

  ##### Request

  'DELETE /api/posts/<id>?access_token=<token you get from signin>` (get \_id from one of post in Read All Posts data)

      curl --location --request DELETE 'localhost:3000/api/posts/620e975b3fa79592ba5ea357?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI2MjBlOTc1YjNmYTc5NTkyYmE1ZWEzNGQiLCJpYXQiOjE2NDUxMjQ5MjMsImV4cCI6MTY0NTk4ODkyM30.5y1N8aiNyt-BNb-Q07d7D5f30I0f5AbKGm0r2x-avhU'

  ##### Response

      HTTP/1.1 200 OK
      X-Powered-By: Express
      Access-Control-Allow-Origin: *
      Content-Type: application/json; charset=utf-8
      Content-Length: 135
      ETag: W/"87-Kc1EnFUCRRLp+mbvYgvIymTDIzQ"
      Date: Thu, 17 Feb 2022 19:55:21 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5

      {"_id":"620e975b3fa79592ba5ea357","title":"Let's Learn","text":"Great","author":null,"categories":["620e975b3fa79592ba5ea351"],"__v":1}
