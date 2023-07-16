# Deploy reactpy app with flask backend in GCP.

## Guide

Visit https://console.cloud.google.com/getting-started

### 1. Create project

Be sure to setup billing too.

### 2. Access Settings

```
Navigation Menu -> IAM & Admin -> Settings
```

### 3. Activate Cloud Shell

Press that button at top right.

### 4. Clone this repo

```
git clone https://github.com/fsmosca/rflask.git
```

### 5. Change directory to rflask

```
cd rflask
```

### 6. Create virtual environment.

```
python -m venv venv
```

### 7. Activate the venv

```
source venv/bin/activate
```

### 8. Install the modules in the requirements.txt

```
pip install -r requirements.txt
```

### 9. Test it

We are not deploying for production yet. Just testing the virtual environment we just created in GCP.

```
gunicorn main:app
```

You should see:

"Hello, world!"

Send control+c in shell to exit.

### 10. Create app

```
gcloud app create
```

### 11. Deploy the app

```
gcloud app deploy --appyaml=app.yaml
```

## Note

* The `app.yaml` is using flexible environment. Attempts to use standard environment did not work so far.
* We use gunicorn in entry point at `app.yaml`, so we need gunicorn in `requirements.txt`

## Reference

* https://reactpy.dev/docs/guides/getting-started/running-reactpy.html#running-reactpy-in-production
* https://cloud.google.com/appengine/docs/flexible/python/runtime
* https://cloud.google.com/appengine/docs/standard/reference/app-yaml?tab=python
