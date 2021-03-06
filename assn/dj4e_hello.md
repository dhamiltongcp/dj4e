Hello World
===========

At this point in the course we are going to start over and build a series of
applications in a Django project.  To review terminology, in the work that you
have done so far:

* `django_projects` is a folder and/or a github repository that contains multiple
Django projects

* `locallibrary` is a *project* in that folder that can contain many applications.  The
project configuration is in the folder `localllibrary/locallibrary`.

* `catalog` is an *application* within the `locallibrary` project that has models,
views, templates, admin configurations, etc.

At this point you should be doing development
locally and uploading it to PythonAnywhere or just using ngrok to turn it in. If
you don't have a compure that can run Django locally you can continue to use
PythonAnywhere but increasingly examples will be shown unsing local development
patterns.

This application will end up with a similar structure to

https://github.com/csev/dj4e-samples/tree/master/autos

**Do not clone this repository**.  It is just to be used as sample code as you
build your new project and application in your `django_projects` folder.

We first need to make a new project within our `django_projects` folder.   It is time
to stop working on `locallibrary` - just keep it working so you can refer back to it
as you build new applications.

Making a New Project
--------------------

Activate any virtual environment you need (if any) and go into your `django_projects` folder
and start a new project and an application:

    workon django2  # as needed
    cd ~/django_projects
    django-admin startproject dj4e

    cd ~/django_projects/dj4e
    python3 manage.py startapp home

Using Django Locally
--------------------

    cd ~/django_projects/dj4e
    python3 manage.py runserver

In general as you make changes to the files below, runserver will monitor
for file changes and restart itself although sometimes you do want to abort
runserver and restart it manually to make sure it sees every new change.

If you are running Django on PythonAnywhere
-------------------------------------------

Under your Web tab, Set the following:

    Source Code:   /home/--your account--/django_projects/dj4e
    Working Directory:   /home/--your account--/django_projects/dj4e

In your WGSI Configuration file use:

    import os
    import sys

    path = os.path.expanduser('~/django_projects/dj4e')
    if path not in sys.path:
        sys.path.insert(0, path)
    os.environ['DJANGO_SETTINGS_MODULE'] = 'dj4e.settings'
    from django.core.wsgi import get_wsgi_application
    from django.contrib.staticfiles.handlers import StaticFilesHandler
    application = StaticFilesHandler(get_wsgi_application())

Of course you need to Reload your application as you make changes to the files below.

Files to Edit
-------------

These are the steps to get things started:

* Edit the `dj4e/dj4e/settings.py`, fix `ALLOWED_HOSTS` and add the home application:

        INSTALLED_APPS = [
            ...
            'home.apps.HomeConfig',    <--- Add
        ]

* Edit `dj4e/dj4e/urls.py` to include the `dj4e/home/urls.py` file.  Do *not* add any redirect
route like we used in the locallibrary / catalog application.

* Edit the `dj4e/home/urls.py` file to add a path that routes the '' path to a direct template view
pointing at a file `dj4e/home/templates/main_home.html`

* Edit `dj4e/home/templates/main_home.html` and put in some text that says "Hello World ... " and
some additional text about cats and/or any text or meta tag
that the autograder is asking for.

Once your project is working, you probably want to check it into github and make a tag
named 'hello_world'.

References
----------

* <a href="https://github.com/csev/dj4e-samples/tree/master/hello" target="_blank">Hello World Sample Code</a>

* <a href="https://github.com/csev/dj4e-samples/tree/master/tmpl" target="_blank">Templates Sample Code</a>

* <a href="dj_install.md" target="_blank">Installing Django Locally</a>

* <a href="../ngrok" target="_blank">Using ngrok to turn in your assignments</a>

