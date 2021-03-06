{{cookiecutter.project_name}}
==============================

{{cookiecutter.description}}


LICENSE: BSD

Deployment
------------

* heroku create
* heroku addons:add heroku-postgresql:dev
* heroku addons:add pgbackups:auto-month
* heroku addons:add sendgrid:starter
* heroku pg:promote HEROKU_POSTGRESQL_COLOR
* heroku config:add AWS_ACCESS_KEY_ID=YOUR_ID
* heroku config:add AWS_SECRET_ACCESS_KEY=YOUR_KEY
* heroku config:add AWS_STORAGE_BUCKET_NAME=BUCKET
* heroku labs:enable user-env-compile
* git push heroku master
* heroku run python {{cookiecutter.repo_name}}/manage.py syncdb --all --noinput
* heroku run python {{cookiecutter.repo_name}}/manage.py migrate --fake
* heroku run python {{cookiecutter.repo_name}}/manage.py createsuperuser

Run this script: (TODO - automate this)

.. code-block:: python

    from django.contrib.sites.models import Site
    site = Site.objects.get()
    site.domain = "{{cookiecutter.domain_name}}"
    site.name = "{{cookiecutter.project_name}}"
    site.save()
