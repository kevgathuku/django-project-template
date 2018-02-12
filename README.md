# Django project template

This is a simple Django 2.0+ project template with my preferred setup. Most Django project templates make way too many
assumptions or are just way too complicated. I try to make the least amount of assumptions possible while still trying
provide a useful setup. Most of my projects are deployed to Heroku, so this is optimized for that but is not necessary.

## Features

- Latest Django (hopefully).
- Uses [Pipenv](https://github.com/kennethreitz/pipenv) - the best packaging tool.
- [django-extensions](http://django-extensions.readthedocs.org) for the various useful commands and things.
- [ShortUUID](https://github.com/skorokithakis/shortuuid), because I end up using it most of the time.
- Secure by default (various things won't work on production without TLS).
  backend).
- Runs using SQLite by default, for when you aren't using Postgres-specific features yet.
- Other things I'm forgetting now.


## Installation

Installing the template is easy, you don't really have to do much:

```bash
django-admin.py startproject \
  --template=https://github.com/skorokithakis/django-project-template/archive/master.zip \
  --extension py,cfg,yml,ini \
  project_name
```

You can then run it locally:

```bash
$ pipenv install --dev
$ ./manage.py migrate
$ ./manage.py runserver_plus
```

Then you can access your project at [http://localhost:8080/](http://localhost:8080/), like a plebe.


## Dokku deployment

The template comes with most of the things you need to deploy it on Dokku. You will need to set up a Postgres database,
a Redis instance and a TLS certificate firt, though. For instructions, see my post on [deploying Django projects on
Dokku](https://www.stavros.io/posts/deploy-django-dokku/).


## Production deployment tips

You're going to need to add some secrets for production. That's fine, as long as you don't commit them in any repo. The
project is structured such that all secrets can be passed as environment variables (see the settings file for the
variable names).

You can also specify any secret keys or settings in a `local_settings.py`, which will override your `settings.py`
variables. I usually use that for local development.
