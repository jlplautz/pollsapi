# pollsapi
Project based on book Building Apis with Django and Django Rest Framework

##2- Create virtual environment
   - pollsapi $ pipenv install django
   - pollsapi $ pipenv install djangorestframework
   - pollsapi $ pipenv shell
   - (pollsapi) pollsapi $ pipenv install flake8
   - (pollsapi) pollsapi $ pip freeze > requirements.txt
   ```
   (pollsapi) pollsapi $ tree
    .
    ├── LICENSE
    ├── Pipfile
    ├── Pipfile.lock
    ├── README.md
    └── requirements.txt
   ```
   - file .flake8
   ```
   [flake8]
   max-line-length = 120
   exclude = .venv
   ```
   - file .pyup.yml
   ```
   requirements:
      - Pipfile
      - Pipfile.lock
   ```   

##2.1- Create a project
   - (pollsapi) pollsapi $ django-admin startproject pollsapi

##2.2- Create setup
   - pollsapi/settings.py file would already have the correct settings
   - (pollsapi) pollsapi $ python manage.py migrate
   
##2.3- Create models
   - (pollsapi) pollsapi $ python manage.py startapp polls
   ```
   (pollsapi) pollsapi $ pwd
   /home/plautz/PycharmProjects/pollsapi/pollsapi
   (pollsapi) pollsapi $ tree
   .
   ├── db.sqlite3
   ├── manage.py
   ├── Pipfile
   ├── Pipfile.lock
   ├── polls
   │   ├── admin.py
   │   ├── apps.py
   │   ├── __init__.py
   │   ├── migrations
   │   │   └── __init__.py
   │   ├── models.py
   │   ├── tests.py
   │   └── views.py
   └── pollsapi
       ├── asgi.py
       ├── __init__.py
       ├── __pycache__
       │   ├── __init__.cpython-38.pyc
       │   ├── settings.cpython-38.pyc
       │   └── urls.cpython-38.pyc
       ├── settings.py
       ├── urls.py
       └── wsgi.py
   ```

##2.4- Active models
   - To create the database tables to our models,‘rest_framework’ and ‘polls’ app needs to be added 
     to the “INSTALLED_APPS” in the ‘django_pollsapi/settings’ file.
   ```
    INSTALLED_APPS = (
    ...
    'rest_framework',
    'polls',
    )
   ```
   - (pollsapi) pollsapi $ python manage.py makemigrations polls
   ```
   Migrations for 'polls':
     polls/migrations/0001_initial.py
       - Create model Poll
       - Create model Choice
       - Create model Vote
   ```
   - (pollsapi) pollsapi $ python manage.py migrate
   - created a file polls/urls.py 
   - include the polls urls pollsapi/urls.py
   ```
   from django.contrib import admin
   from django.urls import path, include
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', include('polls.urls'))
    ]
   ```
