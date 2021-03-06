# FoodFinder
## Setup
### Install Dependencies
  * Erlang / OTP version 21
  * Elixir version 1.7
  * Phoenix version 1.4
  * NodeJS version 8.10 (e.g. the Ubuntu packages: nodejs npm)
  * Standard C/C++ dev tools (e.g. the Ubuntu build-essential package)
  * Postgresql 10.5

### Setup Postgres

Setup Postgres User
```
$ service postgresql start
$ sudo su - postgres
pg$ cd ~
pg$ createuser -d food_finder
pg$ psql
postgres=# alter user food_finder with password '<password>';
pg$ ^D
```

Edit config/dev.exs and test.exs
```
config :food_finder, FoodFinder.Repo,
  username: "food_finder",
  password: "<replace Ashwin's password with yours>",
  database: "food_finder_dev",
  hostname: "localhost",
  pool_size: 10
```

Create DB
```
$ mix ecto.create
$ mix ecto.migrate
```


### Register a Google API Key
Go to https://console.cloud.google.com and figure out how to make an API Key
Then export it to your environment so that the app can use it.
```
export GOOGLE_API_KEY=<insert key here>
```
This will add the variable for your current terminal session. Put it in your bashrc
or equivalent for your terminal to have it be loaded for other terminal sessions.

### Starting Geolocated

To install the React Geolocated:

* `(cd assets && npm install react-geolocated --save`)


### Starting Phoenix

To start your Phoenix server:

  * Install dependencies with `mix deps.get`
  * Create and migrate your database with `mix ecto.create && mix ecto.migrate`
  * Install Node.js dependencies with `cd assets && npm install`
  * Start Phoenix endpoint with `mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

Ready to run in production? Please [check our deployment guides](http://www.phoenixframework.org/docs/deployment).

## Learn more

  * Official website: http://www.phoenixframework.org/
  * Guides: http://phoenixframework.org/docs/overview
  * Docs: https://hexdocs.pm/phoenix
  * Mailing list: http://groups.google.com/group/phoenix-talk
  * Source: https://github.com/phoenixframework/phoenix
