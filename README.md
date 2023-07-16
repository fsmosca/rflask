# Deploy reactpy app with flask backend to GCP.

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

This is only local with respect to the machine in GCP that we are using. This is different when we actually deploy our app.

```
python -m venv venv
```

### 7. Activate the venv

```
source venv/bin/activate
```

### 8. Install the modules in the requirements.txt

To test if the contents of our requirements.txt file is right.

```
pip install -r requirements.txt
```

### 9. Test it

We are not deploying for production yet. Just testing the virtual environment.

```
gunicorn main:app
```

You should see:

"Hello, world!"

Send control+c in the shell to exit.

### 10. Create app

Now let us create an app for production. This is the real deal that we are up to.

```
gcloud app create
```

### 11. Deploy the app

The app.yaml is using flexible environment, you can open the app.yaml file. Flexible uses a container. There are comments in app.yaml file. Read the items in the reference section too.

```
gcloud app deploy --appyaml=app.yaml
```

This is our `app.yaml`.

```python
runtime: python

# F1 = 2 workers (default), F2 = 4 workers
instance_class: F1

env: flex

# -w 2 sets gunicorn number of workers
# The number of workers you specify should match the instance class of your App Engine app:
entrypoint: gunicorn -b :$PORT -w 2 main:app

runtime_config:
    operating_system: "ubuntu22"
    runtime_version: "3.11"
```

## Note

* The `app.yaml` is using flexible environment. Attempts to use standard environment did not work so far.
* We use gunicorn in entry point at `app.yaml`, so we need gunicorn in `requirements.txt`

## Reference

* https://reactpy.dev/docs/guides/getting-started/running-reactpy.html#running-reactpy-in-production
* https://cloud.google.com/appengine/docs/flexible/python/runtime
* https://cloud.google.com/appengine/docs/standard/reference/app-yaml?tab=python
