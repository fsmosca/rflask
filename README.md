# Deploy reactpy app with flask backend in GCP.

It does not work.

Issues:

reactpy/backend/flask.py

```
ModuleNotFoundError: No module named 'flask_cors'
ModuleNotFoundError: No module named 'flask_sock'
```

After installation of the two modules outside of reactpy by:

`pip install Flask-Cors`  
`pip install flask-sock`

GCP runs correctly with command from shell.

```
gunicorn -w 1 main:app
```

But if it is deployed with:

```
gcloud app deploy
```

It does not work.

Page message.

```
502 Bad Gateway
---------------
    nginx
```

Page console:

```
Failed to load resource: the server responded with a status of 502 ()
```
