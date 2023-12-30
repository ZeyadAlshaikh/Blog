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
(/DevServer.png)
## Step 5: Creating blog app
## Step 6: Some configuration steps
### Apply migrations:
### Create a Superuser to access admin page:
## Step 7: Designing the Database
## Step 8: Creating Views and Templates
### Creating view to serve your index page:
### Adding URL to serve the index
## Step 9: Testing

### Thank You!
