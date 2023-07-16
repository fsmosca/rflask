# Deploy reactpy app with flask backend in GCP.

Command to deploy.

```
gcloud app deploy app.yaml
```

## Note

The `app.yaml` is using flexible environment. Attempts to use standard environment did not work so far.

## Reference

* https://cloud.google.com/appengine/docs/flexible/python/runtime
* https://cloud.google.com/appengine/docs/standard/reference/app-yaml?tab=python
