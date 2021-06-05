# How to build


### backend setup
```
$ cd ./myapp/
$ docker-compose run --no-deps backend rails new . --api -fT -d postgresql
```

### frontend setup
```
$ docker-compose run frontend yarn create nuxt-app app --edge

# Fix frontend/app/package.json
.
.
"scripts": {
    "dev": "HOST=0.0.0.0 PORT=3000 nuxt",   <- Fix
.
```

### After setup
```
$ docker-compose build

# Fix backend/config/database.yml
default: &default
  adapter: postgresql
  encoding: unicode
  host: db            <- Add 
  username: postgres  <- Add 
  password:           <- Add 
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>

$ docker-compose run --rm backend rails db:create
$ docker-compose up -d
```

frontend install library
```
npm install @nuxtjs/vuetify --save


```
