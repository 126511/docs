# Deploying a Django application on Heroku.

In this guide, I'll take you through the process of setting up a basic Django app on Heroku. For this tutorial, I assume you have
* a repository on GitHub with your Django App
* a free account on heroku.com (if you do not have one, go to [Heroku](https://www.heroku.com) and sign up)
* a virtual environment or at least you are able to use `pip` and `Python` in the commandline

I'm on a Windows machine, but the steps will be very similar on different platforms.

## Preparing your Django app

In order to support Heroku, we need to install a `PyPi` packages `django-heroku` and `gunicorn` with the command

```shell
pip install django-heroku
pip install gunicorn
```

Then in `settings.py` add this code to import the library and set it up.
```python
import django_heroku
django_heroku.settings(locals())
```

In order to recognize that this is a Django app we need to add a file `Procfile` (without extension) to the root of our repostiory.

1. Create a file named `Procfile` in the root of your repository.
2. In the the file, put this `web: gunicorn <application_name>.wsgi:application --log-file -` where `<application_name>` should be replaced by the name of your application. You can recognize it by the name of the folder that contains `wsgi.py`.

Then, we should add a runtime file that tells Heroku the Python version to use, in your command line execute
```shell
python --version
``` 

This tells you the version of Python you're running, for me its
```shell
Python 3.9.13
```

Add a file to the root of your repository called `runtime.txt` and put `python-3.9.13` in it, where you replace `3.9.13` with your version.

Lastly, we should tell Heroku what packages to use, in your command line in the root of your repository run 
```shell
pip freeze > requirements.txt
```

Commit this to GitHub and your Django-app is prepared!
