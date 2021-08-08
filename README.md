Step by step guide to create a Django Project:

Create project directory.

// In Gitbash Terminal  //

Create virtual environment in that directory: $ python -m venv env_name

Turn on virtual environment: $ source env_name/Scripts/activate

Install Django in virtual environment: $ pip install django

Start Project: $ django-admin.exe startproject project_core .

Migrate databases: $ python manage.py migrate

Create App: $ python manage.py startapp app_name

Add the newly created app to settings.py under "Installed Apps" : Installed Apps = [,'app_name',]

Add include after the path in core urls.py: from django.urls import path, include

Add new path in urlpatterns: urlpatterns = [,path('',include('app_name.urls')),]

Create a new urls.py in app_name then add each web pages in the app: 

// Code //

from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name="index"),
]

// End Of Code //

Add views in views.py: 

// Code //

def index(request):
    return render(request, 'index.html', {})

// End Of Code //

Create a templates folder inside app_name

Create index.html which will become the home page of your website

Create a static directory inside app_name

In settings.py under {{ STATIC_URL = '/static/' }}, add this code:

// Code //

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]

// End Of Code //

Note: If there is no /* import os */ in settings.py add it at the top of the code : import os
