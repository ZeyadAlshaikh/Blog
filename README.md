![Banner](https://github.com/ZeyadAlshaikh/Blog/assets/15981299/6980a4c9-ef6f-4c44-8b43-9b9faf359c56)

# Django Blog website Guide
Building a blog website using Django can be a rewarding experience. Django is a powerful web framework that allows developers to create dynamic and feature-rich websites. In this guide, we will walk you through the process of building your own Django blog website.

## Step 1: Install python on your machine
Make sure that you have installed python correctly on your machine. You can test it by running the following command.
```
$ python -V
# you should see somthing like this
$ Python 3.8.10
```

## Step 2: Create virtual environment ( best practice )
```
$ python -m venv venv
```
You might need to active your environment if not activated automatically by typing the following command.

For mac and linux users
```
$ source venv/bin/activate
```

For windows users
```
#for command prompt
$ .\venv\Scripts\activate
# for powershell
$ .\venv\Scripts\Activate.ps1
```

## Step 3: Installing Django
Before getting started, make sure you have installed Django on your virtual environment. You can install Django using pip, the Python package manager. 
```
$ pip install django
```


## Step 4: Creating your project
Once Django is installed, create a new Django project and test it.
```
$ django-admin startproject blog_project
$ cd blog_project
$ python mange.py runserver
```
Click on the link (http://127.0.0.1:8000/) to open your project. if you see the image below, then congratulation, you have a running website. 
![Screenshot of development server](/DevServer.png)

## Step 5: Creating blog app
Now, you can stop the server by (press Ctrl+C in the terminal) . Run the following command to create the blog app.
```
$ python manage.py startapp blog
```
## Step 6: Some configuration steps
### Add the App to Your Project:
Open the settings.py file located in your project directory (blog_project/settings.py). Locate the INSTALLED_APPS section and add the name of your new app to the list.
```python
INSTALLED_APPS = [
# ...
'blog',
]
```
### Apply migrations:
```
$ python manage.py migrate
```

### Create a Superuser to access admin page:
To create a superuser for the admin interface run the following command and follow the prompts.
```
$ python manage.py createsuperuser
```
## Step 7: Designing the Database
Next, design the database schema for your blog website. Think about the models you'll need, such as a model for blog posts, categories, and user comments. Use Django's ORM (Object-Relational Mapping) to define your models and their relationships.

Open the **`models.py`** file located in your project directory (**`blog_project/blog/models.py`**).

```python
class Post(models.Model):

    title = models.CharField(verbose_name="title", max_length=50)
    body = models.TextField(verbose_name="body", max_length=500)
		
		def __str__(self):
        return self.title
```
Apply your changes to the database by running the following commands:
```
$ python manage.py makemigrations
$ python manage.py migrate
```

## Step 8: Creating Views and Templates
In this step, you'll create views and templates for your blog website. Views handle the logic behind each page, and templates define how the pages should be rendered. Use Django's built-in template language to create dynamic and interactive web pages.
Create folder templates in your app directory (blog_project/blog/tempaltes/) to add all .HTML pages. 

Open the settings.py file located in your project directory (blog_project/settings.py). Locate the TEMPLATES section and add  import os before it. Then change the following:

```python
'DIRS': [os.path.join(BASE_DIR, 'templates')],
```
Now, all .HTML files will be served from this folder. 

Create index.html page to be the landing page for your website. Add the following code.

We will use bootstrap template to save us time. You can download the template from: (https://getbootstrap.com/docs/5.0/examples/album/) with some modifications

### ndex.html
```HTML
<!doctype html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.4.1/dist/css/bootstrap.min.css"
        integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Django Blog</title>
</head>

<body>

    <header>

        <div class="navbar navbar-dark bg-dark shadow-sm">
            <div class="container">
                <a href="#" class="navbar-brand d-flex align-items-center">
                    <strong>Django Blog</strong>
                </a>
            </div>
        </div>
    </header>

    <main>

        <section class="py-5 text-center container">
            <div class="row py-lg-5">
                <div class="col-lg-6 col-md-8 mx-auto">
                    <h1 class="fw-light">Elevating Web Development: A Journey Through Django's Framework Wonders </h1>

                </div>
            </div>
        </section>

        <div class="album py-5 bg-light">
            <div class="container">
                <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
                    {% for post in posts %}


                    <div class="col">
                        <div class="card shadow-sm">
                            <div class="card-header">
                                <h4>{{post.title}}</h4>
                            </div>

                            <div class="card-body">
                                <p class="card-text">{{post.body}}</p>
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="btn-group">
                                        <button type="button" class="btn btn-sm btn-outline-secondary">View</button>

                                    </div>
                                    <small class="text-muted">9 mins</small>
                                </div>
                            </div>
                        </div>
                    </div>



                    {% endfor %}
                </div>
            </div>
        </div>


    </main>

    <footer class="text-muted py-5">
        <div class="container">
            <div class="text-center">
                <p class="mb-1">This project to demonstrate how to use Django</p>

            </div>


        </div>
    </footer>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
        integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
        integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.4.1/dist/js/bootstrap.min.js"
        integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6"
        crossorigin="anonymous"></script>
</body>

</html>
```


### Creating view to serve your index page
Open the views.py file located in your project directory (blog_project/blog/views.py).  and add the following.

```python
from django.shortcuts import render
from .models import Post
# Create your views here.
def index(request):
    posts = Post.objects.all()

    return render(request,'index.html',context={'posts':posts})
```

### Adding URL to serve the index
Open the urls.py file located in your project directory (blog_project/).  and add the following.
```python
from django.contrib import admin
from django.urls import path
from blog import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.index),
]
```
## Step 9: Testing
Now we need to add posts and see how our website looks like. 
Access the admin page from this URL: (http://localhost:8000/admin/) and login with the created superuser credentials.  You will not see the post table because we did not add it to the admin. Thus, we will add it now. 

Open the admin.py file located in your project directory (blog_project/blog) and add the following.
```python
from django.contrib import admin
from .models import Post
# Register your models here.

admin.site.register(Post)
```
Now, refresh your page and add new posts and check the index page. You should see the result of newly added posts.
### Thank You!
