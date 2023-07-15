# rflask
Deploy reactpy app with flask backend in GCP.

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
```
