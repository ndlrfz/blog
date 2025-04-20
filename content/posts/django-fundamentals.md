+++
date = '2025-04-15T11:11:12+07:00'
draft = false
title = 'Django Fundamentals'
+++

## Intro

* Django is a Python web framework for building web applications.
* MVT (Model, View, Template)

## Install Django

In this example, I will use `uv` (you should try `uv` / 100x faster than `pip`).

1. Setup project directory and virtual env.

   ```bash
   mkdir -p ~/project; cd ~/project
   uv init

   uv venv
   source .venv/bin/activate
   ```

2. Install Django

   ```bash
   uv add django
   django-admin --help
   ```

## Create Django Project

1. Add project.

   ```bash
   django-admin startproject main .
   ```

2. Check the project tree.

   ```bash
   tree

   .
   ├── movies
   │   ├── admin.py
   │   ├── apps.py
   │   ├── __init__.py
   │   ├── models.py
   │   ├── tests.py
   │   └── views.py
   ├── main
   │   ├── asgi.py
   │   ├── __init__.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── db.sqlite3
   ├── main.py
   ├── manage.py
   ├── pyproject.toml
   ├── README.md
   └── uv.lock
   ```

3. Run Django.

   ```bash
   py manage.py runserver
   ```

4. Visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

## Create Your First Application

1. Create app.

   ```bash
   py manage.py startapp movies
   ```

2. Edit file `main/settings.py`.

   ```python
   INSTALLED_APPS = [
      ...,
      'movies',
   ]
   ```

3. Edit `movies/views.py`.

   ```python
   from django.http import HttpResponse

   ...

   def index(request):
      return HttpResponse("Hello Django - movies app")
   ```

4. Create URL file `movies/urls.py`

   ```python
   from django.urls import include, path

   from . import views

   urlpatterns = [
      path('', views.index),
   ]
   ```

5. Edit main URL file `main/urls.py`.

   ```python
   from django.http import include, path

   ...

   urlpatterns = [
      ....,
      path('movies/', include('movies.urls')),
   ]
   ```

6. Rerun the django dev.

```bash
py manage.py runserver
```

7. Visit [http://127.0.0.1:8000/movies/](http://127.0.0.1:8000/movies/).
