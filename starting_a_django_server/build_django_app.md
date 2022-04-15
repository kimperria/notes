## Build a django app in your project
Django allows us to build projects with multiple apps/modules.

Run:
```bash
(virtual) python manage.py startapp <name_of_your_app>
```
This command will build a folder with your application name on the root project directory.

App folder should contain atleast these modules: admin, models, init, views etc...(python files)
## Test App (users)
To get us started I will create a users application. It will help us learn on how to create models, i.e user profile, user forms, how to handle user registration and authentication to our django project.

Run:
```bash
(virtual) python manage.py startapp users
```
This should create a new application on your root folder with the name users.

```
user logic:
    > user templates
    > user models
    > user forms
```

### Register new app to a django project
Application registration is done on the django project.
Navigate to the project folder, open settings.py file and register the application name under INSTALLED_APPS list.

Custom list should look like:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
There are two ways to registering a django app.
On the list, create a new string with the app name as its value. i.e
```
    ### some already existing apps above
    'users',
```
or
```
    ### some already existing apps above
    'users.apps.UsersConfig',
```

Remember to put in the comma at the end as installed app django variable is a list.

#### Add Bootstrap
[Bootstrap](https://django-bootstrap-v4.readthedocs.io/en/latest/) helps us improve our web user interface, quick design and customize responsive mobile-first websites.

Run:
```bash
    pip install django-bootstrap4
```

I will use [django-bootstrap4](https://pypi.org/project/django-bootstrap4/) for this project.

##### How to register bootstrap / other pips in django

Just like applications, pips and other additional requirements in django are registered in a similar manner by addding the pip inside the installed application list.

```
    ### some already existing apps above
    'bootstrap4',
```

### Register application url
URL dubbed (urlpatterns django variable) is a list that provide all the possible webpage navigation. 

Register your new application url as seen in the example below:

django-project directory/urls.py
```
from django.contrib import admin
from django.urls import path, include
from users import views as user_views


urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('neighbours.urls')),

    #users application
    path('register/', user_views.register, name='register'),
]

```
N/B: Django enables us to create application views. Two function that I am familiar with are the [class-based](https://docs.djangoproject.com/en/4.0/topics/class-based-views/intro/) and [function-based](https://docs.djangoproject.com/en/4.0/topics/http/views/) views.  

I will use a simple function based view to create the fist tempalate
### Create User registration form
Django helps us with most user logic on the background. A new user is required to sign up and my this django has a special module to help with that. UserCreationForm

Navigate to our users application to create a view function that renders new user registration form.

users/views.py
```
from django.shortcuts import render
from django.contrib.auth.forms import UserCreationForm

def register(request):
    '''
    New user registration
    '''
    form = UserCreationForm()
    return render(request, 'users/register.html', {"form":form})
```

### Create the first template
We will render the form instance on a html template. Located in templates/users/register.html

Create templates directory inside the users application.
Run: 
```bash
   $ mkdir templates
   $ cd templates/
   $ mkdir users
   $ touch register.html
```

The above commands should create two directories; templates and users and one register html file.

Create a simple html that will display our form instance example:

users/templates/users/register.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <div class='user-registration-form'>
        <form action='' method='POST'>
            {% csrf_token %}
            <fieldset class='form-group'>
                <legend class='border-bottom'>Register Here</legend>
                    {{ form }}
                <div class='form-group>
                    <button class='btn'>Sign Up</button>
                </div>
            </fieldset>
        </form>
        <div class='border-top>
            <small class="text-muted">
                Already have an account? <a href="#" class="ml-2">Login</a>
            </small>
    </div>
</body>
```
###### Conclusion
That's it! Your first template is set for display.
Run:
```bash
    python manage.py runserver

    output:
        Watching for file changes with StatReloader
        Performing system checks...

        System check identified no issues (0 silenced).

        You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
        Run 'python manage.py migrate' to apply them.
        April 15, 2022 - 10:38:12
        Django version 4.0.3, using settings 'neighbourhood.settings'
        Starting development server at http://127.0.0.1:8000/
        Quit the server with CONTROL-C.
```
###### local host development server
click on the subsequest link provided on your terminal. For this example, my developments server runs on: http://127.0.0.1:8000/ 

###### or

On your browser url section type in http://localhost:8000/ for django applications.

Naviate to the user registration section using the path below;
http://127.0.0.1:8000/register/ or http://localhost:8000/register/
