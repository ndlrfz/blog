+++
date = '2025-04-15T11:11:12+07:00'
draft = false
tags = ["django", "python"]
showTags = true
title = 'Django Fundamentals'
toc = true
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

## Create Django project

1. Add project.

   ```bash
   django-admin startproject main .
   ```

2. Check the project tree.

   ```bash
   tree

   .
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

## Create your first application

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

## Rendering HTML template in Django

1. Edit the file `movies/views.py`.

   ```python
   from django.shortcuts import render

   def index(request):
      return render(request, 'index.html')
   ```

2. Create a new directory and file.

   ```bash
   mkdir -p movies/templates/movies/
   touch movies/templates/movies/index.html
   ```

3. Edit the `movies/templates/movies/index.html`.

   ```html
   <h1>Hello Django</h1>
   ```

4. Re-run the Django development server.

   ```bash
   py manage.py runserver
   ```

## Passing data to Django template

1. Edit the `movies/views.py`.

   ```python
   ...
   ...
   def index(request):
      # my test data
      context = {
         'name' : 'ndlrfz96',
         'address' : 'Magelang',
         'hobbies' : ['Reading', 'Watching Movies', 'Python', 'Linux']
      }

      return render(request, 'index.html', context)
   ```

2. Add to the `movies/templates/movies/index.html`.

   ```html
   <h1>Hello Django</h1>

   <p> My name is {{ name }} and I'm from {{ address }} </p>
   <br>
   <p> My hobbies is: </p>
   <ul>
      {% for hobby in hobbies %}
         <li>{{ hobby|title }}</li>
      {% endfor %}
   </ul>
   ```

3. Re-run the Django development server again.

## Serving static files in Django

1. Create a new directory within your root project directory `static/{css,js,img}`.

   ```bash
   cd ~/project/
   mkdir -p static/{css,js,img}
   ```

2. Edit `main/settings.py`.

   ```python
   import os
   ...
   ...
   # default static url => site.com/static/css/style.css
   STATIC_URL = 'static'

   # static root directory after collects
   STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

   # additional static directories in list, you can add multiple
   # for dev
   STATICFILES_DIRS = [os.path.joinc(BASE_DIR, 'static')]
   ```

3. Add the CSS file `static/css/style.css`.

   ```css
   body {
       background-color: lightblue;
       font-family: Inter;
   }
   ```

4. Add the JavaScript file `static/js/main.js`.

   ```javascript
   // refreshPage() to refresh current tab
   function refreshPage() {
     window.location.reload();
   }

   // openYoutube() in new tab
   function openYoutube() {
     window.open("https://www.youtube.com/watch?v=OJEqTnsLCEE", "_blank");
   }
   ```

5. Add your image to `static/img/cat.png`.

6. Edit the `movies/templates/movies/index.html`.

   ```html
   {% load static %}

   <!DOCTYPE html>
   <html lang="en">
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1">
           <title></title>
           <link href="{% static 'css/style.css' %}" rel="stylesheet">
       </head>
       <body>
       <h1>Hello Django</h1>
       <p>My name is {{ name }}, and I'm from {{ address }}</p>
       <p>My hobbies is:</p>
           <ul>
               {% for hobby in hobbies %}
               <li>{{ hobby|title }}</li>
               {% endfor %}
           </ul>

       <button type="submit" onClick="refreshPage()">Refresh this page</button>
       <button type="submit" onClick="openYoutube()">Open Ant</button>
       <br>
       <br>
       <img src="{% static 'img/cat.png' %}" alt="Cat profile">
       <script src="{% static 'js/main.js' %}"></script>
       </body>
   </html>
   ```

   From the above template:

   * Load static via `{% load static %}`.
   * Add CSS, JS, and image file with the format `{% static 'css/style.css' %}`.
   * Created two submit button with the JavaScript function `refreshPage()` and `openYoutube()`.

7. Re-run the Django development server.
