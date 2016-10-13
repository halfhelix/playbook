## Rails

A guide for writing great web apps.

## Create App

Use suspenders unless good reason not to.

Get Suspenders.

    gem install suspenders

Create the app.

    suspenders app --heroku true --github organization/app

## Set Up App

Get the code.

    git clone git@github.com:organization/app.git

Set up the app's dependencies.

    cd project
    ./bin/setup

Use [Heroku config](https://github.com/ddollar/heroku-config) to get `ENV`
variables.

    heroku config:pull --remote staging

Delete extra lines in `.env`, leaving only those needed for app to function
properly. For example: `BRAINTREE_MERCHANT_ID` and `S3_SECRET`.

## Git Protocol

Follow the normal [Git Protocol](/protocol/git).
