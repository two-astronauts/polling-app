# polling-app
Real time polling app using RethinkDB and Nodejs

## Upload database

    docker run -p 8080:8080 -p 28015:28015 --name rethink rethinkdb

## Run app

    node app.js

## Queries

    r.db("polls").table("poll")

    r.db("polls").table("poll").count()

    r.db("polls").table("poll").pluck("question").distinct()

    r.db("polls").table('poll').get("0bf52c32-cc79-4f29-bd40-9932c6bd2d5e")

    r.db("polls").table('poll').filter(r.row("question").eq("Best phone?"))

    r.db("polls").table('poll').filter(r.row("question").eq("Best phone?")).limit(5)

    r.db("polls").table('poll').get("0bf52c32-cc79-4f29-bd40-9932c6bd2d5e")("polls")("option")

    r.db("polls").table("poll").filter(function (row) {
        return row('polls').map(function (o) {
            return o('option').eq("Android")
        }).eq([true])
    })
