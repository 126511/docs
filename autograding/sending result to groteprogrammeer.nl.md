# Sending the result of a check to groteprogrammeer.nl
Now that the user has created, via a `.sh`-file the result in `json` form. We need to send that data to groteprogrammeer.nl, so it can be processed into their final scores and can be stored there.

## `send.py`

```python 
import requests, json

def send(file):
""" Send a file (argument) to groteprogrammeer.nl """

	# Open file
	f = open(file)
	result = str(f.read())

	# Establish key
	key = "j3JK_SF#IN3fw"

	# Get username
	username = input("Enter your username on groteprogrammeer.nl: ")

	# Format data
	data = {'key':key, 'username':username, 'result':result}

	# Post request to website
	r = requests.post("http://127.0.0.1:8000/input/", data=data)

	# Close file
	f.close()
```
`send.py` declares a function `send` that takes the name of the `JSON`file with the result as input (e.g. `result.json`). This function needs to be run in the same folder as `result.json`, so that the function has access to the contents of that file. Then, it asks the user for their username on groteprogrammeer.nl, so the result can be linked to their account on the site. Then, it POSTs that data to the website which receives it in the input-app.

## Receiving the POST request with Django
```python
@csrf_exempt
def input(request):
	result = request.POST['result']
	
	import  json
	data = json.loads(result)
``` 
This is a view in the file `views.py`. It needs an url declaration in urls,py like this: `path("input/", views.input, name="input")`. It finds the result in the request.POST dictionary, and then loads that string into JSON form so that it can be pushed onto the database. The decorator `@csrf_exempt` makes sure that even the `send` function can access this view. Do not add this to others views without knowing exactly what it does, as it can create considerable security breaches.

## Saving data in the database
Now that all the JSON has been received at the back of the website, we need to process the data, that happens in three steps

### Storing the result in general
We keep all the results students submit, so they can later look at the submission they've done. To do so, all we do is add the JSON to a model, called something like `Input`.
```python
class Input(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    result = models.JSONField()

    from datetime import datetime
    datetime = models.DateTimeField(default=datetime.now())
```
This model has three fields, `user`, which is a ForeignKey to the user's field in the User table; `result`, which is the JSON `send` has sent to the website and `datetime`, which is a combination of the date and time the result was uploaded (so we can track the latest submission).
```python
    u = User.objects.get(username=request.POST['username'])
    i = Input(user=u, result=data)
	i.save()
```
This is the code that creates a new field for the model described above. `u` is a variable that holds the `User` instance (belong to the username that the user has provided to `send`). Then `i` is the new instance of `Input` (notice that the datetime field is autmatically populated, as specified in `models.py`).
### Updating the user's score
Aside from storing the result in its entirety, we also want to store how each user is doing for each `slug`, which is the unique GitHub url that identifies where the problems checks are stored.
```python
class Score(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    slug = models.CharField(max_length=256)

    total_tests = models.IntegerField()
    passed_tests = models.IntegerField()
```
The `Score` model stores to which `user` the score belongs, to what `slug` (i.e. exercise / assignment) and how many tests there are in total (`total_tests`) and how many of those the user has passed (`passed_tests`). 

